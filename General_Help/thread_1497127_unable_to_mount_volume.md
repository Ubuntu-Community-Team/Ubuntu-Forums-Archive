---
title: "unable to mount volume"
date: 2010-05-30
forum: General Help
---

### Post by aaanekre on 2010-05-30
I have been taking disks in and out of the system and have now problems mounting one of them.
Please help me out. I am new to ubuntu but know a lot about computers and windoze...

Using the GUI "Disk utility" I can see my drive with the name: 1TB_OLD1 but when I try to mount it I get the error: * "according to mtab, /dev/sde1 is already mounted on /"*

This is a NTFS volume and "Disk utility" reports that this device is:   "/dev/sda1/"  which is a bit confusing as the error say:  */dev/[SIZE=2]**sde1**[/SIZE] is already mounted *

I tried to edit the blkid.tab where my 1TB_OLD1 disk was listed but after a reboot this file is now missing! and the problem is still the same

[B][SIZE=2]This is my fstab file:
[/SIZE][/B]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01d14ecd-0a65-4e50-92ae-6367880dfaf8 none            swap    sw           $

[SIZE=2][B]This is my mtab file:
[/B][/SIZE]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01d14ecd-0a65-4e50-92ae-6367880dfaf8 none            swap    sw           $

---

### Post by lmarmisa on 2010-05-30
Maybe an UUID is duplicated.

Please, type this command:

> 
sudo blkid


---

### Post by aaanekre on 2010-05-30
Here is the output from the blkid command:

/dev/sda1: LABEL="1TB_OLD1" UUID="6B01402A55383BAC" TYPE="ntfs" 
/dev/sdb1: LABEL="500GB_1" UUID="6FB189402DD9E0A9" TYPE="ntfs" 
/dev/sdd1: LABEL="1.5TB_1" UUID="147F242037EC1D52" TYPE="ntfs" 
/dev/sdc1: LABEL="1.5TB_0" UUID="77a1c2c5-8db3-4875-872e-81a3b477339b" TYPE="ext4" 
/dev/sde1: UUID="0ab26c74-c44c-4adf-94ff-f12ea8495ab6" TYPE="ext4" 
/dev/sde5: UUID="01d14ecd-0a65-4e50-92ae-6367880dfaf8" TYPE="swap" 
/dev/sdf1: LABEL="1T-EXT2" UUID="5A0A5F720A5F4A61" TYPE="ntfs" 

sde1 is my system drive...

---

### Post by dino99 on 2010-05-30
install mountmanager to easily deals with your devices and partitions: tweak it into system admin mountmanager

---

### Post by lmarmisa on 2010-05-30
This line of your /etc/fstab seems incorrect:

> 
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda1 is not an ext4 partition. 

I believe that this line would be fine:

> 
UUID=0ab26c74-c44c-4adf-94ff-f12ea8495ab6 /               ext4    errors=remount-ro 0       1


---

### Post by lmarmisa on 2010-05-30
If you are moving disks, do not use absolute positions for your devices (/dev/sda1). 

UUIDs are more appropriate not only for your case but also for all cases, IMHO.

Try to edit your /etc/fstab file and change the wrong line.

Maybe a **sudo update-grub** command would be needed.

---

### Post by aaanekre on 2010-05-30
Thanks to all of you! Its now working. Also after a reboot..
I tried dino99's suggestion first, and that worked. :P.  I changed the mount point to media\1TB_OLD1 and mounted the drive with mountmanager.  When I first opened mountmanager the default mountpoint was only  \.

Imarmisa:  
you are probably correct in your assumption. Here is my fstab now:

UUID=147F242037EC1D52 /media/1.5TB_1 ntfs-3g defaults 0 0
**[SIZE=2]UUID=6B01402A55383BAC /media/1TB_OLD1 ntfs-3g defaults 0 1[/SIZE]**
UUID=0ab26c74-c44c-4adf-94ff-f12ea8495ab6 / ext4 defaults 0 0
UUID=01d14ecd-0a65-4e50-92ae-6367880dfaf8 swap swap sw 0 0


I agree that it seems better to use UUID. But how do I choose to use it? I just installed 10.04 desktop with everything default.

I have to admit that I am sometimes tempted to go back to windows on my server, but LINUX is cool, its free, and the forum is great!
Thanks again.

---

### Post by ryan858 on 2010-05-30
> **aaanekre said:**
> 
I agree that it seems better to use UUID. But how do I choose to use it? I just installed 10.04 desktop with everything default.


Well, you kind of already did, here:
> **aaanekre said:**
> 
UUID=147F242037EC1D52 /media/1.5TB_1 ntfs-3g defaults 0 0
**[SIZE=2]UUID=6B01402A55383BAC /media/1TB_OLD1 ntfs-3g defaults  0 1[/SIZE]**
UUID=0ab26c74-c44c-4adf-94ff-f12ea8495ab6 / ext4 defaults 0 0
UUID=01d14ecd-0a65-4e50-92ae-6367880dfaf8 swap swap sw 0 0

If it says UUID= instead of /dev/whatever then you're using uuid.

Also Ubuntu 10.04 uses UUID's by default, so you shouldn't have to do anything.

---

### Post by wangsuda on 2010-05-30
I'm not really good at this, but this command has worked for me when mounting drives. Perhaps it can help you:
```
sudo chown -R *COMPUTER NAME*:*COMPUTER NAME* /media/*NAME OF DISK HERE* 
```
EXAMPLE: If your computer's name is bob, and the disk you want to mount is jane, then the command would be *sudo chown -R bob:bob /media/jane*

---

