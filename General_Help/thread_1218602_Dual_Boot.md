---
title: "Dual Boot"
date: 2009-07-20
forum: General Help
---

### Post by geolink on 2009-07-20
hello,
I have two hard drives in my computer. one with ubuntu and one with windows xp. is there any way to set it up that i get a prompt window for which hdd i want to boot from

---

### Post by blueridgedog on 2009-07-20
If you setup your system to boot from either drive currently will you get XP on one and then Ubuntu on the other?  If so, the easiest way to boot each OS is to set your BIOS up to boot from the Ubuntu drive and ad an entry in the grub menu to boot the xp OS off of the other drive.  If the answer is yes, I can talk you through editing your grub menu if you post the output of

```
sudo fdisk -l 
```

(This will simply print a list of your hard disks and partitions that you can copy and paste in a reply)

and 

```
cat /boot/grub/menu.lst
```

(This will display your current grub boot menu...menu.lst, so you can copy and paste in a reply).

---

