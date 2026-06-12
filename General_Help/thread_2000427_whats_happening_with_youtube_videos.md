---
title: "whats happening with youtube videos ???"
date: 2012-06-09
forum: General Help
---

### Post by rostom_zer on 2012-06-09
hello every one

could any one tells me what's the problem with youtube videos in my laptop ???

here is a screen sample (attachement)

you see the colors ????

what's the problem ???

---

### Post by Vaphell on 2012-06-09
latest flash + nvidia drivers + hardware acceleration enabled - don't expect it fixed ever, adobe has dumped linux standalone flash plugin entirely

disable hw accel or rollback to some earlier version of flash plugin

---

### Post by VE6EFR on 2012-06-09
It appears other people are having this problem as well:

[http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

---

### Post by rostom_zer on 2012-06-09
yesterday i was watching and all was fine with full hardware accel and latest nvidia driver (flash plugin i dont know which version )

but all was fine

!!!

---

### Post by philinux on 2012-06-09
> **rostom_zer said:**
> hello every one

could any one tells me what's the problem with youtube videos in my laptop ???

here is a screen sample (attachement)

you see the colors ????

what's the problem ???

[http://www.iheartubuntu.com/2012/05/blue-people-on-youtube-video-in-ubuntu.html](http://www.iheartubuntu.com/2012/05/blue-people-on-youtube-video-in-ubuntu.html)

---

### Post by Morbius1 on 2012-06-09
As a temporary fix you can right click the video > Settings > un-tick Enable Hardware Acceleration > reload the page.

For a permanent fix:
```
gksu gedit /etc/adobe/mms.cfg
```[COLOR=Blue]*It will either come up with that file or if it doesn’t exist it will create it.*[/COLOR]
Then add to the end of the file the following:
```
EnableLinuxHWVideoDecode=1
```Save the file, restart the browser and see if it goes away.

---

### Post by rostom_zer on 2012-06-09
Done...

problem fixed with flash-aid addon for firefox (google for it) then install adobe flash from it ( [COLOR=Lime]tools > flash-aid > quick mode > install stable flash[/COLOR] )

then it will reinstall adobe flash with the best settings.

thanX for helping

please ADMIN, change the title to SOLVED

---

