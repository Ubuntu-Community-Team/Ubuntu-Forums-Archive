---
title: "dual-booting 10.04 and 7"
date: 2010-06-15
forum: General Help
---

### Post by rablanken on 2010-06-15
Hi, I'm having trouble dual-booting ubuntu and windows 7. My laptop is a SONY VAIO VGN-AR170P, and in this model there are two internal HDD which were originally set-up in RAID configuration when I used windows, but when I switched to Ubuntu 10.04 I removed the RAID and now disk utility sees them as separate drives.

I already have Ubuntu installed on one drive, and the other one is free to be formatted and used in any way. I want to know if there is a way to install windoze 7 on that drive, and have a dual boot set up. I have the windows 7 CD and I've already tried to install it on that drive, but when I choose my free drive in the set-up screen, I always get the same error message, saying that it can't create/locate the partition table or something around those lines. Deleting the partition on the free drive and having the Windows installer reformat it does not work either.

Any help would be greatly appreciated. I attached a screen of disk utility. Thank you

---

### Post by Chesamo on 2010-06-15
You really want to install Windows *first*, then Ubuntu. Install Windows on its own (on a single drive), then plug in the second drive (don't unplug the first one) and install Ubuntu onto it. Ubuntu's installer will see the second hard drive and make a GRUB entry for it.

Also make sure the Ubuntu hard drive is the first one in the boot order.

---

### Post by rablanken on 2010-06-15
So then what is a sure-way of installing windows? Should I try to install to Windows 7 on the same drive as Ubuntu is installed on? And both the drives in my laptop are internal, how do I unplug one?

---

### Post by garvinrick4 on 2010-06-15
> **rablanken said:**
> So then what is a sure-way of installing windows? Should I try to install to Windows 7 on the same drive as Ubuntu is installed on? And both the drives in my laptop are internal, how do I unplug one?
You do not have to unplug you can format that the sdb drive in NTFS and install 7 on it. When you are done installing you just have to put the install CD in for Ubuntu and choose Try Ubuntu and then put in a few commands to reinstall grub2 so you can select either one to boot into.

---

### Post by wilee-nilee on 2010-06-15
Wait a minute if Ubuntu is put on the second drive grub will default to the first one. You have to point grub at the 2nd drive by checking the advanced tab in the last gui of the install process. It would probably be sdb just confirm this by looking at gparted or knowing for sure where your installing to. Don't put grub on a partition which would be sda or sdb with a number like sdb1.

It doesn't matter in which order windows or Ubuntu is installed. It does matter though if you have XP and W7 or any other combination of dual MS boots so that the MS boot picks up the other MS.

With just a true dual boot not** wubi** the bootloaders if everything is set up correctly can be reloaded with 2 commands from a install cd/dvd every time no problem.

---

### Post by garvinrick4 on 2010-06-15
While you are in in Live Cd for Ubuntu. (Try Ubuntu). Choose the disk utility again and select your Ubuntu drive and Label it lucid. After you install Windows 7 take out the Windows install CD and put in the Ubuntu CD and open a terminal. Applications/Accessories/terminal.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sdax /media/lucid
``` (change x to what your ubuntu install is)
                          ```
sudo grub-install --root-directory=/media/lucid /dev/sda   
``````
sudo umount /media/lucid
```You are making a folder or directory for /media/lucid 
You are mounting your partition
you are installing grub2 into your mbr of sda. (overwriting the one Windows put in)
you are unmounting lucid

To find out your sdax partition # use this code
```
sudo fdisk -l
``` (that is a small L)

Once you are back in running Ubuntu put in these to codes.

sudo update-grub

sudo grub-mkconfig

All of this given you already have Ubuntu install on your first drive. We call sda and second drive is sdb

---

