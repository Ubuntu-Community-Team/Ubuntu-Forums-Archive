---
title: "GParted in UBUNTU shows entire disk as UNALLOCATED SPACE"
date: 2012-06-30
forum: General Help
---

### Post by Prescilla on 2012-06-30
Good day to everyone. I hope someone can help me with my problem.

I have a dual boot Windows and Ubuntu system.

I recently encountered an [FONT=Courier New]**hd0 out of disk**[/FONT] error and was not able to boot into Ubuntu. So I booted into Windows, after 2 to 3 times of booting and rebooting into Windows, I tried booting again into Ubuntu but still I get the [FONT=Courier New]**hd0 out of disk**[/FONT] error.

So I decided to run Ubuntu from [FONT=Courier New]**LIVEUSB**[/FONT] to try to fix my Ubuntu partition using GParted, but when I run GParted, it shows my entire disk as [FONT=Courier New]**UNALLOCATED SPACE**[/FONT]!

The strange thing is that [FONT=Courier New]**Nautilus**[/FONT] still shows and mounts my partitions. Also every time I boot into Windows , my partitions exists and I am able to read and write to them.

I have no idea what is wrong. Please help! I can't stand using Windows since most of the tools I use are in Ubuntu. I don't mind reinstalling Ubuntu. In fact I already tried reinstalling using the LIVEUSB but I wasn't able to, since GParted or the Ubuntu installer itself does not recognized my partitions and shows the entire disk as unallocated space.

When I run [FONT=Courier New]**sudo fdisk -l**[/FONT], here's the output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb30ab30a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104869887    52433920   83  Linux
/dev/sda2       104869888   105074687      102400    7  HPFS/NTFS/exFAT
/dev/sda3       105074688   156149759    25537536    7  HPFS/NTFS/exFAT
/dev/sda4       156151800   625153409   234500805    f  W95 Ext'd (LBA)
/dev/sda5       156151808   169156591     6502392   82  Linux swap / Solaris
/dev/sda6       169158656   294991871    62916608    7  HPFS/NTFS/exFAT
/dev/sda7       294993920   471037944    88022012+   7  HPFS/NTFS/exFAT
/dev/sda8       471041928   625121152    77039612+   7  HPFS/NTFS/exFAT
```In Nautilus, my partitions are recognized and mounted:
[IMG]http://img21.imageshack.us/img21/9485/nautilusl.png[/IMG]

In GParted, the whole disk is unallocated space:
[IMG]http://img600.imageshack.us/img600/5522/gpartedh.png[/IMG]

In Windows, partitions are recognized and mounted as well:
[IMG]http://img651.imageshack.us/img651/4941/disksa.png[/IMG]

---

### Post by Shadius on 2012-06-30
In my case, it was because I had overlapping partitions. However, from what I can see from your output of *fdisk*, I haven't detected any overlapping. Unless I'm missing it. You can right-click on on the drive from within GParted and selecting **Information** to see if it gives you any warnings.

---

### Post by Prescilla on 2012-06-30
> **Shadius said:**
> In my case, it was because I had overlapping partitions. However, from what I can see from your output of *fdisk*, I haven't detected any overlapping. Unless I'm missing it. You can right-click on on the drive from within GParted and selecting **Information** to see if it gives you any warnings.

Thank you for the quick response.
Here's the Information I got from GParted -> Information option:

[IMG]http://img580.imageshack.us/img580/1452/infofp.png[/IMG]

---

### Post by Shadius on 2012-06-30
> **Prescilla said:**
> Thank you for the quick response.
Here's the Information I got from GParted -> Information option:

[IMG]http://img580.imageshack.us/img580/1452/infofp.png[/IMG]

I ***think*** I figured it out. So from your output of *fdisk* it appears that *sda4* is larger than the disk itself. Thus, giving you that warning of "Can't have a partition outside the disk!" Your output indicates that your [COLOR="Red"]total sectors are 625142448[/COLOR], but your [COLOR="Red"]*sda4* partition ends at 625153409[/COLOR]. Am I clear so far? So, I believe you would have to shrink *sda4* to bring the size down to match the disk drive size.

---

### Post by Prescilla on 2012-06-30
> **Shadius said:**
> I ***think*** I figured it out. So from your output of *fdisk* it appears that *sda8* is larger than the disk itself. Thus, giving you that warning of "Can't have a partition outside the disk!" Your output indicates that your [COLOR=Red]total sectors are 625142448[/COLOR], but your [COLOR=Red]*sda8* partition ends at 625121152[/COLOR]. Am I clear so far? So, I believe you would have to shrink *sda8* to bring the size down to match the disk drive size. 

[COLOR=Red]Wait, that seems to be wrong[/COLOR]. I think I confused myself. :confused:

Isn't [COLOR=Red]625142448 [COLOR=Black]greater than[/COLOR] [/COLOR][COLOR=Red]625121152[COLOR=Black]???[/COLOR]
[/COLOR][LEFT][COLOR=Black]
I have no idea what to do...:(
[/COLOR][/LEFT]

---

### Post by Shadius on 2012-06-30
> **Prescilla said:**
> Good day to everyone. I hope someone can help me with my problem.

I have a dual boot Windows and Ubuntu system.

I recently encountered an [FONT=Courier New]**hd0 out of disk**[/FONT] error and was not able to boot into Ubuntu. So I booted into Windows, after 2 to 3 times of booting and rebooting into Windows, I tried booting again into Ubuntu but still I get the [FONT=Courier New]**hd0 out of disk**[/FONT] error.

So I decided to run Ubuntu from [FONT=Courier New]**LIVEUSB**[/FONT] to try to fix my Ubuntu partition using GParted, but when I run GParted, it shows my entire disk as [FONT=Courier New]**UNALLOCATED SPACE**[/FONT]!

The strange thing is that [FONT=Courier New]**Nautilus**[/FONT] still shows and mounts my partitions. Also every time I boot into Windows , my partitions exists and I am able to read and write to them.

I have no idea what is wrong. Please help! I can't stand using Windows since most of the tools I use are in Ubuntu. I don't mind reinstalling Ubuntu. In fact I already tried reinstalling using the LIVEUSB but I wasn't able to, since GParted or the Ubuntu installer itself does not recognized my partitions and shows the entire disk as unallocated space.

When I run [FONT=Courier New]**sudo fdisk -l**[/FONT], here's the output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb30ab30a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104869887    52433920   83  Linux
/dev/sda2       104869888   105074687      102400    7  HPFS/NTFS/exFAT
/dev/sda3       105074688   156149759    25537536    7  HPFS/NTFS/exFAT
/dev/sda4       156151800   625153409   234500805    f  W95 Ext'd (LBA)
/dev/sda5       156151808   169156591     6502392   82  Linux swap / Solaris
/dev/sda6       169158656   294991871    62916608    7  HPFS/NTFS/exFAT
/dev/sda7       294993920   471037944    88022012+   7  HPFS/NTFS/exFAT
/dev/sda8       471041928   625121152    77039612+   7  HPFS/NTFS/exFAT
```

