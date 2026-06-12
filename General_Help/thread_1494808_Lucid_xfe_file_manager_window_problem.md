---
title: "Lucid: xfe file manager window problem"
date: 2010-05-27
forum: General Help
---

### Post by Robbyx on 2010-05-27
When xfe opens the blue  strip at the top of the window with the window controls is hidden as if it is out of range of the top of the window. It  cannot be seen or easily accessed without moving the window. Are there any ubuntu changes  that I can make to  ensure that all of the window can be seen when a program's window opens?

---

### Post by Robbyx on 2010-05-27
Here is the correspondence I have had with one of the authors, setting out how to correct the window problem. In ubuntu the file xferc is at /home/<USER>/.config/xfe/xferc. I also notice that there is no xpos and ypos values but there is height and width. I set my height to 1000 and left the width at 1280.

Hi,

just close Xfe and edit your ~/.config/xfe/xferc file and change the
xpos and ypos values in the OPTIONS section to a value like 100 or so.
Also set the save_win_pos value of the SETTINGS section to 1.

Then restart Xfe and you should have your borders.

There is a bug with this behavior that I have fixed in the next
upcoming version, but I have to fix other bugs before releasing it.




> I have found the blue strip at the top of the window with the window
> controls. It seems that when xfe opens that  top strip is hidden out of
> the window range, so it cannot be seen or easily accessed without moving
> the window. Do you know what I can do to ensure that the top of the xfe
> window is always in view.

---

