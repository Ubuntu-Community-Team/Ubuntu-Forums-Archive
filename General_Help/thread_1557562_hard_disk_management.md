---
title: "hard disk management"
date: 2010-08-20
forum: General Help
---

### Post by lisarox on 2010-08-20
is there a decent hard disk management apt . you see when i started using ubuntu i specified  2 gigs for ext filesystem drive because at that time windows was my basic OS . but now ubuntu became almost my only OS , so i wanna cut out like 20 gigs of the ntfs windows drive and add them to ubuntu's filesystem without removing or formating neither OS's or drives

is there a software that can do that ?
thanks ^_^

---

### Post by ScarletWyvern on 2010-08-20
Administration > gParted

Be advised, you're editing partitions here. If you're not careful, you can kill your whole system.

---

### Post by Miljet on 2010-08-20
1. As has been advised, backup any important data on both partitions. Resizing almost always goes without a hitch, but that is little consolation if you are one of the very few to lose data.

2. Partitions can not be resized if they are in use. Therefore you need to boot a live CD and make the changes from there.

3. No one can give you specific instructions without knowing how your current partition table is set up. Open a terminal (Applications -> Accessories -> Terminal) and copy and paste the following code
```
sudo fdisk -l 
```
That is a small letter L, not a one. You will be asked for your password. It will not show as you type it in but that is normal. Just type in your regular password and hit Enter. Then copy the results and paste it here and someone will give you specific instructions.

---

### Post by Quackers on 2010-08-21
If you are using Vista or Windows 7 I would recommend that you try resizing the Windows partition from within Windows. Start > Right-click on Computer > Manage > Disk Management then right-click on your Windows partition and choose resize. It may be resizable and it may not. It's worth a try though, as it is the quickest and safest way to resize it. This won't work in XP though.

---