Okay, it seems the problem is *sda4* instead. Notice that it ends at [COLOR="Red"]625153409[/COLOR], but the [COLOR="Red"]total sectors of the disk drive are 625142488[/COLOR]. So if you do that math, it's over by 10921. You will have to shrink the size of the partition to bring it back into the disk drive, so to speak. Sorry for the confusion, but I'm sure that this is the problem, this time. You might wait for a second opinion on this also. :)

---

### Post by Shadius on 2012-06-30
> **Prescilla said:**
> Isn't [COLOR=Red]625142448 [COLOR=Black]greater than[/COLOR] [/COLOR][COLOR=Red]625121152[COLOR=Black]???[/COLOR]
[/COLOR][LEFT][COLOR=Black]
I have no idea what to do...:(
[/COLOR][/LEFT]

Yes, you're right. Maybe I should delete this post to avoid confusion? Yes? Let me know, it is your thread, after all. I don't want to confuse you in trying to help you. I've edited the post to include the correct information. Again, I'm so sorry about the confusion. ](*,)

---

### Post by HermanAB on 2012-06-30
Howdy,

Gparted is not the world's best partition editor.  I would rather use fdisk.

---

### Post by houseworkshy on 2012-06-30
This is an odd one, which I'm bumping as much as anything.  If you do reinstall maybe reduce the number of partitions and use exe3 or four as the linux file system despite the fact that windows can't see it.  The not booting what used to boot does suggest that a close look at the bootloader may be in order, it may be worth posting it.  Invisible to gparted but viewable in windows is just plain weird.  
This distro may be helpful [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)
Wish I had a quick fix but don't.  Do backup that parition while you can before doing anything.
Bumping bigtime.

---

### Post by oldfred on 2012-06-30
It usually is not gparted, but Windows (or third party Windows partition tools)  and sometimes testdisk that cannot count and make extended too large.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table and copy to another device.
sudo sfdisk -d /dev/sda > parts_sda.txt

---

### Post by Shadius on 2012-06-30
> **oldfred said:**
> It usually is not gparted, but Windows (or third party Windows partition tools)  and sometimes testdisk that cannot count and make extended too large.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table and copy to another device.
sudo sfdisk -d /dev/sda > parts_sda.txt

Hey oldfred):P 

I believe it was you who helped me with my issue of GParted showing my entire disk as unallocated space. 

So I wasn't right about *sda4* being larger than the disk drive itself?

---

