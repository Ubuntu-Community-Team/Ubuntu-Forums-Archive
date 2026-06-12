---
title: "dynamic resize ubuntu partition"
date: 2009-11-30
forum: General Help
---

### Post by Jim55 on 2009-11-30
I did a search but could not find a solution to my two issues.

 I am new to ubuntu and would appreciate help in dynamically resizing ubuntu so that I can free up space to be used by XP.  I also would like to to change the grub menu such that XP is first on the list and boots by default after a shorter period than 10s.   
 

 I have a 1TB drive with 100gb as NTFS with XP and 900gb as extended.
 I installed ubuntu 9.1 “side by side” and reduced the XP NTFS to 59gb and the install showed ubuntu to be 41gb.  However, when the os came up it looks like ubuntu has all of the 872gb extended partition with XP NTFS at 59gb.  The 872gb is split between 863gb for ubuntu (EXT4) and 9gb for swap.  My preference is to give ubuntu 41gb.
 

 I have installed Gparted.   
 

 Your help would be appreciated.

---

### Post by fluffman86 on 2009-11-30
You want be able to edit your Ubuntu partition while logged into Ubuntu.  Instead, boot from the Live CD or USB, then load Gparted from System > Administration > Gparted Partition Editor and edit from there.

---

### Post by Jim55 on 2009-12-09
I resized ubuntu but now get "invalid signature" when I try to bring up XP.  How do I get XP back?

---

### Post by Leppie on 2009-12-09
try:
```
$sudo update-grub
```

---

### Post by Jim55 on 2009-12-09
This fixed my problem

sudo grub-mkdevicemap
sudo update-grub2

---

