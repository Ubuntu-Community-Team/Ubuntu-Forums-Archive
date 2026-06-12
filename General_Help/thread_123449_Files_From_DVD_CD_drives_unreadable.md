---
title: "Files From DVD CD drives unreadable"
date: 2006-01-30
forum: General Help
---

### Post by ockertom on 2006-01-30
Hi peeps me again :)

The problem I have is that I have 1 lg dvd ram recorder & 1 lg cd&dvd recorder problem is that I have a number of disks burnt with the dvd burner, mostly done in nero in windows, some in k3b, thing is the drives can read the header of whats on the disc but when I open the drive there is nothing there or folders with ?????? names. I could see files on one dvd out of the 10 I tried, they are working I know that. Now in windows I had to get the latest aspii? drivers for my drives is it the same for this os as well? If so where do I go to get em. Thanks In Advance :evil:

---

### Post by Aramil on 2006-01-30
That's because you have probably used different encoding in your file names when you burned them.I think you have to edit some lines in the /etc/fstab file.There you will find a line 

/media/cdrom0

On the 4th column it probably says 

user,noauto


Change it to

user,noauto,iocharset=utf8

Let me know if it worked!

---

### Post by ockertom on 2006-02-01
Lol now it wont even mount them :)

/dev/hdd        /media/cdrom0   udf, iso9660 user,noauto,iocharset=utf8    0       0
/dev/hdc        /media/cdrom1   udf, iso9660 user,noauto,iocharset=utf8     0       0

If I take away the udf iso9660 it doesnt do anything either sigh ah well thanks for the help mate :)

---

### Post by ockertom on 2006-02-01
No the command works but I still get invalid encoding shrug. Works in mandriva this is weird.

---

### Post by akiro.yamamoto on 2006-02-01
I had a similar experience. I used a trick to enable ejecting the drive with the eject button on the disk and suddenly could not read any disks.
When I reverted to the original set-up......all good. Tried it again and so far stiiiillllll good.
I don't know if that's the problem for you but you can keep it in mind.
;)

---

### Post by ockertom on 2006-02-03
Just for a heads up peeps, I did fix the problem, it seems if you instal that eject from button on cd dvd device from Automatix, it screws up the file system. 

Fix? lol for me was a reinstall, could read my discs :-?  I would say there would have been a easier way of fixing this, But im not experienced enough in nix, but Im learning quick.

Ah well live and learn. Still love this distro but as in life is all is a learning curve.

---

### Post by adam.jimenez on 2006-03-09
Had the same problem. I've got a fix for this that doesn't require a reinstall!

sudo gedit /etc/sysctl.conf

remove last line: dev.cdrom.lock=0

save and reboot.

---

### Post by djl on 2006-03-20
I did this fix, removed the line and saved, rebooted and nothing has changed - I checked the sysctl.config and the line is gone... is there a second file somewhere or has my machine decided to do what it likes...

---

