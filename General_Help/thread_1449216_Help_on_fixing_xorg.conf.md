---
title: "Help on fixing xorg.conf"
date: 2010-04-07
forum: General Help
---

### Post by SidZ on 2010-04-07
Hello, I am having trouble with Ubuntu, after it boots, the screen is black, and pretty much has no graphics. The last thing I did was edit the xorg.conf file, and after reading up on this problem, I saw that it is indeed my xorg.conf file that is broken. 

Right now, I am on the Live CD, and I have been reading up on how to fix it, and have found that the fix is either to repair it via Recovery Mode, or to make a backup of the xorg.conf file on the ubuntu that is on my hard drive, then copy the one from the Live CD to it... However, I neither know how to back the file up, nor do I know how to copy the one from the Live CD to the Hard drive file system. I also have tried the Recovery Console, but it never repaired the broken xorg.conf file. Now, I have read as much as I could find on the matter, and I have attempted to do the fixes, so I would not be asking if it was otherwise. One of the main obstacles in my way was finding the xorg.conf file on my Live CD to copy, as it was absent from the X11 folder into which it should be found. I also tried: "locate xorg.conf" in the terminal, and to no avail, other then it pointing me to a xorg.conf.5.gz file in /media/share/man/man5...

So my question relies on the obvious: How do I fix my xorg.conf file? 

Any help would be appreciated. I am fairly new to Ubuntu, but have used the terminal a bit, still don't understand a lot of things. Also, I am using 9.10 Karmic with Gnome if that helps.

Thanks.

---

### Post by SidZ on 2010-04-07
Not trying to bump, but I just figured something out indirectly. I used: gksudo gedit /etc/X11/xorg.conf then save as "xorg.conf" to make a new one on the Live CD. Problem is, does this make it equal to the file I need, and I still need to know how to copy it from the Live CD to the HD File system. 

Thanks.

---

### Post by SidZ on 2010-04-07
Hello all, well I figured it out myself. After MUCH searching, I finally found a command thing called "nano" which allowed me to open it straight from the Hard Drive Filesystem, and configure on the spot, however, I did need to go into Recovery Mode and run it, then delete my invalid entries there, then save it, and reboot, now I'm all good. 

To be clearer on how I did it, I will type it step by step:

1. Reboot computer

2. Wait until it starts booting(Around the time you see "GRUB loading" in the upper left hand of the screen), a little bit before it does that sometimes, and hit the "esc" key. You may have to try this a few times if you weren't quick enough.

3. Then you should see a menu, and the second option should be "Start in recovery mode". Select that.

4. Wait until it loads up, you should see another menu on a blue screen now, and the last option on mine was something like "Boot shell prompt" which allows root access. This is the terminal you want to be in, and at the bottom of the screen should be a line area where you can input your code.

5. Input "nano /etc/X11/xorg.conf" and hit enter. This will take you to nano with the relevant file open. The commands to use nano are a little tricky, but this is all you need to know: ctrl + O will save the file, but ask you first the name you want to name it. I named one the same as it was, and then one extra for backup called xorg.conf.bak. Just hit enter when you're done naming it, and tada! Done. Or at least in my case. Now Reboot back to yoru Hard drive and have fun!

Thanks anyway guys!

---

### Post by 3rdalbum on 2010-04-07
If I'd seen this thread earlier I would have just suggested removing the xorg.conf file. X can come up without an xorg.conf. If you still needed one, you can tell X to create one based on what it detects.

---

### Post by SidZ on 2010-04-08
Indeed, but the problem was that I couldn't get permission to do anything with the xorg.conf file on the HDD in the first place. That is why I had to go into recovery mode to get into a root terminal to do this. Now, I am quite the newbie when it comes Ubuntu still, but was their another way to gain permission to do that?

---

### Post by wojox on 2010-04-08
Just move it:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

---

