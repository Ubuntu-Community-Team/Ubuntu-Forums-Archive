---
title: "I'm not quite sure the exact problem.. Window's are messed up?"
date: 2010-02-02
forum: General Help
---

### Post by Lunami on 2010-02-02
Alright, I just booted up, after making a flash USB for a test (didn't work) so I booted as normally into Ubuntu 9.10 (not dual boot). When I get back on, there's this... I don't know how to explain it. If someone can think of a better way to explain this, I'll change the title to be a bit more helpful, and easier to search for those who have a similar problem.

I can't browse through windows (such as with Alt + Tab, or even just clicking on another window), nothing comes to the front, and stays as is. I've not touched my graphics / display settings, so the only thing I can think of, is when I was going through the boot-up applications, but I doubt I disabled anything that would have been graphics and GUI based, or the compizconfig-settings-manager disrupted something. I've ye to test anything, it's rather early.

Any suggestions, need me to do something, just ask away, I really am quite baffled with this. A screenshot should be provided below, and note the only way I got that bar at the top of my firefox is from hitting F11 I believe it was. I'm hoping this can be fixed, without having to reinstall ubuntu to the drive.

Thanks in advance.

---

### Post by 3rdalbum on 2010-02-02
There's no window manager running. If you've done something really bad in compizconfig-settings-manager, it can cause Compiz to crash out and not replace itself with the default Metacity.

Find a way to run this command (might require some lateral thinking):

```
metacity --replace
```

Or turn off Visual Effects and it will go back to Metacity.

Reverse your changes in compizconfig-settings manager and then you can run:

```
compiz --replace
```

---

### Post by coldraven on 2010-02-02
Tip! Press Fn+PrintScreen to get an image of the whole desktop or Alt+Fn+Printscreen for just the active window. (It works on laptops anyway)
I'm sorry I cannot help you in any other way. Good luck!

---

### Post by Lunami on 2010-02-02
Well, even attempting to perform the metacity --replace takes a while, and usually ends up becoming unresponsive. For the time being, I reinstalled CCSM, and simply ran the last code

compiz --replace

This seems to work, however, it stops the moment I boot back into the OS. Seems I've still much to learn about this, but hopefully, I'll have learned enough by time I re-install this, or simply upgrade to 10.4 when it's released.

Anywho, any tips on how to make this start this way? I'm thinking I should be able to just throw the command at start-up, or just placing a script on the desktop to run compiz --replace when I get the desktop booted to.

---

