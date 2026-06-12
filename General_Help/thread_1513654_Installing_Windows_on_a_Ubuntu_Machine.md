---
title: "Installing Windows on a Ubuntu Machine"
date: 2010-06-19
forum: General Help
---

### Post by shinjlong on 2010-06-19
Ok so i have a computer that is running just unbuntu, no other OS on it. i would like to remove Ubuntu and replace it with Windows, id prefer to do this without formatting my harddrive if at all possible. if someone could help that would be great.
 
my email is [EMAIL="Gamer01982@gmail.com"]Gamer01982@gmail.com[/EMAIL] the names Jeremy. thanks
 
 
Ps. please if possible make subject of email "Ubuntu/Windows Help" so i dont accidently delete it or anything thanks.

---

### Post by Miljet on 2010-06-19
Windows uses NTFS file system - Ubuntu uses EXT4 file system and they are NOT compatible. Therefore you will have to format the hard drive, or at least that portion that has the operating system. If your hard drive is divided into multiple partitions, you only have to format the partition that has the operating system.

So, why exactly do you not want to format the drive?

---

### Post by Mark Phelps on 2010-06-20
> **shinjlong said:**
> Ok so i have a computer that is running just unbuntu, no other OS on it. i would like to remove Ubuntu and replace it with Windows, id prefer to do this without formatting my harddrive if at all possible. if someone could help that would be great.

If you're concerned about losing your current data -- that is going to be a tough problem to solve because, although you could use GParted to shrink your current partitions to make room for adding MS Window partition, the presumption is that when done, you will be able to read the Ubuntu partitions from MS Windows -- which, if installed them using Ubuntu 9.10 or 10.04, you will NOT be able to do.

That is because 9.10 and 10.04 use Ext4 filesystems by default -- which MS Windows can NOT read.

---

### Post by megamandos on 2010-06-20
An actual solution...

Get a ubuntu 10.04 live cd, then boot to it, open up gparted, shrink your ubuntu partition to as small as you can, but leave about 100MB empty space on it. Reboot and install windows, go into advanced options and install on the empty part of the drive (creating your windows partition), boot into a ubuntu live cd, copy the files you need from your old patition to your new partiton (ubuntu to windows), if you have a very full drive you may have to re-size several times, (ie, if you cant free up half the drive in the first resize). Then after you have gotten all of your files copied over, delete your ubuntu partition and use gparted to resize your windows partition to fill the entire drive. Then boot into the windows CD (if its windows vista/7) and click "repair my computer", a progress bar will appear and then it will tell you that it found some problems with your windows installation, click "repair and restart".

done.

Just a warning in advance, if you have like 75% of your hard drive full, this will probably take several hours since you will be resizing 2-3 times, but you shouldn't lost any data, unless your power goes out when resizing....

EDIT: one more thing, when booting with the ubuntu live CD, as soon as it starts reading the cd, press F2 repeatedly until a menu comes up, the select "try ubuntu" or w/e to boot it live. And if you are using RAID, you will need to use "sudo apt-get install kpartx" from terminal after it boots in order to see your RAID array in gparted.

---

