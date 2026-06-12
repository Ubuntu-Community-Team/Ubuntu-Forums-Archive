---
title: "Can you move and entire filesystem to a new harddrive?"
date: 2006-06-01
forum: General Help
---

### Post by nbx909 on 2006-06-01
I am thinking about buying a new harddrive but i want to install dapper ASAP. I am wondering if there was a way to install dapper on a smaller harddrive then later move it to a different bigger harddrive with out having to reinstall dapper? I know there has to be a way i just can't find it or think of a way since ext3 isn't supported by the stuff that ussually comes with hard drives to move them. Also   i can't add the harddrive as a slave permently because the other hd (hdb) has windows on it.

---

### Post by gatekeep on 2006-06-01
well you could dd the drives (ie dd if=/dev/hda of=/dev/hdb), but if the new drive (which is more then likely) is bigger, the filesystem won't be extended over the whole drive (ie get bigger)

---

### Post by nbx909 on 2006-06-01
yeah i was afriad of that... could i extend the file system some how?

---

### Post by gatekeep on 2006-06-01
yes, try resize2fs... i forgot about that utility myself till just now when you asked...

---

### Post by nbx909 on 2006-06-01
thank you, also will doing dd=/dev/hda/ /dev/hdb also copy grub?

---

### Post by diebels on 2006-06-01
[QUOTE=nbx909]I am thinking about buying a new harddrive but i want to install dapper ASAP. I am wondering if there was a way to install dapper on a smaller harddrive then later move it to a different bigger harddrive with out having to reinstall dapper? I know there has to be a way i just can't find it or think of a way since ext3 isn't supported by the stuff that ussually comes with hard drives to move them. Also   i can't add the harddrive as a slave permently because the other hd (hdb) has windows on it.[/QUOTE]
When you get the new drive, place it where you have the windows drive. Copy `cp` over everyting except /proc. Use -a switch to preserve dates, links, owners and stuff. Create: `mkdir /${newdrive}/proc`. ${newdrive} == windows?

Probably smart to do this stuff in single user mode `sudo init 1`

Replace the old drive with the new. Now /etc/fstab should be ok.

Grub is not ok, so you'll need to install that. Should be easy with the live cd.
[quote=gatekeep]yes, try resize2fs... i forgot about that utility myself till just now when you asked...[/quote]
Won't the partition table be setup for the smaller drive? Will resize2fs take care of that?

---

### Post by nbx909 on 2006-06-01
the new drive will be a completely new drive but i can remove the windows drive while i am moveing the stuff to the new drive.

---

### Post by nbx909 on 2006-06-01
Also i don't get how to work resize2fs can somebody post a sorta step by step instructions to the whole thing? Also could i just use gparted instead?

---

### Post by gatekeep on 2006-06-01
yea you could use gparted, that actually works around the partition table size thing i didnt think about... so you could do a dd and then use gparted to resize the partitions...

---

### Post by diebels on 2006-06-01
Haven't used gparted much, but from [here]("http://en.wikipedia.org/wiki/GParted") it looks like it could do the whole copying job. Running it from the dapper live-cd should work fine.

---

### Post by aysiu on 2006-06-01
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by RAOF on 2006-06-01
If you haven't installed yet, the "LVM" option of the text-mode-installer is **exactly** what you want.  (If a bit more complicated than the gparted option).

You'll need to "manually partition" your harddrive.  Set up two linux partitions, one about 50 MB big (and set it to be used for /boot), and a second one as large as you want marked as "use for LVM".

Then go "Setup LVM", add the one partition to a Volume Group (call the VG whatever you want, I used "storage").  Accept that setup.

Now, you'll be back at the partitioning stage, except with a "LVM drive" thing.  Make your partitions on this.  I suggest a / partition (about 5-10GB), a swap partition (500MB - 1GB), and a /home partition (everything else).

The rest of the install will go the as normal.

