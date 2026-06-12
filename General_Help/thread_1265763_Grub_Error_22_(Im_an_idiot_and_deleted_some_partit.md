---
title: "Grub Error 22 (Im an idiot and deleted some partitions)"
date: 2009-09-13
forum: General Help
---

### Post by .adma on 2009-09-13
OK, I said it up front.  I know I shouldn't have deleted the partitions...but here is what happened

[LIST]
[*]Good ol Ubuntu 9.04 installed
[*]Tried to install Mythbunti twice on two new partions
[*]didn't really get Mythbuntu work like I wanted
[*]booted up in to good ol ubuntu, fired up Gparted, blew away those other two partitions
[*]thought to myself, grub won't like looking for those since they arent there
[*]opened up /boot/grub/menu.lst, and deleted references to old partitions
[*]Grub error 22
[*]live distroed in, restored previous menu.lst, but same error persists...
[*]How do I fix Grub?
[/LIST]

Thanks in advance, I feel dumb for doing this.  But sort of need urgent help since my PC is practically unusable unless I boot using SuperGrub (which is not a longtime solution)

per some other recommendations, I also tried 

```
adam@adam-desktop:~$ sudo grub-install /dev/sda1
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda1 as (hd0,0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
adam@adam-desktop:~$ 
```
which seemed promising, but alas, did not get rid of my grub error 22 problem

Adam

---

### Post by zvacet on 2009-09-14
Read [this]("http://members.iinet.net.au/~herman546/p15.html#22") and see if it is of any help to you.

---

### Post by .adma on 2009-09-27
you are a gentleman and a saint!

---

