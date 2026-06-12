---
title: "How to format (grub) ?"
date: 2006-05-29
forum: General Help
---

### Post by Morientes on 2006-05-29
Now that Dapper is comming out I would like to format my Linux drive and install it clean from scratch!
I can easily format the linux drive from partition magic in windows, but I wonder what would happen to the grub menu then? Will it just stay the way it is untill modified by the dapper installer? Is there something one should do about it?

---

### Post by kzutter on 2006-05-29
I would think that if you do a true install ( rather than a dist-upgrade) you will be presented with the option to format any partition you want.
I have not done a dapper install yet, but breezy gave you this option.

---

### Post by bullgr on 2006-05-29
if you need dual boot (windows/linux), you can use a windows install cd, boot with it,
go to command prompt (fix errors option or like that, i don't remember exactly)
and type "fixmbr".

this fix the master boot record, grub is gone and you able to boot dyrectly to win.

the other sollution is to install directly darper and the grub will auto-update thru
the install proccess

---

### Post by Cavalierski on 2006-05-29
Yes, it stays as it is till you over write it.  Of course if you select one which is formated, grub throws a error. If you modify the grub menu before the format, it would looks better , however if you gonna install Dapper anyway it will update the grub. I guess you don't need to worry about it. 

# Recently I've formated some h/d with [gparted live cd,]("http://gparted.sourceforge.net/livecd.php")  it works quicker than knoppix. But if you plan to install Dapper, gparted is already in the install CD, so you don't need it...

---

### Post by Morientes on 2006-05-30
Ok thank you for the replies! I guess I'm just gonne install it then!

---

