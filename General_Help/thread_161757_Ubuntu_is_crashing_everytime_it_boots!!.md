---
title: "Ubuntu is crashing everytime it boots!!"
date: 2006-04-17
forum: General Help
---

### Post by Mr Aragorn on 2006-04-17
Im a noob, I just installed ubuntu, but everytime I choose ubuntu it loads up but the screen is filled with colors, and thats it. What am I doing wrong?Someone please help me?

Here is a pic of what the screen shows when ubuntu boots up.

THanks

---

### Post by Qrk on 2006-04-17
Most problems of this nature are solved by reconfiguring xorg.

Do: 

<Ctrl><Alt><F1> or <Ctrl><Alt><Backspace> 
Login, then type this at the prompt
```
sudo dpkg-reconfigure xserver-xorg
```

You problem is probably with the second dialog screen, where the driver is displayed. Try switching the driver to "vesa" which seems to have the best universal hardware support. Once you've gone through the whole configuration, type this into the prompt:
```
startx
```

Edit: Once you have a graphical interface, read (in System->Help) on how to get a 3-d driver for your graphics card.

---

### Post by testube_babies on 2006-04-17
I have a similar problem.  Reconfiguring xorg didn't solve anything.  Take a look at [my thread]("http://www.ubuntuforums.org/showthread.php?t=161277").  In the end, once a solution is found, it will probably lead you down the right path.

---

