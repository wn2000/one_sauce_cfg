The numbers in the `.rmp` files denote indices in [this list](https://github.com/libretro/RetroArch/blob/f89738e9a01326031faab4a062c7c73255149599/configuration.c#L5497-L5500):

```
      "b",      // 0
      "y",      // 1
      "select", // 2
      "start",  // 3
      "up",     // 4
      "down",   // 5
      "left",   // 6
      "right",  // 7
      "a",      // 8
      "x",      // 9
      "l",      // 10
      "r",      // 11
      "l2",     // 12
      "r2",     // 13
      "l3",     // 14
      "r3",     // 15
      "l_x+",   // 16
      "l_x-",   // 17
      "l_y+",   // 18
      "l_y-",   // 19
      "r_x+",   // 20
      "r_x-",   // 21
      "r_y+",   // 22
      "r_y-"    // 23
```

For example, the line
```
input_player1_btn_x = "10"
```
means "when retropad button X is pressed, send the 10th item in the list, or button L instead."

So what does "button L" do? That depends on the libretro core used.

For MAME2003-plus, when using its "Classic" controller type, it can be seen [here](https://github.com/libretro/mame2003-plus-libretro/blob/07485ae940e8ad5c5435b43a96d9e580910d4794/src/mame2003/mame2003.c#L982-L993) that the buttons are ordered as
```
B, A, Y, X, L, R, L2, R2, L3, R3.
```
So "button L" corresponds to "Button 5". In Street Fighters, this would be "Medium Kick".

Therefore, when using MAME2003-plus with its "Classic" controller type, the line
```
input_player1_btn_x = "10"
```
maps "RetroPad X" to "Button 5" or "Medium Kick" in Street Fighter.

