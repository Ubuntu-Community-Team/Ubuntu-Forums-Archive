---
title: "grub2 and /boot"
date: 2010-12-24
forum: General Help
---

### Post by mattman85 on 2010-12-24
I followed instructions from the [Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") page, and I've done a lot of searching, but nothing answers what I want to ask..

I removed old kernels via Synaptic, but I still see their choices in the Grub2 menu when I start my laptop. I also still have the old files in /boot. Can I delete the old files?

```
computer:~$ ls -a /boot
.                             memtest86+.bin
..                            memtest86+_multiboot.bin
abi-2.6.32-24-generic         System.map-2.6.32-24-generic
abi-2.6.32-27-generic         System.map-2.6.32-27-generic
abi-2.6.35-22-generic         System.map-2.6.35-22-generic
abi-2.6.35-23-generic         System.map-2.6.35-23-generic
config-2.6.32-24-generic      vmcoreinfo-2.6.32-24-generic
config-2.6.32-27-generic      vmcoreinfo-2.6.32-27-generic
config-2.6.35-22-generic      vmcoreinfo-2.6.35-22-generic
config-2.6.35-23-generic      vmcoreinfo-2.6.35-23-generic
grub                          vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-27-generic
initrd.img-2.6.32-27-generic  vmlinuz-2.6.35-22-generic
initrd.img-2.6.35-22-generic  vmlinuz-2.6.35-23-generic
initrd.img-2.6.35-23-generic
```

I'm running the 2.6.35-23 kernel. Can I delete any/all of the past ones, including the 2.6.35-22 files?

Is it as simple as doing a sudo rm command?

like I said, I searched, and couldn't find anything to just tell me that. If someone knows of a thread that does cover it, and I just overlooked it, that would help, too!

Thanks!

---

### Post by QLee on 2010-12-24
[QUOTE=mattman85]... I also still have the old files in /boot. Can I delete the old files?
...
I'm running the 2.6.35-23 kernel. Can I delete any/all of the past ones, including the 2.6.35-22 files?

Is it as simple as doing a sudo rm command?

...[/QUOTE]

My advice would be, in order to not leave uneeded things behind on your system that would just be taking space, that you don't just remove what you are looking at.

Are you sure the package manager removed the old images successfully? Wouldn't take much time to try it again to verify that.

Then you would use update-grub to get a new GRUB2 menu if the package manager doesn't run it automagically for you. 


[Edit] I might as well add, I sometimes use dried tomatos in my fruit salad. So, given your sig, you may not want my advice.

---

### Post by psusi on 2010-12-24
Yes, remove the packages correctly through the package manager.  You can run dpkg -S /some/file to search for which package that file belongs to, then remove it.  If dpkg -S does not report it belongs to any package, then you just have to rm it.

---

### Post by Quackers on 2010-12-24
And run sudo update-grub afterwards.

---

