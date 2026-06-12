---
title: "Computer won't boot."
date: 2011-02-02
forum: General Help
---

### Post by asdfasdf1122 on 2011-02-02
I loaned out my computer to a friend for a day and they returned it to, wherein it will no longer boot. They'd said that it had froze and they had simply turned it off via the power button and left it at that.  

Anyways when I boot fromm HDD I get the following:

```
mount: mounting /dev/disk/by-uid/04a93c6e-542b-4fd8-bc2e-b4705b14c1fa on /root failed: Invalid Arguement
mount: mounting /dev on /root/dev failed: No such file or directory.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: mounting /proc on /root/proc failed: No such file or directory.

Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg
```

So I'll try and run the LiveCD and see if I can "Try Ubuntu Without Installing", only to get the following errors:

```
mount: mounting /dev/sda1 on /cdrom failed: Invalid Arguement
stdin: error 0
``````
(Initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/Output Error
```

I've tried several LiveCD's (10.10 desktop / 10.10 netbook / 9.10 / 8.10) to no avail. I also tried to install those versions from the LiveCD but all resulted in errors.

I'm not very familiar with ubuntu and commands, so where relevant would appreciate full explinations.

Thanks in advance.

---

### Post by khamil8686 on 2011-02-02
it looks like its having trouble mounting the root partition so that it can be used, i dont know why loaning the computer to a friend would cause that except maybe the moving it around caused a cable or 2 to knock loose? im assuming its a desktop computer so if its a laptop this wouldnt really apply, but maybe check the cables inside and see if everything is securely connected where it should be

---

### Post by asdfasdf1122 on 2011-02-02
Sorry should have said it's a laptop. She seems to remember the update manager popping up shortly before it froze.

---

### Post by AlecJ on 2011-02-02
Sounds more like hardware.
Drive interface part of the motherboard, not booting on the CD tells you that..

---

### Post by khamil8686 on 2011-02-02
i 2nd AlecJ, maybe a piece of hardware started going bad on the mobo :(

---

### Post by asdfasdf1122 on 2011-02-02
Anyway to test?

---

### Post by AlecJ on 2011-02-02
I think you have tested it.
I think if the BIOS is new enough, you could try to boot from a USB stick?

---

