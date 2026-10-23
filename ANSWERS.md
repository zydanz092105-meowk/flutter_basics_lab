https://github.com/zydanz092105-meowk/flutter_basics_lab.git

1. What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each
from this lab.
StatelessWidget vs. StatefulWidget: A StatelessWidget never changes after it is drawn, whereas a StatefulWidget can update dynamically while the app is running. In this lab, ProfileCard (Activity 1) is a StatelessWidget, and WaterTrackerPage (Activity 2) is a StatefulWidget.

2. Why is a StatefulWidget written as two classes? What does each class do?
Two Classes for StatefulWidget: The first class (extending StatefulWidget) has no build() method and is only responsible for calling createState() to instantiate the State object. The second class (extending State<T>) holds the mutable data and contains the build() method to continuously redraw the screen using that current data.

3. In Activity 2, what happened when you changed _glasses outside setState()? Why?
Changing _glasses outside setState(): The internal variable increments, but the screen does not update to show the new number. Wrapping the change inside setState() is required because it signals Flutter that the data has changed and explicitly tells it to redraw the screen.

4. Looking at the Debug Console in Activity 2, when is build() called?
When build() is called in Activity 2: It is called when the app initially loads, and again every time the data is modified inside a setState() block such as tapping the add or remove buttons.
Here is the 3 builds from the terminal: build() called: 2 glasses
build() called: 3 glasses
build() called: 2 glasses

5. Explain the main axis and the cross axis of a Row and of a Column.
Row and Column Axes: For a Column, the main axis runs vertically (top to bottom), and the cross axis runs horizontally. For a Row, the main axis runs horizontally (left to right), and the cross axis runs vertically.

6. In Activity 3, what happened when you removed Expanded from a StatBox? What does Expanded do?
Expanded in Activity 3: Removing Expanded causes the StatBox to shrink to only fit its internal text instead of sharing the row's width equally, and it can cause an overflow error (yellow and black stripes) if the content exceeds the screen width. Expanded forces a child widget to take an equal share of the leftover available space.

7. Why do we use GridView.builder for the menu instead of a Column with many children?
GridView.builder vs Column: GridView.builder is highly efficient because it only builds the rows and items that are currently visible on the screen, which keeps the app fast even if the menu has 1,000 items.

8. How do Stack and Positioned create the Best seller badge in Activity 4?
Stack and Positioned for Badges: A Stack is used to place widgets directly on top of each other in layers. Inside the stack, the Positioned widget is used to pin the "Best seller" badge specifically to the top-left corner (top: 8, left: 8) of the card.

9. What is the difference between customizing with ThemeData and with a style on one widget? Give
one example of each from Activity 5.
ThemeData vs Widget Style: ThemeData is configured once inside MaterialApp and forces every widget in the app to follow its rules. A local style is passed to a single widget and changes only that specific instance. In Activity 5, ThemeData is used globally to enforce centered AppBar titles and pill-shaped ElevatedButtons, while a local style override is used explicitly on the "My skills" text widget to make it headlineSmall.

10. When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the
change reach MaterialApp?
Dark Mode State Management: The state variable (_isDark) is held in the top-level parent widget, ThemeDemoApp. The switch passes the change up via a callback (onDarkChanged), which triggers setState() in the parent; this rebuilds the widget tree and passes the new value down to MaterialApp's themeMode property.

