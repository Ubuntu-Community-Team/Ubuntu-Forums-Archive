---
title: "Resizing Partitions With GParted and What Will Happen With Grub"
date: 2010-05-07
forum: General Help
---

### Post by ShokTHX on 2010-05-07
I want to resize and eventually remove some partitions on my drive but I need to know how this will affect grub and what to do if I need to fix it.
I currently have 3 standard partitions and 1 extended partition on a 160Gb drive.
They are;
1st Partition -Windows XP about 60Gb with about 35Gb used. NTFS
2nd Partition -Ubuntu Lucid 10.04 amd64 about 40Gb, 22Gb used ext4
3rd Partition -Linux swap about 2.5Gb
Extented Partition -Ubuntu 9.10 about 49Gb with 23Gb used ext4 

I'd like to shrink the Extended partition down and add the space to the 2nd partion where Lucid is. Eventually, I'll want to delete the whole extended partition and add all the space to the Lucid partition.

After using GParted to resize these partitions, what will happen when I boot? Will I need to tell grub where the swap and 9.10 are? I am not changing the start of the first two partitions so I would assume there will not be any problem with them (I'm not sure how moving the start of the swap might affect the Lucid installation though).

Thanks
James

---

### Post by jbrown96 on 2010-05-07
You won't directly be able to do this. First, you need to figure out what version of grub you have. When you boot the computer press escape and shift. The grub menu will appear and the version is listed at the top. If you 1.97 or 1.98, that's the easiest. If not, then we'll probably switch you to that. You are going to need to delete your Ubuntu 9.10 partition and then recreate it. That's the only way to do this. 

1) From 10.04, mount your 9.10 parition and then back it up. I would recommend creating a tar archive using lzma compression. That might compress small enough to fit in 10.04, or you can put it on the Windows partition. 
2) delete your swap partition. Comment out the swap entry in /etc/fstab by adding a # sign to the beginning of the line.
3) Delete your swap and 9.10 partitions. Double check their partition numbers with ```
sudo fdisk -l
``` Once you are sure, then enter fdisk and delete the partitions ```
sudo fdisk /dev/sda
``` Press m to list the commands. Then d to delete and delete both partitions. Save and exit with w. 
4) Install Grub2. This is very important. ```
sudo apt-get install grub2
``` then update with ```
sudo update-grub
``` This will ensure that your system is still bootable!

 You will need to boot an Ubuntu LiveCD/USB for the next couple parts

5) Once in the live envrionment open the partition editor (gparted). Expand your 10.04 partition to the desired size. Create your 9.10 partition directly after it. Re-create your swap partition at the END of the disk. 
6) I believe that gparted will automatically increase the file system as well. Let me know if it doesn't. Reboot to 10.04
7) Uncompress and copy over the 9.10 backup that you made. Then run ```
sudo update-grub
``` to make 9.10 bootable again.

---

### Post by oldfred on 2010-05-07
A lot of what you can or cannot easily do depends on actual partition order on the drive.

```
sudo fdisk -lu
```The easiest solution of all would be to convert the extended partition to /home. That in effect adds a lot of space to your linux install and allows easy updates to new versions. If you do that you may end up wanting to move space the other way.

If any of your partitions changes changes sdax numbers you may have to reinstall grub. If you delete swap and recreated it you will have to manually edit fstab with the new UUID number.

UUIDs
```
sudo blkid
```

---

### Post by ShokTHX on 2010-05-07
I've got Grub 1.98. The partition order is how i listed it.
Sounds like delete the partitions, reinstall grub. Update grub. Redo the partitions. Update grub.
I think I may just delete the 9.10 partition instead of resizing and save some time. Have nearly everything moved to Lucid anyways.

Any reason not to update Grub to 2.0 first?
It seems like I'v done most of my partition editing in Gparted (or Partedmagic) before (it has been a while and I'm not real comfortable, which is why I posted before trying it). Any reason for using fdisk instead (maybe Gparted doesn't do this)?

James

---

### Post by oldfred on 2010-05-07
You can use gparted either from the Ubuntu liveCD or as a gparted liveCD download and made into a liveCD. Make sure you have good backups as any partition changes can cause problems.

If you want to combine space you will have to delete & recreate swap. So before you can reboot you will have to go in and edit fstab with the new UUID.

---

### Post by jbrown96 on 2010-05-07
> **ShokTHX said:**
> I've got Grub 1.98. The partition order is how i listed it.
Sounds like delete the partitions, reinstall grub. Update grub. Redo the partitions. Update grub.
I think I may just delete the 9.10 partition instead of resizing and save some time. Have nearly everything moved to Lucid anyways.

Any reason not to update Grub to 2.0 first?
It seems like I'v done most of my partition editing in Gparted (or Partedmagic) before (it has been a while and I'm not real comfortable, which is why I posted before trying it). Any reason for using fdisk instead (maybe Gparted doesn't do this)?

James

Grub is three parts. 1) a very small part of the beginning of the hard disk (mbr) points to stage 1.5. It doesn't do anything else. 1.5) Doesn't really do anything, but it is in /boot 3) That's located in your /boot, which has some basic things to get the system running and the locations of all the boot files. If your mbr points to /boot in your 9.10 install, and you delete, then your system is unbootable. 
By default, Ubuntu always installs Grub, unless you changed it. Therefore, it's probably already using /boot from 10.04, and your safe. But it's better not to take any chances.

