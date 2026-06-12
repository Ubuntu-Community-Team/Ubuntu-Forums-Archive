---
title: "Wireless drivers not showing up in installed version, only in &quot;live&quot;"
date: 2010-03-22
forum: General Help
---

### Post by chris_b_shanks on 2010-03-22
Hi; sorry I think I incorrectly posted this in "Absolute Beginners" so I'm reposting it here:

I've got something that's really confusing me.  I'm a total noob, but I  read a fair bit about Ubuntu before I overwrote my windows.  To make  sure it worked, I used the Live run option, and it worked fine on my  system.  Everything worked, it notified me, however, to use the internet  I'd have to download proprietary drivers (Broadcom B43 wireless driver  and Broadcom STA wireless driver).  I did it and my internet started  working.  So everything was fine and I rebooted and actually installed  the OS.  Once installed, it would not get internet, nor prompt for  drivers being required.  So I checked my manual and tried to do it  manually: System / Administration / Hardware Drivers.  It searched, and  said there were no proprietary drivers.  I thought that this was weird,  so I rebooted my system "Live" again (even though it was already  installed): and the Drivers were there again!  They only show up in  live, I can't get internet in the installed version. What's going on?   How do I get these two drivers to show up on my actual installed copy,  not my lie copy?  Help would be greatly appreciated!

thanks for your time and consideration, chris

---

### Post by l.billon on 2010-03-22
Hi!
Regarding to the drivers you cited, i bet you are using a DELL Studio. Please do not forget your computer spec when asking for technical help.
Try Fn + F2 or whatever is your computer's wireless switch, as it may be the reason why you can't see any interface.

Restart your computer and type in a console
```
gksudo jockey-gtk
```
to see if the proprietary driver manager is detecting the driver.

---

### Post by pastalavista on 2010-03-22
On your installed system, go to System->Administration->Software Sources. Place the live CD in the drive and check the box in Software Sources to use the disk as a repository. Then run the Hardware Drivers tool again. Or you could connect to the internet via wired ethernet and download the drivers.

---

### Post by chris_b_shanks on 2010-03-22
Hells yeah!  Thanks so much!  Solved!

---

