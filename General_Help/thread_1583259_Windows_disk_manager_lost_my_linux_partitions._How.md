---
title: "Windows disk manager lost my linux partitions. How do I get them back?"
date: 2010-09-27
forum: General Help
---

### Post by jgor on 2010-09-27
I dual boot Windows and Ubuntu, and I was following the advice of a forum post that said I could fix my Windows vista hibernation problems by marking the vista partition as active in windows' disk manager [http://neosmart.net/forums/showpost.php?p=11909&postcount=37]("http://neosmart.net/forums/showpost.php?p=11909&postcount=37"), I stupidly went along with this idea forgetting that as a Linux user I should never use windows' disk partitioner. Marking the vista partition as active fixed the hibernation problem but caused my Linux partitions to disappear. Is there a way to undo this very rude change to my partition table? Is it possible to get the many files I lost in my /home partition back? The file system I was using was ext4. Thank you in advance for all possible help.

---

### Post by spiky001 on 2010-09-27
have you done update-grub?

---

### Post by jgor on 2010-09-27
> **spiky001 said:**
> have you done update-grub?

How do I do update-grub? I'm afraid to turn on my computer at the moment fearing that I might make the recovery worse. Is it possible that updating grub will get the partitions back? I did use a ubuntu CD and gparted to check to see if my ubuntu partitions were really missing and they were, every one of them was gone.

---

### Post by spiky001 on 2010-09-27
so if you switch machine on dose it give you the option to boot into ubuntu? also you could recover your files from live cd

---

### Post by jgor on 2010-09-27
> **spiky001 said:**
> so if you switch machine on dose it give you the option to boot into ubuntu? also you could recover your files from live cd

When I turn on the machine I get ```
error: no such partition.
grub rescue>
```

---

### Post by spiky001 on 2010-09-27
ok boot live cd open terminal ```
sudo update-grub
```

---

### Post by jgor on 2010-09-27
> **spiky001 said:**
> ok boot live cd open terminal ```
sudo update-grub
```

When I go into gparted the linux partitions are gone, if I update-grub wouldn't that make things worse by making grub forget about the linux partitions completely?

---

### Post by spiky001 on 2010-09-27
sorry looked back thought you could see partitions, so you might be looking at data recovery

---

