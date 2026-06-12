---
title: "boot menu"
date: 2010-11-03
forum: General Help
---

### Post by eipapp on 2010-11-03
Whenever I start up my desktop computer I see the following boot menu:

GNU Grub Version 1.98-1ubuntu7

Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory Test (Memtest 86+)
Memory Test (Memtest 86+, serial console 115200)
Microsoft Windows XP Home Edition (on / dev/sda1)
Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)
Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)
Ubuntu, with Linux 2.6.32-20-generic (on /dev/sda5)
Ubuntu, with Linux 2.6.32-20-generic (recovery mode) (on /dev/sda5)

Is there a way to simplify the appearance of this screen without all of these options ? It seem every time we update to a newer version of the list continues to grow. Wish I could narrow choices to just Ubuntu (current version) and Windows. Help !! 

Thanks,
Eipap

---

### Post by ivarn on 2010-11-03
You get a new kernel so that if an update makes your system crash, you can use the old kernel and just remove the new kernel. Since you new kernel works you can remove it from Synaptic. Also you can use ubuntu-tweak if you think that's easier.
Or you can use a grub editor app such as kgrub-edit.
Actually, since you have 2 operating systems installed, the list will be long nomatter what you do.
You can remove everything but the two for ubuntu and one for windows.

---

### Post by sikander3786 on 2010-11-03
It is advised that you keep at least one older kernel besides the latest one so that if the latest one fails, you have a choice to go back into the older one and fix your computer.

You can search for the un-needed kernels in Synaptic, remove them and run

```
sudo update-grub
```

to get rid of the Grub menu entries.

---

### Post by garvinrick4 on 2010-11-03
I like the Synaptic way also, open Synaptic type in box the 2.6.32-24 if that is the offensive one and it will come up with generic and headers remove them and sudo update-grub and they will be gone. It is a good idea to keep 2 kernels for each install incase 1 of them gets a bit funky on you. (sorry for repeat was typing same time as previous post)
 You can install aptitude:
```
sudo apt-get install aptitude
```then upgrade using aptitude instead of apt-get.
```
sudo aptitude update && sudo aptitude upgrade
```this will keep system cleaner. Google aptitude in Ubuntu and read up on, very Interesting.
```
aptitude show (package name)
```Is nice to use to show what a package is and if it is installed also.

---

