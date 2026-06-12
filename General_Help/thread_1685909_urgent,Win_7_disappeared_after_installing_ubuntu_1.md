---
title: "urgent,Win 7 disappeared after installing ubuntu 10.04 on netbook..."
date: 2011-02-11
forum: General Help
---

### Post by mashv27 on 2011-02-11
I have win 7 on the netbook Asus system.

I did a installation of the ubuntu 10.04 on the netbook which erased the window 7 operatingt

After trying out while various options, it fails on the grub dos prompt.

Dual boot option is not displayed duting the booting process.

Please help of any ways to get the windows 7 restored on the Asus neitbook which has the 
   ubuntu 10.04 installed.

thanks a lot,

Mahesh.

---

### Post by wilee-nilee on 2011-02-11
> **mashv27 said:**
> I have win 7 on the netbook Asus system.

I did a installation of the ubuntu 10.04 on the netbook which erased the window 7 operatingt

After trying out while various options, it fails on the grub dos prompt.

Dual boot option is not displayed duting the booting process.

Please help of any ways to get the windows 7 restored on the Asus neitbook which has the 
   ubuntu 10.04 installed.

thanks a lot,

Mahesh.

From the Ubuntu install or a live Ubuntu cd booted run this command in the terminal and post the readout
sudo fdisk -lu

---

### Post by sanderj on 2011-02-11
... or, if you prefer mouse-clicking in a GUI:

System -> Aministration -> Disk Utility. Then click on your harddisk in the left pane. Check if you see a "NTFS" partition on the right.

See my screendump

---

### Post by alphaamanitin on 2011-02-11
So what exactly happened?  Did you over write your Windows Partition, or did you install Ubuntu in a side by side partition layout and now simply cannot boot into Windows 7?  If you completely insalled Ubuntu over Windows 7 you are in for some trouble, and stop using the computer if you want to recover anything.

AlphaA

---