### Post by jgor on 2010-09-27
I found the reason to the problem here [http://support.microsoft.com/kb/228004]("http://support.microsoft.com/kb/228004") I changed the active partition to my windows "C:" drive and that made my computer un-bootable.

---

### Post by coffeecat on 2010-09-27
> **jgor said:**
> When I go into gparted the linux partitions are gone, if I update-grub wouldn't that make things worse by making grub forget about the linux partitions completely?

I believe that testdisk can recover lost partitions by editing the partition table. You can install testdisk in the live session while using a live CD or live USB. I'm sorry but I have no experience of testdisk except for using photorec (which is part of testdisk) for file recovery. But try testdisk first. You should be able to find some information from someone who knows about testdisk on the forum somewhere.

For the record, you can use Gparted to make a partition active, but I'm surprised the Vista partition wasn't already. Windows won't boot unless the partition is set as active.

---

### Post by coffeecat on 2010-09-27
> **jgor said:**
> I found the reason to the problem here [http://support.microsoft.com/kb/228004](http://support.microsoft.com/kb/228004) I changed the active partition to my windows "C:" drive and that made my computer un-bootable.

I don't believe that was your problem. That describes an intrinsic windows issue within the C: partition. What happened with you is that Vista has somehow rewritten the partition table.

---

### Post by jgor on 2010-09-27
> **coffeecat said:**
> I don't believe that was your problem. That describes an intrinsic windows issue within the C: partition. What happened with you is that Vista has somehow rewritten the partition table.

I know, it doesn't make sense! all I did was make the Windows C: partition active and then hibernated the computer.

spiky001 gave me a link that sounds too good to be true though [http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart](http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart), I might beable to get my partitions back with "sudo gpart /dev/sda -W /dev/sda" The only partition I really care about is the /home one though, if it can find that I'll be thrilled

---

### Post by spiky001 on 2010-09-27
I pm so you would get it quick hope it helps

---

### Post by jgor on 2010-09-27
Do you think it is possible to do the "sudo gpart /dev/sda -W /dev/sda" command but without the automatic writing to disk, I just want to know if it CAN find the partitions before it writes to the partition table.

---

### Post by spiky001 on 2010-09-27
just a thought could you not copy an image of the disc before doing anything that way you will always have it  [http://ubuntuforums.org/showthread.php?t=492795](http://ubuntuforums.org/showthread.php?t=492795)

---

### Post by jgor on 2010-09-27
dang, according to [http://en.wikipedia.org/wiki/Gpart]("http://en.wikipedia.org/wiki/Gpart") Gpart can't find ext4, only ext2.

---

### Post by spiky001 on 2010-09-27
maybe someone has used this can advise [http://ext4-file-recovery.data-recovery-linux.com/](http://ext4-file-recovery.data-recovery-linux.com/)

---

### Post by jgor on 2010-09-27
I can't thank you enough for the very quick help. I'm doing a "sudo gpart /dev/sda" scan right now to see if it can find my lost partitions.

---

### Post by RobstaHendricks on 2010-09-27
Just had the same problem but with a Fat32 Partition.

Try testdisk, it is in the repositories

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It's definitely part of the Parted Magic Live disk [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

The tip was given to me today by [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") so thank him, not me.

---

### Post by jgor on 2010-09-28
I tried TestDisk, it found my linux partitions but it marked them as D for Deleted. I didn't know how to go on from there.

---

### Post by jgor on 2010-09-28
when I do a quick search with TestDisk I get this output:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA                0  32 33  1274 241 55   20480000 [PQSERVICE]
 2 P HPFS - NTFS           1274 241 56 20095  33 34  302346240 [ACER]
 3 P HPFS - NTFS          20095  33 35 21474  33 24   22153625
 4 E extended LBA         21475   0  1 38913 254 63  280157535
 5 L Linux                21475   1  1 38252 254 60  269538504

```

I'm tempted to select Write but I remember that there were more than one linux partition in the extended section

---

### Post by jgor on 2010-10-02
Ok, I read [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") completely. When running TestDisk I found that TestDisk could read all my lost file systems with the Deeper Search. This made me very happy, so I went on to recover the deleted file systems by selecting "write", TestDisk quickly went back to the main menu, and I checked gparted to see what it did. No partitions at all! I tried to restart my computer like TestDisk said I should, and it wouldn't even start the BIOS. TestDisk did give me warnings and I took the risk. Perhaps my harddrive doesn't use the Intel partition table.

---

### Post by srs5694 on 2010-10-02
> **jgor said:**
> Ok, I read [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) completely. When running TestDisk I found that TestDisk could read all my lost file systems with the Deeper Search. This made me very happy, so I went on to recover the deleted file systems by selecting "write", TestDisk quickly went back to the main menu, and I checked gparted to see what it did. No partitions at all! I tried to restart my computer like TestDisk said I should, and it wouldn't even start the BIOS. TestDisk did give me warnings and I took the risk. Perhaps my harddrive doesn't use the Intel partition table.

Try unplugging the hard disk and see if the boot process gets any further. If so, plug the drive back in and see how far the BIOS gets. If it won't boot, post details, like any error messages displayed or what the last status message was. (If the BIOS just puts up a graphics image, you can disable that with the hard disk disconnected. Go into the BIOS setup utility and look for options relating to a "boot splash screen" or something similar, and set it to text mode. Then shut down, reconnect the hard disk, and try again. With any luck you'll see text messages about checking RAM, scanning for USB devices, etc.)

If the hard disk blocks the BIOS from even presenting any boot options, it could be you're running into a difficulty like the [ones described here.](http://www.rodsbooks.com/gdisk/bios.html) I have no idea if your disk uses the GUID Partition Table (GPT) that page references, but it might; and even if it doesn't, it could be you've run into some similar flakiness in the BIOS. Your best bet then is to try the disk in another computer so you can isolate and correct the problem; or to connect the disk after booting the computer. This is safe if you've got an appropriate USB adapter for your drive type, a little bit risky for directly hot-plugging SATA drives, and much riskier for directly hot-plugging PATA drives.

I recommend you post hardware details if you need more advice. If you've got another computer or can get the system to boot and detect the drive, say via a PATA-to-USB adapter, boot up [PartedMagic,](http://partedmagic.com) launch a text-mode shell (terminal), type "gdisk -l /dev/sda", and post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. The gdisk program can identify which of four different partition table types is in use, which is a necessary first step in solving the problem, if the BIOS is freaking out because of what it sees (or doesn't see) in the partition table.

---

### Post by jgor on 2010-10-04
> **srs5694 said:**
> Try unplugging the hard disk and see if the boot process gets any further. If so, plug the drive back in and see how far the BIOS gets. If it won't boot, post details, like any error messages displayed or what the last status message was. (If the BIOS just puts up a graphics image, you can disable that with the hard disk disconnected. Go into the BIOS setup utility and look for options relating to a "boot splash screen" or something similar, and set it to text mode. Then shut down, reconnect the hard disk, and try again. With any luck you'll see text messages about checking RAM, scanning for USB devices, etc.)

If the hard disk blocks the BIOS from even presenting any boot options, it could be you're running into a difficulty like the [ones described here.](http://www.rodsbooks.com/gdisk/bios.html) I have no idea if your disk uses the GUID Partition Table (GPT) that page references, but it might; and even if it doesn't, it could be you've run into some similar flakiness in the BIOS. Your best bet then is to try the disk in another computer so you can isolate and correct the problem; or to connect the disk after booting the computer. This is safe if you've got an appropriate USB adapter for your drive type, a little bit risky for directly hot-plugging SATA drives, and much riskier for directly hot-plugging PATA drives.

I recommend you post hardware details if you need more advice. If you've got another computer or can get the system to boot and detect the drive, say via a PATA-to-USB adapter, boot up [PartedMagic,](http://partedmagic.com) launch a text-mode shell (terminal), type "gdisk -l /dev/sda", and post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. The gdisk program can identify which of four different partition table types is in use, which is a necessary first step in solving the problem, if the BIOS is freaking out because of what it sees (or doesn't see) in the partition table.

I'm so sorry, I should have tried taking out the battery before despairing. It turns out the laptop never turned off at all it must have just been in a weird state where it seemed to be off but really was on.

---

### Post by jgor on 2010-10-04
Ok, very good news, TestDisk must have done something right because I can find all my lost partitions and files in xubuntu's "Open File" dialog box. The problem that remains is that when I open GParted it says my entire disk is *unallocated* (which is alarming!) and when I try update-grub I get the message "grub-probe: error: cannot find a device for /.".

---

### Post by srs5694 on 2010-10-04
TestDisk may have created an improper extended partition. See [my Web page on this topic](http://www.rodsbooks.com/missing-parts/index.html) for details. If you need more help, post the output of the "sudo fdisk -lu" command, typed in a Linux shell window. Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] blocks for legibility.

---

### Post by jgor on 2010-10-04
> **srs5694 said:**
> TestDisk may have created an improper extended partition. See [my Web page on this topic](http://www.rodsbooks.com/missing-parts/index.html) for details. If you need more help, post the output of the "sudo fdisk -lu" command, typed in a Linux shell window. Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] blocks for legibility.


ok, my "sudo fdisk -lu /dev/sda" output is:
```

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc6914cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20482047    10240000    c  W95 FAT32 (LBA)
/dev/sda2        20482048   322828287   151173120    7  HPFS/NTFS
/dev/sda3       322842240   344995864    11076812+   7  HPFS/NTFS
/dev/sda4       344995875   625153409   140078767+   f  W95 Ext'd (LBA)
/dev/sda5       344996001   423682240    39343120   83  Linux
/dev/sda6       423682308   614534443    95426068   83  Linux

```

and my "sudo parted /dev/sda print" output is:
```

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!

```

You were right!

---

### Post by jgor on 2010-10-04
I'm going to do a full backup with clonezilla before I make any further changes, I have a teacher that can help me with that. Thanks for the help so far. spiky001, coffeecat, RobstaHendricks, srs5694; you are all very helpful.

---

### Post by srs5694 on 2010-10-04
Creating a backup is always wise. Fortunately, it looks like your partitions are all there (except maybe a small one at the end -- maybe a swap partition?), and although the repair is a bit scary, it's fairly straightforward, as described on the Web page I referenced. Take your time, double-check your arithmetic, ask further questions if you're unsure of anything, and it should work fine.

---

### Post by jgor on 2010-10-06
> **srs5694 said:**
> TestDisk may have created an improper extended partition. See [my Web page on this topic](http://www.rodsbooks.com/missing-parts/index.html) for details. If you need more help, post the output of the "sudo fdisk -lu" command, typed in a Linux shell window. Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] blocks for legibility.

Thank you for that website! Manualy editing the partition table worked for me, now I can look at my partitions with gparted. Now all I think I have to do is add a swap partition and do update-grub to get the computer bootable again.

---

### Post by jgor on 2010-10-06
when I do "sudo update-grub" it says "grub-probe: error: cannot find a device for /." I don't know what to do.

---

### Post by srs5694 on 2010-10-06
I'm glad you got your partitions sorted out.

Are you trying to update GRUB from a boot to the regular installation (say, using [Super GRUB Disk](http://www.supergrubdisk.org/) to boot), or directly from an Ubuntu live CD or something similar? If the latter, update-grub is probably trying to configure itself to boot from the CD, but that's not what it should do. The easiest solution is likely to use Super GRUB Disk to boot into your regular system and then do update-grub from there. Alternatively, it is possible to mount your regular root (/) filesystem (and /boot, if it's a separate partition) and re-install GRUB, but I don't recall the exact syntax offhand.

If you're already booting to your regular system, then my only idea is that your /boot/grub/device.map file may have gotten damaged. It should look something like this:

```

(hd0)    /dev/sda

```

There should be additional entries for other disks, if you've got more than one. In some such cases, the mapping might not be the logical 0-a, 1-b, 2-c, and so on, depending on device types and BIOS settings.

---

### Post by jgor on 2010-10-06
I think the answer to my problems now is just to reinstall xubuntu and that will take care of my grub and swap problems. I have two linux partitions right now, one is for /home and the other (sda5) is for everything else. My question is when I reinstall linux can I mount sda5 as "/" without formatting all the programs I have downloaded on it? since it is the same version of xubuntu (10.04) I would find it a shame to have to re-download the 8 GB of Linux programs I currently have on that partition.

---

