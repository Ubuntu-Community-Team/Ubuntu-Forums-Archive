---
title: "Fstab Help"
date: 2011-09-24
forum: General Help
---

### Post by trackmagic on 2011-09-24
I have been trying to make it so my windows partition loads on my desktop when I start Ubuntu, but I have had some problems getting it work. I figured out I need to edit my fstab file, but it still does not seem to work. My original fstab file had this code:

UUID=b761cc86-818e-4adc-b010-aa600021bf59 none  swap  sw   0    0

I replaced it with this (and many other things that did not work):
BOAC6686AC664746 /home/ben/Desktop ntfs-3g defaults,locale=en_US.utf8 0 0

This gives an error message when I start Ubuntu.

Can somebody tell me what is wrong?

---

### Post by papibe on 2011-09-25
The line you replaced is necessary for Ubuntu to work properly. Put it back on fstab. You just needed to add a line, but not modify the existing ones (at least in this case).

Hope it helps,
Regards.

---

### Post by trackmagic on 2011-09-25
Thanks, I added that line back in and it worked (loaded with no errors)

I tried to append a new line that would load the windows partition. My fstab file now looks like this:

# swap was on /dev/sda7 during installation
UUID=b761cc86-818e-4adc-b010-aa600021bf59 none            swap    sw              0       0
/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0	 0

When I add that code I get another error message. That is strange because I found that code on this fstab instruction page:

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

Also, If that did work I am supposed to use my desktop path where it says "/media/windows" if I want to mount on my desktop right?

Thanks again for you help with this!

---

### Post by papibe on 2011-09-25
A few things to consider:
[LIST]
[*]The safest way to mount a disk is using its UUID. To get disk's uuids run this:```
sudo blkid 
```
[*]The directory in which you mount the filesystem has to exsist. In this case the dir windows under /media
[/LIST]
I hope that helps,
Regards.

---

### Post by patryk77 on 2011-09-25
> ```
/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0	 0
```
That is 7 arguments, fstab expects 6 (remove one of the 0s at the end).

What is the error message?

And what does running:
sudo fdisk -l
give you when your system is running?

---

### Post by mhgsys on 2011-09-25
a example; I'll use /dev/sdb1 as my example and bold out what info I mean'
also; you should writeout/save the file you edited of course.

you should make a directory you want to mount to; 

```
sudo mkdir /media/stor
```
then you can mount your disk like;

```
sudo mount /dev/sdb1 /media/stor
```
when mounted; in your /etc/mtab you'll find some valuable data
f.e

```
nano /etc/mtab
```
gives 

> /dev/sdb1 /media/stor fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
Were gonna use some of that data to put in fstab;
best way is to use blkdid so all disks have there own UUID.
use the command blkid to obtain these UUID; 

```
sudo blkid
```
f;e blkid gives me;

> /dev/sda1: UUID="BC9003C9900388DA" TYPE="ntfs" 
/dev/sda2: UUID="8d824aa4-eb23-4333-b62b-7edf4d9b9135" TYPE="swap" 
/dev/sda3: UUID="a6bec86d-0211-4086-a239-9bafed817dc7" TYPE="ext4" 
/dev/sdb1: LABEL="STORAGE" UUID="0CF0267DF0266CE0" TYPE="ntfs" 
/dev/sdc1: LABEL="DATA" UUID="561CFADD1CFAB759" TYPE="ntfs

Now; We wanted to have /dev/sdb1 mounted as /media/stor at boot; So were gonna edit the /etc/fstab and add the UUID and some info we found in /etc/mtab.


```
sudo nano /etc/fstab
```
and add the line

> UUID=0CF0267DF0266CE0 /media/stor ntfs rw,nosuid,nodev,allow_other 0 0 

you can now test you're fstab by umounting the manual mount 

```
sudo umount /dev/sdb1
```
and mount by fstab

```
sudo mount -a
```
after doing this; it will always mount on (re)boot
__________________

---

### Post by dcstar on 2011-09-25
> **trackmagic said:**
> I have been trying to make it so my windows partition loads on my desktop when I start Ubuntu, but I have had some problems getting it work. I figured out I need to edit my fstab file
.......

Just install the **pysdm** package and it will make all the necessary changes for you when you run it.

---