Now, when you want to move your linux stuff to a new harddrive, you want to:
1) Initialise the new drive with **sudo pvcreate /dev/*newharddrive***
2) Add the new drive to your VG (eg: **sudo vgextend storage /dev/*newharddrive***).
3) Add the "dm-mirror" kernel module: **sudo modprobe dm-mirror**
4) Move all the stuff of your old drive: **sudo pvmove -v /dev/*oldharddrive***
5) Remove the old harddrive from your VG (eg: **sudo vgreduce storage /dev/*oldharddrive***)

And your stuff's now on the new harddrive.

Alternatively, you could just **extend** your existing partitions onto the new harddrive - that's easier.  Just do 1) & 2) from above, then for example: **sudo lvextend storage/breezy-root --size +10G** to extend your partition by 10GB

---

### Post by nbx909 on 2006-06-01
if i dd and then move it over will grub still be intact?

---

### Post by nbx909 on 2006-06-01
RAOF, but that wouldn't move the /boot partition would it?

---

### Post by RAOF on 2006-06-01
[QUOTE=nbx909]RAOF, but that wouldn't move the /boot partition would it?[/QUOTE]
Good point.  :-| 
But if you're not going to remove the harddrive that /boot is on, it won't matter.  If you **are** going to remove the harddrive that /boot is on, you'll need to partition the new harddrive with a 50MB partition and a second partition for the LVM stuff, make a filesystem on the 50MB partition, and copy all the stuff from /boot there.  You **might** be able to **dd if=/dev/*oldboot* of = /dev/*newboot*** to copy your /boot to the new drive, but I'm not sure.  It's probably safer to just copy the files.

You'll also need to fix your fstab to point to the new /boot.

---

### Post by flar on 2006-06-01
There are many ways to do this, here is a simple way.

Let's say hard drive 1 (/dev/hda)  has dapper installed on it.  

Install hard drive 2 (/dev/hdb, your new one) in the same machine

Boot your computer with a live cd ( could be the Dapper install disk)

Go to a terminal and type fdisk /dev/hdb

Use fdisk to create your partion scheme on the new hard drive, don't forget to make a swap partition.

Mount the partitions on both hard drives, eg: 
mkdir /mnt/old_ubuntu_root
mkdir /mnt/new_ubuntu_root
mount /dev/hda1 /mnt/old_ubuntu_root
mount /dev/hdb1 /mnt/new_ubuntu_root

use the command cp -ax  to copy the contents of the old disk to the new one, one partition at a time. eg:
cp -ax /mnt/old_ubuntu_root/*  /mnt/new_ubuntu_root/ 

This will take a while, but the new hard drive will have the same contents as the old one.  Using this method, it doesn't matter how big the partitions are, provided that the data fits in it.  

After the copy completes, you will have to set up your bootloader,  
to do this type "grub" at the command prompt.
At the grub prompt type:
setup (hd1)   Note: you can press tab after typing "setup (hd" to get a list of disks and partitions

then,
root (hd1,0)

then, 
quit

Your bootloader is setup

To create the swap space, if, for example, it's on the second partions of hard disk 2, 

mkswap /dev/hdb2  

Turn off the machine.

Remove or unhook your old harddrive and reboot.  That should do it

---

### Post by blakamin on 2006-06-02
OK... just to make things more difficult...

I had XP on hda1---11 gig
I have Auditor on hda3---4gig
I have hda4 as my /home (just moved it there)---8gig
and Dapper is on hda5---4.5gig
hda6 is my swap--- just under a gig


I want to move Dapper from hda5 to hda1... anyone want to see?

```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1407    11301696    7  HPFS/NTFS
/dev/hda2            2933        3648     5751270    f  W95 Ext'd (LBA)
/dev/hda3            1408        1877     3775275   83  Linux
/dev/hda4            1878        2932     8474287+  83  Linux
/dev/hda5            2933        3521     4731111   83  Linux
/dev/hda6            3522        3648     1020096   82  Linux swap / Solaris
```


I'm pretty sure hda5 and hda6 are an extended (hda2 extend?)

---

### Post by flar on 2006-06-02
To move ubuntu from hda5 to hda1,

Reboot with a livecd, 

you would have to create a linux filesystem on hda1, to make ext3 partition you would type:

mk2fs -j /dev/hda1

The above command will destroy Windows and all data on that partition.
Then mount your partitions:

mkdir /mnt/new_ubuntu
mkdir /mnt/old_ubuntu
mount /dev/hda1 /mnt/new_ubuntu
mount /dev/hda5 /mnt/old_ubuntu


Now copy:
cp -ax /mnt/old_ubuntu/* /mnt/new_ubuntu/


Then install grub as explained in earlier post

You will also have to edit /etc/fstab on the new ubuntu partition, eg:

nano /mnt/new_ubuntu/etc/fstab

and change the settings there accordingly.

Then you should be able to reboot into ubuntu on your first partition.

---

### Post by blakamin on 2006-06-02
Cheers!!!!

Will do that tonight! 

currently it is an empty ntfs partition as I killed windows ages ago... but I was wasting the space (and didn't have the time to sort it)

Thanks again!

---

### Post by flar on 2006-06-02
I should also mention, don't erase your old installation until your new one is tested and working!!

---

### Post by blakamin on 2006-06-02
thanks... then, I was wondering, If I could delete the extended partition and resize the hda1 using gparted ... maybe making a swap file as well?? (i have the Gparted live cd)

---

