---
title: "Serial mouse will not work"
date: 2009-12-11
forum: General Help
---

### Post by Aralhach on 2009-12-11
My sister's abuse of this poor thing ruined the normal PS/2 mouse I was using.  This has forced me to pull out one of my old COM mouse.  However, I haven't been able to get Ubuntu to recognize it.  I went to the SerialMouseHowTo in the Community Documentation.  It said that the method below does not work since Ubuntu started using HAL (this was confirmed when I looked at the xorg.conf file, the entries were commented out and talked about HAL).  I added the line that it said to add, namely:
```
Option "AllowEmptyInput" "false"
```to the ServerLayout section as indicated.
When I reboot, the mouse still doesn't work and my keyboard goes bezerk (forcing me to exit with Ctrl-Alt-F1 and to replace the xorg.conf with xorg.conf~ to undo the changes).

Any help, to get this mouse working? It's still in excellent condition... :)
Thanks in advance for your help!!

---

### Post by derrick81787 on 2009-12-11
I'd also be interested in knowing the solution to this.  It seems like it should be something simple, but I don't know what.  I tried a while back, but then I found an old PS/2 mouse and just started using that before I ever got the serial mouse working.

---

### Post by joes7 on 2009-12-11
Check the Harware and Driver options.

---

### Post by Aralhach on 2009-12-11
I checked there... Hardware Drivers only has the video card drivers in it.... I don't know.

I changed the PS/2 mouse from another computer that uses Windows and gave it the COM mouse (it works fine)..... too bad.  I guess the fix is not in sight and probably no one will every make it since they are growing more and more uncommon and USB mice are becoming standard.

---

### Post by raygj on 2009-12-11
This works well
[http://ubuntuforums.org/showthread.php?t=1331499]("http://ubuntuforums.org/showthread.php?t=1331499")
<http://ubuntuforums.org/showthread.php?t=1331499>

---

