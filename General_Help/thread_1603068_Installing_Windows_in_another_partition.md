---
title: "Installing Windows in another partition"
date: 2010-10-22
forum: General Help
---

### Post by awd01 on 2010-10-22
Hello, I am using Ubuntu 10.04 and i want to install windows into another partition in order to play some games. I created a partition (GParted live) 80GB in ext2 and later i convert it to NTFS ( I didnt know what the ext2 was) after that i run the windows live cd but i occured an error that windows can not be installed in none of my partitions because my partitions are unrecognizable. Why does this happened? I think that has to do with my file stystem.. but i convert in ntfs...:confused:
Any suggestions? I checked many dual boot (ubuntu-wnds) guides but i didnt find a solution.

---

### Post by Grenage on 2010-10-22
The partition format shouldn't be an issue.  During the install process, can you not delete the partition and then re-create it?

---

### Post by sikander3786 on 2010-10-22
How did you convert ext2 > NTFS?

I would be better to just delete the partition from gparted and then create a partition in the free space during the Windows installer.

In addition, Windows will need a primary partition to boot from and after installation you'll need to reinstall Grub in order to boot into Ubuntu. We can guide you incase you are not sure.

It would be better to post the output of

```
sudo fdisk -l
```

So we can have a better idea of your current setup.

---

### Post by awd01 on 2010-10-22
> **Grenage said:**
> The partition format shouldn't be an issue. During the install process, can you not delete the partition and then re-create it?
 
no i cant. there are some options that i cant select. there are in the same color like the ''next'' button that i cant select.

---

### Post by awd01 on 2010-10-22
> **sikander3786 said:**
> How did you convert ext2 > NTFS?
 
I would be better to just delete the partition from gparted and then create a partition in the free space during the Windows installer.
 
In addition, Windows will need a primary partition to boot from and after installation you'll need to reinstall Grub in order to boot into Ubuntu. We can guide you incase you are not sure.
 
It would be better to post the output of
 
```
sudo fdisk -l
```
 
So we can have a better idea of your current setup.
 
ok i'll post the result and yes i want you to guide me m8 :) cause i am n44b.
Thank you. i'll post them in some hours.

---

### Post by awd01 on 2010-10-22
> **sikander3786 said:**
> How did you convert ext2 > NTFS?

I would be better to just delete the partition from gparted and then create a partition in the free space during the Windows installer.

In addition, Windows will need a primary partition to boot from and after installation you'll need to reinstall Grub in order to boot into Ubuntu. We can guide you incase you are not sure.

It would be better to post the output of

```
sudo fdisk -l
```So we can have a better idea of your current setup.



these are my results m8 : 
```
awd01@awd01-desktop:/$ sudo fdisk -l
[sudo] password for awd01: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006cab6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       65340   524837888   83  Linux
/dev/sda2           76697       77826     9066497    5  Extended
/dev/sda3           65341       76696    91213824   83  Linux
/dev/sda5           76697       77826     9066496   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I cant make another partition during the windows installer because these actions are like ''frozen'' it says that it is unrecognizable. I select each partition and the same error.

---

### Post by Grenage on 2010-10-22
There are no NTFS partitions there; which one did you format?

---

### Post by awd01 on 2010-10-22
> **Grenage said:**
> There are no NTFS partitions there; which one did you format?[FONT=monospace]\

[/FONT]this one:**   /dev/sda3           65341       76696    91213824   83  Linux ** 
i run the disk utilities i select format volume and i select the NTFS
but the process was very fast maybe something happened.. :confused::confused:

---

### Post by Quackers on 2010-10-22
Did you click on the green tick in the toolbar to apply the proposed changes? Or did you forget, like I have done :-)

---

### Post by awd01 on 2010-10-22
> **Quackers said:**
> Did you click on the green tick in the toolbar to apply the proposed changes? Or did you forget, like I have done :-)

yep I did it:)

---

### Post by sikander3786 on 2010-10-22
Just delete sda3 from gparted and again post the output of

```
sudo fdisk -l
```

---

### Post by awd01 on 2010-10-22
> **sikander3786 said:**
> Just delete sda3 from gparted and again post the output of

```
sudo fdisk -l
```
 do i have to delete the partition? there is no other solution? i just want this partition to be recognizable from windows :) there isnt other way?

---

### Post by sikander3786 on 2010-10-22
> **awd01 said:**
> do i have to delete the partition? there is no other solution? i just want this partition to be recognizable from windows :) there isnt other way?
Unmount the drive from gparted, Right click > Format to > NTFS.

There is no real deal in deleting the whole partition. You are going to lose the data anyway.

As I mentioned before, it would be better to just delete the partition and then create a new partition from the Windows installer in the un-allocated space.

---

### Post by Grenage on 2010-10-22
> **sikander3786 said:**
> As I mentioned before, it would be better to just delete the partition and then create a new partition from the Windows installer in the un-allocated space.

Yup, I'd do that.  Windows can't complain if it's creating the partition.

---

### Post by awd01 on 2010-10-22
> **Grenage said:**
> Yup, I'd do that.  Windows can't complain if it's creating the partition.

ok i'll delete the partition but guys i cant create another partition from the windows installer these buttons are frozen! i dont know why:)

---

### Post by Grenage on 2010-10-22
Are the discs unrecognisable, or the partitions?  What _exactly_ does it say?

---

### Post by awd01 on 2010-10-22
> **Grenage said:**
> Are the discs unrecognisable, or the partitions?  What _exactly_ does it say?

let me check

---

### Post by awd01 on 2010-10-26
i run the windows live i deleted the partition and i made another1. I couldnt create another because there was no space or smth like that. So,I installed windows.  After that ubuntu weren't running.. only windows. I run the ubuntu live I installed Grub2 and now i can't see windows and also the grub menu

---

### Post by sikander3786 on 2010-10-27
> **awd01 said:**
> i run the windows live i deleted the partition and i made another1. I couldnt create another because there was no space or smth like that. So,I installed windows.  After that ubuntu weren't running.. only windows. I run the ubuntu live I installed Grub2 and now i can't see windows and also the grub menu
Doesn't sound good to me. Feels like you messed up your Ubuntu install and installed Windows over it. Please post the output of bootinfoscript as per instructions here. You'll need to perform that from a Live CD.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please wrap the output with proper code tags #.

---

### Post by crackpotfox on 2010-10-27
Delete the NTFS partition sothat it is just unallicated space, then windows will recognse it. but if you install windows after ubuntu, you will be subjected to the windows test of courage and ubuntu knowlege ;)  in other words, grub will have to be reinstalled or whatever

---

