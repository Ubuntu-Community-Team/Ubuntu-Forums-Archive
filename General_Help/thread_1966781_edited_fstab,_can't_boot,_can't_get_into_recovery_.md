---
title: "edited fstab, can't boot, can't get into recovery mode"
date: 2012-04-27
forum: General Help
---

### Post by anotherlinuxnewbie on 2012-04-27
Using this [[COLOR="Red"]site[/COLOR]]("http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html") as a guide, I edited my fstab, rebooted, and now I can't boot into Ubuntu (server), and when I tried to go into recovery mode, it seems to work (lots of lines flash onto the screen), but then it goes black and my monitor goes into "no signal"/power save mode -- i.e., the box seems to stop communicating with the monitor.  I can't telnet into the machine (which is usually how I interact with it), but I can ping it.  So something's booting up, but I just don't know what, and I can't get to the fstab file to revert it back.

I'm thinking I'll have to use some kind of boot disk that'll let me edit the fstab file, but I don't know what or how.

Any suggestions would be appreciated.

---

### Post by oldfred on 2012-04-27
Did you run this command? which was in the last part of the instructions?
```

sudo mount -a
```

If that returned with no errors then your fstab is ok and it boot issue is related to something else.

Do you get a grub menu? Often black screen after starting to boot is a video driver issue or other boot parameter. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by anotherlinuxnewbie on 2012-04-27
For anybody interested, here's how I fixed it: [http://www.sysresccd.org/forums/viewtopic.php?f=4&t=4474&p=13105#p13105](http://www.sysresccd.org/forums/viewtopic.php?f=4&t=4474&p=13105#p13105)

---

