---
title: "Editing GRUB file"
date: 2009-09-27
forum: General Help
---

### Post by gyan on 2009-09-27
Hello.
Is someone willing to help me edit the grub menu.lst config file?

I have installed XP over Ubuntu, then used one of those tutorials to restore GRUB as the default boot manager (sudo grub, find ..root, setup hd0 quit).

Now after the system boots, Ubuntu loads automaticaly, i can't choose to run either another kernel or memtest.

Here is my grub config file:
[http://docs.google.com/Doc?docid=0ARXJ8YFTQe2YZGdxZnN4cjNfMzhmMmNuc2NjNA&hl=en](http://docs.google.com/Doc?docid=0ARXJ8YFTQe2YZGdxZnN4cjNfMzhmMmNuc2NjNA&hl=en)

How should i configure grub in order to detect the Windows XP os ?
Thanks.

---

### Post by zeroseven0183 on 2009-09-27
You don't have a Windows entry in your menu that looks something like this.

title  Microsoft Windows XP Pirated Edition
root   (hd0,0)
makeactive
chainloader +1

Did you follow the instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ?

---

### Post by sahabcse on 2009-09-27
For fixing the grub pls follow below url

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by gyan on 2009-09-27
I'm receiving an Error 13: invalid or unsupported executable format

How do i identify which partition is Windows Xp installed on ?
And how do i edit the grub config file again in order to make it boot right?
At this moment, the xp settings looks like this:

title        Windows XP
root        (hd0,0)
makeactive
chainloader     +1

And the boot.ini from xp partition:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by SuperSonic4 on 2009-09-27
Use ```
sudo fdisk -l
``` to find it. If you don't know post it here

---

### Post by gyan on 2009-09-27
ok so it's /dev/sda3

now how do i tell that to grub ? :D

---

### Post by SuperSonic4 on 2009-09-27
sda3 is the **third** partition on the **first** hard drive. But since grub starts at 0 you actually want (0,2)


```
title Cookie Monster
root (hd0,2)
makeactive
chainloader +1
```

needless to say you can make the title whatever you like xD

---

### Post by gyan on 2009-09-27
Thanks everyone for the fast and great support.
Solved :D

---

