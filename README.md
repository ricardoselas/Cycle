# Cycle
Cycle game

In this example, we're going to focus on the Cycle player's movement and creating the trails that are left behind as he moves across the screen. We could use line drawing functions for the trail behind the bike, or go for a system like Snake, where blocks are added to the trail as the player moves.

In this example, though, we're going to use a two-dimensional list as an array of screen positions. This means that wherever the player moves on the screen, we can set the position as visited or check if it has been visited before and if so, trigger an endgame event.

For the main draw() function, we first erase our background image, which is the hatched arena, then we iterate through our two-dimensional list of screen positions (each 10-pixel square) displaying a square wherever the Cycle has been. The Cycle is then drawn and we can add a score display.

The update() function contains code to move the Cycle and check for collisions. We use a list of directions in degrees to control the angle the player is pointing at and another list of x and y increments for each direction. With each update, we add x and y coordinates to the Cycle actor to move it in the direction it is pointing multiplied by our velocity variable.

We have an on_key_down() function defined to handle the Cycle actor changing direction with the arrow keys. We need to wait a bit before checking for collisions at the current position, as the Cycle won't have moved away by multiple updates, so each screen position in the matrix is actually a counter of how many updates it has been there.

We can then test to see if 15 updates have happened before testing the square for collisions, which gives our Cycle enough time to clear the area. If we detect a collision, we can start the endgame sequence.

We set the gamestatevariable to 1, which means that the update() function uses this variable as a counter to cycle through the animation frames for the Cycle burst. Once it reaches the end of the sequence, the game stops.

We have a keystroke defined (the SPACEbar) in the on_key_down() function to call our init() function, which will not only set variables when the game starts, but also return things to their initial state.

