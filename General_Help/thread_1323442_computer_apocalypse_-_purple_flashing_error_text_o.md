---
title: "computer apocalypse - purple flashing error text on startup"
date: 2009-11-11
forum: General Help
---

### Post by happyisland on 2009-11-11
I just tried to turn on my desktop PC (running 9.10, updated yesterday) and after the bios and grub screens the screen starts showing the following error message, scrolling down the screen:


[drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22


What in the heck is going on here? I tried googling but couldn't come up with any solutions. Pretty alarming stuff!


EDIT: I just found a bug report here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1825991.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1825991.html)   but I have no idea what it means. 

EDIT #2: This thread seems to deal with the issue, but I'm not technically adept enough to know what they're talking about: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421)

---

### Post by 824957q on 2009-11-11
ok basicly you have a install error either you tamperd with the compute while it was installing or there was an error with the internet connection.. try to reinstalll by disc that should work

---

### Post by happyisland on 2009-11-11
I think my first post was unclear. I upgraded to 9.10 the day it came out and it has been working flawlessly since. 

For no reason that I can tell (I haven't changed any settings or changed/installed anything big) today when I went to turn on the desktop it started acting VERY strangely, as described above.

---

### Post by xiella on 2009-11-12
I am also experiencing this error (although not purple flashing text, just normal white on black).  Installed Karmic (kubuntu) 9.10 fine, loaded fine every day for over a week, then just yesterday it displayed the "failed to restore crtc configuration" message.

If I press enter I am able to log in to a command line and access files that way.  I guess this means it failed to load the desktop but the actual OS is ok?

I found the following threads that might be helpful to you:
[http://ubuntuforums.org/showthread.php?t=1305010](http://ubuntuforums.org/showthread.php?t=1305010)
[http://www.uluga.ubuntuforums.org/showthread.php?t=1306935](http://www.uluga.ubuntuforums.org/showthread.php?t=1306935)

Also, the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421) has been updated.  They post a workaround to modify the boot options, however that doesn't work for me so I am still looking.

Update: As I was typing this my friend suggested I put "vga=792" in the boot options, which worked, amazingly!  I'm now back into KDE.  I have no idea what this parameter does, though, sorry.

Hope one of these solutions helps a bit?

---

### Post by happyisland on 2009-11-12
Hey xiella,

Thanks a lot for the thoughtful reply!

First, the purple color was a red herring, having to do with a simultaneous video cable problem. I fixed that, and then moved on to get the pc to boot into gnome by using the fix detailed on this thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421)

It's still unclear to me why it would suddenly stop working after working so well, but I'm just happy to have a functional computer again.

Thanks again for the help - it is much appreciated.

---

