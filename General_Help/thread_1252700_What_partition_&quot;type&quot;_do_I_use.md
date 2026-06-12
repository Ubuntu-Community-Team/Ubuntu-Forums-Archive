---
title: "What partition &quot;type&quot; do I use?"
date: 2009-08-29
forum: General Help
---

### Post by lakelovers on 2009-08-29
I'm stuck. I added an external usb drive which has a msdos partitioning on it. I want to re-partition the drive to dedicate it exclusively to Ubuntu (I haven't Windows for years). So, I open Gparted, select drive /dev/sdb and then pull the drop-down menu for partition type. Ten types show up. I'm guessing the one I should use is "gpt." put I'm not 100% sure and I don't want to screw up. Is that the correct partition type? I'm running 9.04.

---

### Post by DeMus on 2009-08-29
> **lakelovers said:**
> I'm stuck. I added an external usb drive which has a msdos partitioning on it. I want to re-partition the drive to dedicate it exclusively to Ubuntu (I haven't Windows for years). So, I open Gparted, select drive /dev/sdb and then pull the drop-down menu for partition type. Ten types show up. I'm guessing the one I should use is "gpt." put I'm not 100% sure and I don't want to screw up. Is that the correct partition type? I'm running 9.04.

You better choose Ext3 or even Ext4 when your OS supports it.

---

### Post by x33a on 2009-08-29
There is no gpt option in my gparted at least. and it is not even a file system. use ext3 for storage partition as demus said.

more info on gpt:

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by NoaHall on 2009-08-29
I'd use ext3, as 4 isn't properly supported yet, although it will be with Karmic

---

### Post by fluffman86 on 2009-08-29
ext4 is fully supported in Jaunty; it's just not the default for the installer.  I would recommend formatting as ext4--huge speed improvements.

---

### Post by louieb on 2009-08-29
> **lakelovers said:**
>  So, I open Gparted, select drive /dev/sdb and then pull the drop-down menu for partition type. Ten types show up. I'm guessing the one I should use is "gpt." put I'm not 100% sure and I don't want to screw up.

Just guessing you opened Device>Set disk label..

If this is an Apple computer the partition table type of **GPT** is alright. Except on Apple computers - not used much. 

Otherwise use the default** msdos** partition table type. This is the standard partition table type in use. Works fine on any PC running Linux or windows. Heed the waring that writing a new disk label will remove any and all partitions currently on the drive.

---

### Post by lakelovers on 2009-08-29
Okay. Well, obviously I don't know how to use gparted though I've used it in the past. (Memory impaired?) This is a blank drive except for the "fat32" file system which I believe is a ms file. I'm using a Dell computer. Is it okay to reformat with the fat32 file system there, or will that be removed so I can move forward with ext3?

---

### Post by NoaHall on 2009-08-29
Jaunty doesn't fully work well with ext4, there are still several problems which are ironed out in Karmic

Yes, it's fine to reformat it to ext3, although you won't be able to use it at all on any Windows computer, because 3rd party ext3 software sucks.

---

### Post by louieb on 2009-08-29
> **lakelovers said:**
>  (Memory impaired?) 

I call mine brain farts or senior moments! 

  Do you plan to ever plug the drive into a PC running Windows? If so its fine to leave it formatted with fat32.  The good thing about fat32 is it works with about any computer you plug it into. The bad thing is it doesn't journal, it fragments and it can't handle files over 3.4GB in size.
  Another option is to format it with NTFS file system. NTFS has pretty good support in Linux and has a much larger file size limit.

 And theres ext3 which would be my choice if the drive is going to be used only on computers running Linux.

---

### Post by lakelovers on 2009-08-29
I do want to use ext3, but I don't how to initiate it because ext3 does not appear anywhere I can find on gparted. How do I proceed?

---

### Post by NoaHall on 2009-08-29
Click on format or reformat , and choose ext3

---

### Post by lakelovers on 2009-08-29
My frustation continues. The "format" option under the "partition menu is grayed. It's not operational.

---

