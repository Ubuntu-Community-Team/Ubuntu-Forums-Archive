---
title: "Ubuntu not booting"
date: 2010-08-14
forum: General Help
---

### Post by CaptainWraith on 2010-08-14
i installed ubuntu 9.10 on my stepbrothers computer  (using wubi)  and now it isnt booting.it goes to a page and gives a command line and when the "boot" command is put in it says something about no kernel to boot from.  (i do not have access to the computer as he lives 3 hours away so i just have what he tells me)   he says hes done nothing different recently and hasnt installed anything new.  any help would be appreciated

---

### Post by bcbc on 2010-08-14
Does he first see the Windows Boot Manager, then selects Ubuntu, then the grub command line? But if he selects Windows, it boots windows normally?

Or, does it not boot anything anymore, rather it just goes straight to a grub prompt?

---

### Post by CaptainWraith on 2010-08-22
windows boots fine but when he selects ubuntu it wont boot

---

### Post by chips24 on 2010-08-22
> **CaptainWraith said:**
> windows boots fine but when he selects ubuntu it wont boot

Hmm... try uninstalling it and try another version.

---

### Post by bcbc on 2010-08-22
> **CaptainWraith said:**
> windows boots fine but when he selects ubuntu it wont boot

Since you installed Ubuntu 9.10 you should first try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If that fails, you could try booting it manually from the grub prompt. You need to know which partition the root.disk is on. If you don't know you can search for it.
```
ls
``` (small LS) shows available partitions
Then for each partition:
```
ls (hdX,Y)/ubuntu
``` 
which will say file not found until you find the correct partition. e.g. ls (hd0,1)/ubuntu

Then you can derive the device name:
hd0,1 = /dev/sda1
hd0,2 = /dev/sda2
hd1,1 = /dev/sdb1

Then boot it (assume you found it on hd0,2 i.e. /dev/sda2):
```
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

```

After booting run 
```
sudo update-grub
```

If you find that all too daunting or if it doesn't work, then I recommend retrieving your important data from the root.disk and reinstalling. The wubi guide shows how to do that [here]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") or install something to view the files under windows [here]("https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?") (you'll need one that supports ext4).

---

