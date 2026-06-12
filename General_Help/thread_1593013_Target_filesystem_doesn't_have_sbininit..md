---
title: "Target filesystem doesn't have /sbin/init."
date: 2010-10-11
forum: General Help
---

### Post by FinalCoyote on 2010-10-11
Hey there all.

I've recently installed 10.10 onto my laptop, a Toshiba Equium A-100.
It's been working perfectly for the last few weeks, but today I woke up, booted and got this;

```
mount: mounting dev/disk/by-uuid/9f8e1fd1-ca75-4eeb-8afc-a6b7bd756180 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```Then it drops me into BusyBox with initramfs.

I have no idea what may have caused this, or how to fix it.
I'm a bit of a linux newbie, and while I can use the system fine, once we get into a shell I'm out of my depth.

Any help would be greatly appreciated. My laptop is useless now, and, unluckily, my 2000 word end-of-semester submission is on it. No, I didn't back it up because I wrote it last night. Arrgh.

---

### Post by GeorgeVita on 2010-10-11
Hi **FinalCoyote**, just an idea:

1. Boot a Live-CD or Live-USB
2. mount your hard drive from menu Places (click on your disk)
3. open a terminal window: Applications > Accessories > Terminal
4. see the name of your hard disk (like /dev/sda) using command: **df**
5. install again grub bootloader to hard disk: **sudo grub-install /dev/sda**

Note: you will use the generic device name and not the partition number! 
Use /dev/**sda** and not /dev/sda1
Replace **/dev/sda** with the actual device name from step#4.

Reboot to check. Above will recreate your grub menu. Other data will not be changed.

Regards,
George

---

### Post by FinalCoyote on 2010-10-11
Okay, tried this.

When I click on my filesystem in Places, I get the following error.
```

Unable to mount 58 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error in some cases useful info is found in syslog-dmesg | tail or so
```

---

### Post by GeorgeVita on 2010-10-11
I have never 'hit' this problem. Till another reader of this thread give you new ideas and as your drive seems to be **/dev/sda** try steps 3 to 5. It is possible to see new error but not destructive.
G

---

### Post by sazlik on 2010-12-13
I'm having the same problem. I don't suppose you ever figured this out, or anyone else is able to offer any suggestions?

---

### Post by pinnacle65 on 2010-12-26
> **sazlik said:**
> I'm having the same problem. I don't suppose you ever figured this out, or anyone else is able to offer any suggestions?


Me too ! I woke up today and I got this same problem! my computer wont boot up! im ubuntu newbie! this is terrible! what do i do!  

[IMG]http://i51.tinypic.com/3009kxw.jpg[/IMG]

---

### Post by amsterdamharu on 2010-12-26
[http://ubuntuforums.org/showthread.php?t=1652969](http://ubuntuforums.org/showthread.php?t=1652969)

---