I would also just think about not recreating swap. I've been using Linux for years on many systems, and swap just isn't used. The only time is during hibernate (different suspend/"sleep") on laptop, but that's such useless feature.

---

### Post by srs5694 on 2010-05-07
First, some terminology: Extended partitions are placeholders for logical partitions. Extended partitions don't *directly* contain filesystems, so the original description:

[quote=ShokTHX]Extented Partition -Ubuntu 9.10 about 49Gb with 23Gb used ext4[/quote]

is technically incorrect, or at least incomplete. There is indeed an extended partition, but Ubuntu 9.10 is presumably in a *logical* partition within that extended partition. This may sound like a trivial terminology nit-pick, but partition manipulations are inherently very nit-picky and precise things, so if people are sloppy about terminology, it's very easy to get led very badly astray. Note that I refer separately to extended and logical partitions in distinct operations below.

Second, IMHO jbrown96 is being overly pessimistic. ShokTHX's goal *can* be achieved fairly easily with GParted, although it will be necessary to do so from an emergency disc such as [PartedMagic,](http://partedmagic.com) [System Rescue CD,](http://www.sysresccd.org/) or an Ubuntu live CD. The reason is that GParted will not operate on a partition that's in use, but at least one of the partitions to be modified will be in use at some point during the operation were it to be attempted from a disk-based boot. (Actually, I suppose you could do part of it from 10.04 and part from 9.10, but the rebooting between operations will be awkward, particularly if you have to make last-minute adjustments that might necessitate several reboots.)

To make these changes, you'll have to start up GParted, shrink the *logical* partition (leaving empty space to its left), shrink the *extended* partition that contains it (to move free space out of the extended partition), move the swap partition to the right, and then expand the Ubuntu 10.04 partition to the right.

Third, concerning GRUB, it might or might not need adjustment; it depends on which GRUB installation is active. If the GRUB from 10.04 is active -- that is, if the GRUB in the MBR points to files in the 10.04 partition -- then chances are no changes will be required. If the 9.10 GRUB is active, though, it *might* require re-installation after the adjustment, but there's a good chance that even it would continue to work fine. Be prepared with the Ubuntu install disc or a copy of [Super GRUB Disk](http://www.supergrubdisk.org/) to facilitate booting in case you run into problems

Finally, I'll say that these sorts of changes always pose risks. If there's a power outage at an inopportune time or if a bug or undetected filesystem damage causes GParted to crash or misbehave, you could end up with a trashed filesystem. Backing up prior to resizing or moving partitions is therefore always advisable.

---

### Post by ShokTHX on 2010-05-07
Thanks everyone!
I'll be doing this sometime this weekend once I find a place to back up the more important stuff in the two home directories.
I'll make sure to post when everything goes good (or not). :)
James

---

### Post by ShokTHX on 2010-05-08
Seems to have gone just fine.
I used GParted from the Ubuntu live CD, deleted the old Ubuntu partition and extended partition it was in. I then tried simply moving the Linux swap and growing the current Lucid partition but got an error. I then tried deleting the swap first then growing the Lucid partition and adding the swap at the end which worked.
I restarted and booted right into Lucid with no problems. I am typing this from the Lucid OS so it seems to be save to say everything is going great.

Thanks again for everyone's help,
James

---

### Post by oldfred on 2010-05-08
Unless they have made an improvement changes to the swap are not normally updated in fstab. Check UUID vs fstab.

sudo blkid

compare UUID for swap vs entry in fstab

gksudo gedit /etc/fstab

---

### Post by ShokTHX on 2010-05-08
YOu're right the UUID's are different. So, I should past the new id from the blkid output to fstab and save?

> **oldfred said:**
> Unless they have made an improvement changes to the swap are not normally updated in fstab. Check UUID vs fstab.

sudo blkid

compare UUID for swap vs entry in fstab

gksudo gedit /etc/fstab

---

### Post by oldfred on 2010-05-08
yes and then run 

```
sudo mount -a
```

It will return error if there is any problem. If no problem it just returns you to terminal. It reloads fstab, and saves issues on booting if you do a typo.

---

### Post by srs5694 on 2010-05-08
You can type "free -m" at a command prompt to review your memory use, both RAM and swap. Here's what it looks like on one of my systems:

```

free -m
             total       used       free     shared    buffers     cached
Mem:          3709       3619         90          0         53       1269
-/+ buffers/cache:       2296       1413
Swap:         6143       1141       5002

```

The "Swap:" line shows swap space use. This system has 6134MB of swap space, 1141MB of which is in use. The key point for this discussion is that swap space exists -- the kernel knows about it and is using it. If the "total" column for swap space reads "0", then it means that the kernel doesn't know about your swap space, so there's likely something wrong with the /etc/fstab entry (or you've just made a change and not activated it yet). Checking this is a good idea after you change your swap configuration as oldfred suggests. Don't worry if the "used" column reads "0", especially right after you activate swap space. It'll only be used if you run more programs than you've got RAM to support or if the kernel decides it wants to dump some long-unused RAM contents to swap space in order to make room for more caches and buffers. (It can do this to improve performance even if programs' demand for memory is below the available RAM.)

---

### Post by ShokTHX on 2010-05-08
Yep, the swap is now working and showing in the free -m command.

---

