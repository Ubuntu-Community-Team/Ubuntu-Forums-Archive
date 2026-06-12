---
title: "start up problem - after readonly system error !"
date: 2011-03-20
forum: General Help
---

### Post by naarkhoo on 2011-03-20
Let me tell whole the story !
I just installed wine and other packages, and in meanwhile noticed that I don't have enough space, then tried to remove some other files but discovered that the permission is changed and evertything is read only ! even for sudo !!! the error was some thing like readonly system error ...

I knew that If I restart, probably I encounter with starting up error and due to the cpu was working 100% and I coudn't halt it ! I reboot my machine ... and now stuck with starting up !!

first it come up with out "out of disk"

and then several error, like
> mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or direcotry
mount: mounting /proc on /root/proc failed: no such file or direcotry
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

and then
> 
BusyBox v.1.13.3 ...
and (initramfs)

I also did try to load with USB boot loader, but seems it doesn't work :(

I would be really appreciate if someone gives and clue ...

---

### Post by naarkhoo on 2011-03-20
I am trying to mount manually the disk,
by 
> mkdir hda1 hda3 hda4
mount -t vfat /dev/hda1 hda1 -o defaults,umask=0
 
but the error : B> lock device required
 
still lookforward to hearing from you !

---

