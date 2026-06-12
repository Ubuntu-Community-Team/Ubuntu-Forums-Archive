---
title: "root re-partitioning"
date: 2006-04-20
forum: General Help
---

### Post by balak on 2006-04-20
hi all,

I have been using breezy happily since Oct. 05. My laptop has windows dual-boot but so I far I have followed my new year resolution of not booting up windoze.

Anyways I now realize that my root partition is full and I need to add more programs. I remember long time back when linux used to fit under 300MB, but now 2.5Gb is not enuf :(

Here is my partition table:

/dev/hda1   *           1       30473    15358108+   7  HPFS/NTFS
/dev/hda2           30474       31465      499968   83  Linux
/dev/hda3           31466      116280    42746729    f  W95 Ext'd (LBA)
/dev/hda5           31466       35534     2050744+  82  Linux swap / Solaris
/dev/hda6           35535       93663    29296984+   c  W95 FAT32 (LBA)
/dev/hda7           93665       98893     2634628+  83  Linux
/dev/hda8           98893      116280     8763426   83  Linux

hda1 has winXP (15GB partition), hda6 is where I stored most of my data (30GB partition), hda7 is / and hda8 is my /home partition.

Here is the output of df
/dev/hda7              2593168   2441684     19756 100% /
tmpfs                   318452        12    318440   1% /dev/shm
tmpfs                   318452     12588    305864   4% /lib/modules/2.6.12-10-386/volatile
/dev/hda8              8625868   3820580   4367120  47% /home
/dev/hda1             15358108   7117520   8240588  47% /media/windows
/dev/hda6             29282656  17014528  12268128  59% /media/data

I would like to create more space for / (by reducing the NTFS partition). Is there a (safe) way to do it without re-installing ubuntu? I have customized it a lot and don't want to redo everything..

Thanks!

---

### Post by aysiu on 2006-04-20
Unfortunately, even if you shrink your NTFS partition, you can't add to the beginning of partitions, only to the ends of them.

You can create a separate partition for /usr, maybe.

Have you tried just clearing out your cache of .debs downloaded? You can do this through Synaptic or manually. If I'm recalling correctly, I think for manual deletion you'd go to /var/cache/apt/archives or something like that.

---

### Post by balak on 2006-04-20
Thanks Aysiu. My .deb cache is clear - I deleted everything sometime back. 

The /usr has the most stuff - 2GB so far. So you are suggesting I free space, create another partition, mount /usr on it and copy all my files from current /usr. will it simply work?

Otherwise can I move my /home partition somewhere else and increase / ? How do I increase the partition size?

thanks!

---

### Post by PriceChild on 2006-04-20
When i wanted to remove my ntfs partition, i went into gpart on the installer cd.

I then deleted the ntfs partition, and shrunk my root as small as it would go.

I then copied my root partition backwards to the start of the drive, deleted the original root partition, then went into the LIVE cd to change grub's menu.lst

This worked ok for me... the only noticable side effect being that whenever the grub updated itself, it changed the hd(x,x) to the original settings, not realising that the partition number had changed since. I think this could be solved by reinstalling grub. This same method may be of interest.

However, what i suggest, is sipmly backing up ALL your data, and doing a full reinstall.

---

### Post by aysiu on 2006-04-20
[QUOTE=balak]
The /usr has the most stuff - 2GB so far. So you are suggesting I free space, create another partition, mount /usr on it and copy all my files from current /usr. will it simply work?[/QUOTE] Yes. If you have symlinks in there, it could be tricky.

This is what I see as the steps:

1. Shrink the NTFS partition and create a new Ext3 partition. The NTFS partition has to be defragmented, and I think that needs to be done through Windows. ```
sudo umount /dev/hda1
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
```

2. Mount the new Ext3 directory--let's just say it's /dev/hda9 ```
sudo mkdir /tmp/usr
sudo mount -t ext3 /dev/hda9 /tmp/usr
```

3. Then I would zip (or tar) your /usr directory and then untar it in /tmp/usr. That way symlinks would probably operating correctly. I'm not sure what exact command you would use for this. Of course, you could always ```
sudo cp -R /usr /tmp/usr
``` but, again, I'm not sure how that would work if you had symlinks in your /usr directory.

4. Then you would edit your /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` and add this line ```
/dev/hda9 /usr ext3 defaults 0 0
```

5. Reboot and pray.

---

### Post by Ramses de Norre on 2006-04-20
You can use the following command to copy files from /usr/ to /mnt/newusr/
```
cd /usr/ && find . -depth -print0 | cpio --null --sparse -pvd /mnt/newusr/
```
So you'll need to mount the new partition as /mnt/newusr/ and after the command has finished change /etc/fstab to mount the partition as /usr/ and delete the existing /usr/
**With this command all links will work after the copy, they wont when you use cp -R!**
EDIT:typo

---

### Post by aysiu on 2006-04-20
Thanks, Ramses. I didn't know that command, but I did know ```
sudo cp -R /usr /mnt/usr
``` wasn't going to do it.

---

### Post by balak on 2006-04-21
Thanks Aysiu and Ramses.

Actually I am having problems with gparted. It refuses to write the new partition table. When it try to resize ntfs partition and apply it says "Atleast one partition was changed on a busy devide - it may confuse the kernel - please reboot".

Rebooting doesn't help either. The partition table is same as before. 
Can I use gparted from a CD?

thanks!

---

### Post by aysiu on 2006-04-21
[QUOTE=balak]
Can I use gparted from a CD?[/QUOTE] Sure.

And if that doesn't work, I've never had any problems [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to repartition. Of course, that involves downloading an entirely new distro.

---

### Post by Irony on 2006-04-21
To resize your ntfs partition see;

[http://ubuntuforums.org/showthread.php?t=142503](http://ubuntuforums.org/showthread.php?t=142503)

Basically what you do is shrink the ntfs filesystem with ntfs tools, then shrink the ntfs partition with fdisk.

You can then copy ubuntu from one partition to another with rsync;

[http://ubuntuforums.org/showthread.php?t=129300](http://ubuntuforums.org/showthread.php?t=129300)

Basically to do this you create a folder and mount the partition to be copied and create a folder and mount the partition to be copied into and then copy from one to the other with rsync - I've done this numerous times and its worked 100% okay so far.

---

### Post by balak on 2006-04-21
Thanks Irony. I was finally able to resize ntfs using ntfsresize and fdisk itself. Somehow gparted didn't work for me.

Now it mounted /usr from a different partition and I am all set to download other programs :)

Thanks everybody!

---

