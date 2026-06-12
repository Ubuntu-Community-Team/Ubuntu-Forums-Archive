---
title: "Save windows too big"
date: 2011-11-02
forum: General Help
---

### Post by mykrob on 2011-11-02
Difficult to explain this one, but regardless of the program I am using, if I need to save something, the dialog that pops up is too big with the save button being off screen. Screenshot is available here:

[http://img7.imagebanana.com/img/lxqqto2o/Workspace1_004.png](http://img7.imagebanana.com/img/lxqqto2o/Workspace1_004.png)

I have deleted the hidden session folder thinking maybe it was a corrupted saved session or something, but no luck. I am open to suggestions. This is on a cleanly installed 11.10 install. I don't have this problem on my laptop.

Help?

Thanks,
-myk

---

### Post by jonkiribati on 2011-11-02
you can use the Alt + mouse click to move a window  so just move it and resize it.

---

### Post by mykrob on 2011-11-02
I have been doing that. But I am looking for a way to reset the window size and save it. I have to move and resize every time at the moment.
Thanks,
-myk

---

### Post by mykrob on 2011-11-03
Surely I an not the only one with this problem...

---

### Post by haqking on 2011-11-03
just resize it.

The next time it should default to the last size you had ?

---

### Post by tractor on 2011-11-03
I've upgraded or done clean installs of Ubuntu 11.10 on about 10 systems so far. One system that was an upgrade from 11.04 is having this exact bug. It doesn't matter what application you are running, when you click on file then save as, the dialog window is too big for the display on the monitor, and the buttons are not visible. Resizing does not help. Once you have resized the window, the next time you do a file/save as, the window is again too big.

---

### Post by mykrob on 2011-11-03
Nobody seems to have a neal answer.
For testing, I created a new user account, and the issue is not present in the new account.
Apparently something let over in the user account is conflicting?

I just moved my files over to the new account and changed ownership of the files. I also made sure the new user had proper permissions, particularly adding the user to the sudo  group. Will test the new account for about a week, then delete the old account.

---

### Post by klaus_15 on 2011-11-20
I had the same issue until I removed some files from .config folder. I'm not completely sure removing which of them solved the problem.. I removed some compiz and nautilus config files. I think there was something named like "choosefile" or similar, but I don't remember now. 
Good luck!

---

### Post by metapaso on 2011-12-13
I have this same issue on a Lenovo X220i, also upgraded from 11.04.  Did you find a solution?  

I can resize the window, but it doesn't save the new dimensions.  Always the Save/Open/Cancel Buttons are off-screen.

---

### Post by tractor on 2011-12-13
On the machine which had the problem, I ended up doing a clean install. That solved the issue. The explanation about the configuration files makes sense.

---

### Post by Nais on 2011-12-31
I figured it was a old config file as well, seeing that very few had the prob.
narrowed it down to ```
~/.config/gtk-2.0/gtkfilechooser.ini
```

either delete it or change **GeometryWidth** and **GeometryHeight** to something sane.

---

### Post by talisman.26 on 2012-01-02
I'm having the same problem.  Some of the windows I cannot resize at all; I have the edge resizer, but it doesn't do anything.  I cannot find the .config folder either.  Lastly, how do I get into the root folder through Dolphin?

---

