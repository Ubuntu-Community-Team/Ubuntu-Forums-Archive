---
title: "How to change a program window's starting location"
date: 2011-06-21
forum: General Help
---

### Post by TerribleLIar on 2011-06-21
Hello. I'm using Ubuntu 11.04 Unity and I have a strange problem. I have a certain program (Transmission) I have set to begin on startup. It works fine and everything, but its starting location is very inconvenient. It begins in the top left corner, not maximized, and the menu bar for it is underneath the Ubuntu bar at the top. It's also so far left that the Unity bar is hidden. The only way to move the program is to hold alt + mouse click because the top bar is so well hidden. If that explanation isn't clear enough, I can include a picture if required.

So the only thing I really want to is to move it a bit so the window is closer to the middle every time the computer starts up so it's easier to move (I like it in workspace 2, but not sure how to do that. devilsPie seemed to mess things up and still didn't work for me). I've tried some various things like moving it then logging off and on, but nothing has moved it... except when I tried out Xubuntu on the same partition with Ubuntu. All it did was move it into an even worse position... So any help on something that seems like it would be so simple would be great.

---

### Post by TerribleLIar on 2011-06-22
Bump.

---

### Post by Mark Phelps on 2011-06-22
What you want can only be done if the program allows it.

There are typically three variants:
1) Program window always opens on the top-left
2) Program remembers the last window size and location -- and reopens with the same the next time
3) Program provides option(s) for setting window opening location in terms of desktop geometry.

2) Is the most common.

3) Usually is provided through the use of a "geometry+/-X+/-Y" parameter where you specific the number of pixels down and to the right of the top-left corner of the desktop.

If 2) isn't working and there is no 3), then you're stuck.

---

### Post by TerribleLIar on 2011-06-22
Hmm. Transmission seems to be special. It does remember the location like variant 2 if you start the program normally, but if you start it under startup applications, it begins in the strange location. What is it about running it from the startup locatons that makes it forget its last location? Would there be any way around it while still having it run at startup?

---