### Post by NoaHall on 2009-08-29
Is your disk mounted? You need to unmount it first. You can do this from the file browser, or from gparted ( i think)

---

### Post by jon64 on 2009-08-29
First you will need to mount it as "NoaHall" said. By doing that you can click on "Places>"your usb drive" to mount it(make sure you exit gparted or else it won't allow you to mount the drive) then you can open gparted and format your usb drive as ext3(only if you only want to use the drive for linux) or you can format it as NTFS as "louieb" said.

Cheers!:popcorn::P

---

### Post by NoaHall on 2009-08-29
I think jon64 means unmount it.

---

### Post by jon64 on 2009-08-29
Yeh sorry ha! yes please "unmount" the drive before partitioning because you can't partition the drive while mounted in gparted. Sorry for the mix up :P

oh and you can unmount it by going into gparted and right clicking on the partition bar of your usb drive to unmount. Then you can resume formating to ext3 or ntfs.

---

### Post by lakelovers on 2009-08-29
Oh man! I can't get anywhere. I mounted the external drive yesterday. Now I have unmounted it via the terminal. When I access the drive on gparted, I still get the fat32 file system. I can't mount the drive via places because I don't have permission. So, I have to mount it via the termina, I guess. I'm going in circles. I may have used a wrong comand in the terminal when I first mounted the drive. How should I do it?

---

### Post by jon64 on 2009-08-29
while in terminal can you do a sudo fdisk -l and tell me which drive is your usb drive please. EDITED: (actually i could probably figure it out since your usb drive is formated as fat32)

---

### Post by lakelovers on 2009-08-29
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15017   120624021    b  W95 FAT32

---

### Post by NoaHall on 2009-08-29
Unmount it, then go to gparted and THEN reformat -> ext3

---

### Post by jon64 on 2009-08-29
> **lakelovers said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15017   120624021    b  W95 FAT32

```
sudo umount /dev/sdb1
``` 

then go to gparted and format it as ext3

Cheers!:popcorn::P

---

### Post by lakelovers on 2009-08-29
Thank you all for your help. I finally got it. . . sorry to be such a dunderhead

---

### Post by jon64 on 2009-08-29
No worries, I'm glad we were able to help you and we all feel like that sometimes haha :P

---

### Post by lakelovers on 2009-08-30
I'm embarrassed to continue this odyssey on "How To" but I'm still stumped. I have the external drive set up for ext3, and mounted. Now, I need to add /dev/sdb2, extended partition and /dev/sdb5, linux-swap partition. I'm guessing that I have to mount these with the terminal. Or can I do this in gparted? If so, I don't see that option for adding a partition. I've tried "sudo mount /dev/sdb2, and get: "can't find /dev/sdb2 in /etc/fstab or /etc/mtab." So, obviously I have to take some action prior to the mount command. What do I do? By the way, I have search myself silly and I can't find a simple step-by-step tutorial on setting up a new external drive complete with partition. I'm going to use the drive for backups, only.

---

### Post by jon64 on 2009-08-30
Well once you get ext3 on your external drive you should be able to mount it any time you need to backup something. Any Linux distro can identify an ext3 formated drive so all you really need to do is mount the external drive and start backing up data on it. :popcorn:

---

### Post by lakelovers on 2009-08-30
That's a relief. I thought I had to partition the drive. Is there any advantage in partitioning it even though I'm using it for backup, only?

---

### Post by x33a on 2009-08-30
> **lakelovers said:**
> I've tried "sudo mount /dev/sdb2, and get: "can't find /dev/sdb2 in /etc/fstab or /etc/mtab."

you need to specify a mount point, too. create a mount point in /media
```
sudo mkdir /media/sdb2
```

then mount it with
```
sudo mount -t ext3 /dev/sdb2 /media/sdb2
```

alternatively, you can have an entry into /etc/fstab. this will enable you to automount the drive.

---

### Post by lakelovers on 2009-08-30
I used your command line and got this for which I have no clue. 

wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by x33a on 2009-08-31
isn't /dev/sdb2 formatted to ext3?

post the output of 
```
sudo fdisk -l
```

---