### Post by Prescilla on 2012-07-01
> **Shadius said:**
> Okay, it seems the problem is *sda4* instead. Notice that it ends at [COLOR=Red]625153409[/COLOR], but the [COLOR=Red]total sectors of the disk drive are 625142488[/COLOR]. So if you do that math, it's over by 10921. You will have to shrink the size of the partition to bring it back into the disk drive, so to speak. Sorry for the confusion, but I'm sure that this is the problem, this time. You might wait for a second opinion on this also. :)

Yes, I think you are right, so the question now is how do I modify the extended partition (sda4) to match the end the total sectors???

---

### Post by Prescilla on 2012-07-01
> **oldfred said:**
> It usually is not gparted, but Windows (or third party Windows partition tools)  and sometimes testdisk that cannot count and make extended too large.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table and copy to another device.
sudo sfdisk -d /dev/sda > parts_sda.txt

Here's the output of the parts.txt
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=104867840, Id=83, bootable
/dev/sda2 : start=104869888, size=   204800, Id= 7
/dev/sda3 : start=105074688, size= 51075072, Id= 7
/dev/sda4 : start=156151800, size=469001610, Id= f
/dev/sda5 : start=156151808, size= 13004784, Id=82
/dev/sda6 : start=169158656, size=125833216, Id= 7
/dev/sda7 : start=294993920, size=176044025, Id= 7
/dev/sda8 : start=471041928, size=154079225, Id= 7
```
I already copied that file to a USB disk.
What to do next? Is it safe to use fixparts?

I tried fixparts /dev/sda and type p, here's the output:
```
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 625142448 sectors (298.1 GiB)
MBR disk identifier: 0xB30AB30A
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048    104869887   primary              Y      0x83
   2             104869888    105074687   primary              Y      0x07
   3             105074688    156149759   primary              Y      0x07
   5             156151808    169156591   logical     Y               0x82
   6             169158656    294991871   logical     Y               0x07
   7             294993920    471037944   logical     Y               0x07
   8             471041928    625121152   logical     Y               0x07
```
The extended partition was not listed, but will it be fixed???

---

### Post by Shadius on 2012-07-01
> **Prescilla said:**
> Yes, I think you are right, so the question now is how do I modify the extended partition (sda4) to match the end the total sectors???

That part I'm a little unsure about, but I've used GParted to resize my partitions before. I imagine it would be the same.

---

### Post by Prescilla on 2012-07-01
> **Shadius said:**
> That part I'm a little unsure about, but I've used GParted to resize my partitions before. I imagine it would be the same.

That's where my problem lies. I have been using GParted for partitioning and since it shows my drive as unallocated space, I can't do anything.

Do you know how to use fdisk? I guess I'll have to do some research first.
Thank you again.

---

### Post by Shadius on 2012-07-01
> **Prescilla said:**
> That's where my problem lies. I have been using GParted for partitioning and since it shows my drive as unallocated space, I can't do anything.

Do you know how to use fdisk? I guess I'll have to do some research first.
Thank you again.

Unfortunately, I'm not familiar with fdisk as I am with GParted. You might want to take a look at [FixParts]("http://www.rodsbooks.com/fixparts/"). If you ever solve this, please post back here and let me know what you did to solve it, if you can.

---

### Post by Prescilla on 2012-07-01
> **Shadius said:**
> Unfortunately, I'm not familiar with fdisk as I am with GParted. You might want to take a look at [FixParts]("http://www.rodsbooks.com/fixparts/"). If you ever solve this, please post back here and let me know what you did to solve it, if you can.

Hello again. I have tried fixparts and it did solve the unallocated space issue. :D

But then again I still can't boot into Ubuntu. I still get the ```
error: hd0 out of disk. Press any key to continue...
``` :(

---

### Post by Shadius on 2012-07-01
> **Prescilla said:**
> Hello again. I have tried fixparts and it did solve the unallocated space issue. :D

But then again I still can't boot into Ubuntu. I still get the ```
error: hd0 out of disk. Press any key to continue...
``` :(

You get that error when trying to boot into Ubuntu? Have you tried using the GParted LiveCD now to see if the partitions show up properly after using FixParts?

---

### Post by oldfred on 2012-07-01
Unless you ran the command to write after starting fixparts it does not correct the error. Did you press w?

---

### Post by Prescilla on 2012-07-01
> **oldfred said:**
> Unless you ran the command to write after starting fixparts it does not correct the error. Did you press w?

Yes, I did use the **w** option to write the partition table to disk. And I knew that it was successful since I can see all my partitions in gparted.

The only problem now is the ```
error: hd0 out of disk. Press any key to continue...
```

---

### Post by oldfred on 2012-07-01
I might try repairing the grub install. Not sure if just a reinstall of the boot loader to the MBR or a full grub uninstall & reinstall is required. Lets try simple first.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If that does not work, run the Bootinfo report  and post the link that creates.

---

