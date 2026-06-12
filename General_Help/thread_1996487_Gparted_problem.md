---
title: "Gparted problem"
date: 2012-06-04
forum: General Help
---

### Post by paulemony on 2012-06-04
[IMG]https://picasaweb.google.com/111997264583664303768/GParted?authkey=Gv1sRgCMa8loH6r4n4jQE[/IMG][IMG]http://picasaweb.google.com/111997264583664303768/GParted[/IMG]

Trying to move sda5 left to use unallocated space. Screenshot is from HDD boot but am using GParted on live disk where sda8 not sda6 is locked. I unswap sda8, both keys disappear. I know I have to expand extended drive sda4 into the space first, GUI lets me move it left but when I click Apply I get progress error message & GParted gives up. I'm probably missing something simple, any suggestions please?

P.S. If can't see screenshot then rightclick, copy URL & paste into address bar (apologies for the bleeding obvious!)

---

### Post by wilee-nilee on 2012-06-04
> **paulemony said:**
> [IMG]http://picasaweb.google.com/111997264583664303768/GParted[/IMG]

Trying to move sda5 left to use unallocated space. Screenshot is from HDD boot but am using GParted on live disk where sda8 not sda6 is locked. I unswap sda8, both keys disappear. I know I have to expand extended drive sda4 into the space first, GUI lets me move it left but when I click Apply I get progress error message & GParted gives up. I'm probably missing something simple, any suggestions please?

Post the screenshot.

---

### Post by paulemony on 2012-06-04
Pls see my P.S., don't know why icon doesn't work. "Open image in new tab" even easier. 

Coltrane!

---

### Post by dino99 on 2012-06-04
if you boot on livecd (liveusb) then start gparted from the livecd, your sd* partitions should not be locked.
if the problem persist, then boot in recovery mode to perform a fsck, then open a root session and run:

shutdown -h now

and try again gparted from livecd

---

### Post by wilee-nilee on 2012-06-04
> **paulemony said:**
> Pls see my P.S., don't know why icon doesn't work. "Open image in new tab" even easier. 

Coltrane!

Yes that is John Coltrane, I see no HTTP address.

---

### Post by paulemony on 2012-06-04
Think its a browser thing, appears in chromium but not FF, anyway it's:

