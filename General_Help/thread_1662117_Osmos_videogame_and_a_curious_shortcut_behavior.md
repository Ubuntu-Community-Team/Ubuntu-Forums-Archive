---
title: "Osmos videogame and a curious shortcut behavior"
date: 2011-01-07
forum: General Help
---

### Post by MichaelPalin on 2011-01-07
This is more an inconvenience than a problem and I don't think I will find a solution, but I'm curious about why this can happen.

The thing is that I bought the Osmos game from the recent Humble Indie Bundle and I have placed the folder in /usr/games. I haven't installed it, the folder is executable as-is, but I have placed it in that address in order to be coherent with common game installations. I have created a shortcut of the executable file and placed it in the desktop. If the game is executed through the shortcut it looks like the first screenshot, if it is executed through the original executable it looks like the second one (it works correctly). It also works correctly if the shortcut is in the same folder as the executable. This happens both with the 32 and 64 bits executables.

Any idea why this can be?

I have a Radeon HD3870X2 and the open drivers in an Ubuntu 10.10 64 bits, if that is of any help.

As mentioned at the beginning, I'm not really looking for a solution, I'd be happy with an explanation of this phenomenon.

---

### Post by MaxIBoy on 2011-01-07
When you click "make link" in the file browser, you're creating a "symbolic link" instead of a shortcut. A symbolic link is like a whole new copy of the file, only it refers to the same data on the hard drive to save space. So imagine making a new copy of the executable, and putting it some random other place like your desktop. If you run it from there, it has no way of knowing where its data files are, and so it can't get at any of its textures. I guess Osmos displays white squares for missing textures, instead of just crashing.

What you actually want to make is a "launcher," which is much more similar to the Windows concept of a "shortcut." Here's a tutorial:
[http://www.yolinux.com/TUTORIALS/GNOME.html#LAUNCHER](http://www.yolinux.com/TUTORIALS/GNOME.html#LAUNCHER)

---

### Post by MichaelPalin on 2011-01-08
I have created a launcher, but, it also shows the white squares...

---

