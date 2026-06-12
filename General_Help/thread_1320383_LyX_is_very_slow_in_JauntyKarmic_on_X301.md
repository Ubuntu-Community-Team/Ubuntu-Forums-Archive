---
title: "LyX is very slow in Jaunty/Karmic on X301"
date: 2009-11-09
forum: General Help
---

### Post by Rendsvig on 2009-11-09
Hi!

I have a ThinkPad X301, and I was running Jaunty, but had problems with LyX 1.6.2 being very slow when it came to scrolling, typing, deleting and especially working in formulas.

I found the following post, and tried changing my hardware acceleraion to XAA, but that didn't help: [https://bugs.launchpad.net/ubuntu/+s...yx/+bug/353449]("https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/353449").

Then I followed the advice in the bottom and tried upgrading to QT4.5.1. as explained here: [http://www.mail-archive.com/lyx-user.../msg74482.html]("http://www.mail-archive.com/lyx-users@lists.lyx.org/msg74482.html")

As I'm very new at the Ubuntu business, I just said Yes, basicly, all the way trough, and now I'm running Karmic with LyX 1.6.4... So, I'm not quite sure what I did.

My problem is that it didn't work. Xorg still uses between 50 and 80 percent CPU when scrolling, and it's still very slow to work in...

I run Win7 on the side, just to note, and here LyX runs very fast and smooth, and it is like that I hope I can get it to run in Ubuntu.

Any suggestions?

---

### Post by alnixx on 2009-11-09
I have the same problem. I am running karmic. even mouse pointer is slow on Lyx. I noticed that the CPU usage does not change and is pretty low. 
I am also new to Ubuntu and I like to know how kind people are here :)

---

### Post by baytuni on 2009-11-16
Rendsvig, I have the exact same problem. For large tables and many figures lyx uses 90% cpu. You've an intel graphics card, right? If you have Jaunty, you can install xorg 2.7 driver for intel and set the accelmethod to EXA. It was working for me for that configuration. As long as I upgraded to Karmic and use xorg 2.9 it came back again. The worst thing is you cannot use EXA in xorg 2.9.

---

### Post by Rendsvig on 2009-11-17
**Øv!**, as I would say in Danish, that's not very good news. Well, it partly is, because this means that there is a solution, its just really a shame that it would require me to *down*grade.

Thank you, baytuni, but I guess I'll leave this one open as it's still unsolved for Karmic.

---

### Post by baytuni on 2009-11-21
Rendsvig, add following lines into /etc/X11/xorg.conf "device section" . it helped me a bit.
```
Section "Device"
               
        Option "FramebufferCompression" "false"
       
        
EndSection
```

If you don't have a xorg.conf file search for "xorg.conf karmic" there is a method to create that file.

---