[https://picasaweb.google.com/111997264583664303768/GParted?authkey=Gv1sRgCMa8loH6r4n4jQE](https://picasaweb.google.com/111997264583664303768/GParted?authkey=Gv1sRgCMa8loH6r4n4jQE)

---

### Post by flemur13013 on 2012-06-04
Boot from the CD.

If your swap sda8 is still locked, rt-click->swap-off.

If others are locked, unmount them.  If it complains make sure you don't have anything (nautilus, etc) using the disk.

---

### Post by ajgreeny on 2012-06-04
Is the gparted screenshot from a live session or from your installed ubuntu OS?

You will need to use a live CD/USB to do what you want, but will still need to right click on the swap partition and choose **swapoff** to be able to do anything as a live system will find and use any swap.  If any other of the ext4 partitions are locked it could be because they are mounted, so again right click and see if you can **unmount**.

You will then need to enlarge the sda4 extended partition to the left to fill the space and then enlarge the sda5 partition.

It will probably take a long, long time, but it is absolutely imperative that you don't stop it or cancel, or allow your laptop, if that's what it is, to lose power, as that will totally mess things up royally, and it will take a lot of time and effort to restore things again.

---

### Post by paulemony on 2012-06-04
OK I tried dino99's idea but keys still show, although I thought swapoff would solve this anyway, which also answers flemur13013 suggestion. 
As explained the screenshot is from Ubuntu installation but I'm using live disk (USB flashdrive) to do the partition, i.e. sda4 then sda5 as stated by ajgreeny. However I've tracked down the error message which basically says "overlapping drives not allowed" 
 but I wouldn't know how to overlap a drive even if I could, so what does it want from me?

---

### Post by ajgreeny on 2012-06-04
> **paulemony said:**
> OK I tried dino99's idea but keys still show, although I thought swapoff would solve this anyway, which also answers flemur13013 suggestion. 
As explained the screenshot is from Ubuntu installation but I'm using live disk (USB flashdrive) to do the partition, i.e. sda4 then sda5 as stated by ajgreeny. However I've tracked down the error message which basically says "overlapping drives not allowed" 
 but I wouldn't know how to overlap a drive even if I could, so what does it want from me?
OK, so let's see the output of ```
sudo fdisk -lu
```which should help by at least showing us the overlapping partitions.

It may then be possible to use [**fixparts**]("http://www.rodsbooks.com/fixparts/") to solve the problem, but one step at a time; the **sudo fdisk -lu** output first, please.

---

### Post by dino99 on 2012-06-04
instead of using gparted you can also try partedmagic

[http://nitinpant.hubpages.com/hub/Repair-Partition-Table](http://nitinpant.hubpages.com/hub/Repair-Partition-Table)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

some hdd have hidden partition( tatooed), be sure that partition beginning/ending is not mixed with other partition.

---

### Post by paulemony on 2012-06-04
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93e4b30b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     2409749     1204843+  27  Hidden NTFS WinRE
/dev/sda2   *     2409750    81502207    39546229    7  HPFS/NTFS/exFAT
/dev/sda3        81502208   122462207    20480000    7  HPFS/NTFS/exFAT
/dev/sda4       151171711   488395928   168612109    f  W95 Ext'd (LBA)
/dev/sda5       151171713   426678271   137753279+   7  HPFS/NTFS/exFAT
/dev/sda6       447186944   488395928    20604492+  83  Linux
/dev/sda7       426680320   443260927     8290304   83  Linux
/dev/sda8       443262976   447184895     1960960   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008205e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3911039     1955488+   b  W95 FAT32

---

### Post by paulemony on 2012-06-04
BTW sda6 is Ubuntu 11.10, sda7 is swap, sda8 is Ubuntu 12.04

---

### Post by ajgreeny on 2012-06-04
> **paulemony said:**
> BTW sda6 is Ubuntu 11.10, sda7 is swap, sda8 is Ubuntu 12.04
I think you have sda7 and sda8 the wrong way round!  Is that a typo?
```
/dev/sda6       447186944   488395928    20604492+  83  Linux
/dev/sda7       426680320   443260927     8290304   [COLOR=Red]83  Linux[/COLOR]
/dev/sda8       443262976   447184895     1960960   [COLOR=Red]82  Linux swap / Solaris[/COLOR]
```

I can not see any partition overlap so far, but will keep looking.

Can you put copied output from terminal in code tags (# in toolbar) in future please; it make everything so much easier to read by formatting it properly.

---

### Post by paulemony on 2012-06-04
Apologies, take 2: sda6 is Ubuntu 12.04, sda7 is 11.10, sda8 is swap for 11.10.

Not sure what "put copied output from terminal in code tags (# in toolbar)" actually means!

---

### Post by ajgreeny on 2012-06-04
> **paulemony said:**
> Not sure what "put copied output from terminal in code tags (# in toolbar)" actually means!
All it means is that after copying the terminal output into the forum reply box you should highlight it and then click on the # in toolbar at the top of the reply box.  It means that the code is shown properly formatted on screen.

Compare your copied fdisk -lu output with that which I showed in my last post, and see the difference between this without code tags:-

/dev/sda1              63     2409749     1204843+  27  Hidden NTFS WinRE
/dev/sda2   *     2409750    81502207    39546229    7  HPFS/NTFS/exFAT
/dev/sda3        81502208   122462207    20480000    7  HPFS/NTFS/exFAT
/dev/sda4       151171711   488395928   168612109    f  W95 Ext'd (LBA)
/dev/sda5       151171713   426678271   137753279+   7  HPFS/NTFS/exFAT
/dev/sda6       447186944   488395928    20604492+  83  Linux
/dev/sda7       426680320   443260927     8290304   83  Linux
/dev/sda8       443262976   447184895     1960960   82  Linux swap / Solaris

and this with code tags:-
```
/dev/sda1              63     2409749     1204843+  27  Hidden NTFS WinRE
/dev/sda2   *     2409750    81502207    39546229    7  HPFS/NTFS/exFAT
/dev/sda3        81502208   122462207    20480000    7  HPFS/NTFS/exFAT
/dev/sda4       151171711   488395928   168612109    f  W95 Ext'd (LBA)
/dev/sda5       151171713   426678271   137753279+   7  HPFS/NTFS/exFAT
/dev/sda6       447186944   488395928    20604492+  83  Linux
/dev/sda7       426680320   443260927     8290304   83  Linux
/dev/sda8       443262976   447184895     1960960   82  Linux swap / Solaris
```See what I mean?

---

### Post by paulemony on 2012-06-04
Never knew that! But if even you "cannot see any partition overlap so far" what chance do I have?

---

### Post by oldfred on 2012-06-04
I do not see it either, but boot script often does the math and may highlight where the issue is. Post link to BootInfo report.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by paulemony on 2012-06-05
[http://paste.ubuntu.com/1024912/](http://paste.ubuntu.com/1024912/)

Could this be it?: "According to the info in the boot sector, sda5 starts at sector 63."
Sector 63 is start of sda1

---

### Post by oldfred on 2012-06-05
No that is just saying it is copied from sda1 and the NTFS boot sector (PBR) has not been fixed. All NTFS PBRs have to have the same partition info on partition start & size as the partition table.

Is this an older computer with BIOS boot limits of 137GB or is BIOS set to IDE mode when it should be LBA or large or whatever BIOS calls large block allocation. Do not use RAID.

Speaking of RAID, did you ever turn RAID on in BIOS? That can write meta data to drive and then many thing do not work as drive is seen as RAID?

If you do not have RAID you can run this, just to make sure you do not have any RAID settings:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by paulemony on 2012-06-06
This is getting complicated! Tried the terminal commands, got "command not found", not sure how to check BIOS for this information, "setup" not very forthcoming. Also tried dino99's suggestion of PartedMagic but this just seems to be another version GParted with the same result:

GParted 0.12.1 --enable-libparted-dmraid

Libparted 3.1

Move /dev/sda4 to the left and grow it from 160.80 GiB to 174.49 GiB  00:00:00    ( ERROR )
    	
calibrate /dev/sda4  00:00:00    ( SUCCESS )
    	
path: /dev/sda4
start: 151,171,711
end: 488,395,928
size: 337,224,218 (160.80 GiB)
move partition to the left and grow it from 160.80 GiB to 174.49 GiB  00:00:00    ( ERROR )
    	
old start: 151,171,711
old end: 488,395,928
old size: 337,224,218 (160.80 GiB)
requested start: 122,462,208
requested end: 488,392,703
requested size: 365,930,496 (174.49 GiB)
libparted messages    ( INFO )
    	
Unable to satisfy all constraints on the partition.
Can't have overlapping partitions.
========================================

---

### Post by oldfred on 2012-06-06
I do not see problem either.

Backup partition table and then do a write (rewrite) of the partition table. Save file to another device.

sudo sfdisk -d /dev/sda > parts.txt

You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk

This may reorder partitions and cause grub or fstab issues. If everything is UUID based it will not matter, but have liveCD available in case you have to reinstall grub or edit fstab.

---

### Post by Kr0nZ on 2012-06-06
I had this problem a couple weeks ago "No overlapping partitions allowed"

IIRC, I think the problem was I was trying to increase the size of a partition inside of the extended partition without increasing the the extended one.

Try increasing the extended (sda4) first, then you will have to shift the others left, then you should be able to increase sda6. (Thats what I did on my HTPC box)

Just make sure to swapoff and unmount all the partitions in gparted

---

### Post by paulemony on 2012-06-07
Exactly what I'm trying to do, but I'm coming to the conclusion that it simply isn't possible to expand an extended partition to the left, having spent a lot of time on trying I've lost interest. Anything that could be loaded on sda6 could just as easily be loaded on sda3 anyway, just not as tidy!

---

