---
title: "Grub detects two Ubuntu"
date: 2009-07-12
forum: General Help
---

### Post by wcasper4 on 2009-07-12
I have loaded Ubuntu dual-boot next to my XP. I have been using Ubuntu ever since. Recently I ran into an issue. When I restart, on the Grub boot menu it seems to be that there are two instances of Ubuntu that Grub detects, both seem the same and seem to work well, but why is this? I didn't have both before? And, how do I get rid of one, and which one?

The Grub menu looks like this:
Ubuntu 9.04, kernel 2.6.28-13-generic
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Other Operating Systems:
Windos XP

Any suggestions?

---

### Post by earthpigg on 2009-07-12
this is perfectly normal!

see the -13 and the -11?

those are two different linux kernels. -11 is older, -13 is newer... your install came with only -11, and then a later update got -13. it keeps the -11 one just in case you discover something not quite working right with -13.

a kernel is at the very heart of any operating system, and is the most important part. a kernel that does not play well with your hardware would make your system unusable -- ubuntu is smart and keeps the old one around just in case.

---

### Post by twright on 2009-07-12
This is completly normal, it allowes you to use old versions of the 'kernel' which updates have past replaced. If you want to remove the old ones you can use System->Administration->Computer Janitor

---

### Post by wcasper4 on 2009-07-12
Wow ok, thanks. As you can see I am new to this... but it's so much better. 
Thanks for allowing me to learn.

---

### Post by Finalfantasykid on 2009-07-12
If after a while it starts to get cluttered up(like after 3 or 4 kernel updates) you can comment out the older kernels.

```
$ cd /boot/grub/
$ sudo gedit menu.lst
```then you will see something like this...

```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Notice how the older kernels have a pound sign in front of each line.  That will stop those older kernels from cluttering up your grub menu.

---

### Post by twright on 2009-07-12
I would not recommend this method, you would need to redo it every time you install a new kernel version + this file will be replaced in the next version of Ubuntu anyway. Instead you can just remove old kernels, they are not doing any good once you are sure the new one works.
> **Finalfantasykid said:**
> If after a while it starts to get cluttered up(like after 3 or 4 kernel updates) you can comment out the older kernels.

```
$ cd /boot/grub/
$ sudo gedit menu.lst
```then you will see something like this...

```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Notice how the older kernels have a pound sign in front of each line.  That will stop those older kernels from cluttering up your grub menu.

---

