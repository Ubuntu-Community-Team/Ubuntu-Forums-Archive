---
title: "Unable to use windows/linux partitions while reinstallation"
date: 2012-04-05
forum: General Help
---

### Post by achu91 on 2012-04-05
i have installed Ubuntu 11.10 along side windows and it booting without any problem.i just tried to re install Ubuntu 11.10 again .to my surprise while going for manual partition in installer i could not find any of my existing partition.i cannot also boot windows as it shows error(but i don't want to use windows).
I googled and found that running the gparted partition editor will solve my problem .But its shows whole disk as unallocated .(screen shot attached).But i can see all my partitions from disk utility menu.the output of fdisk-l is mentioned below

[COLOR="Red"]suja@suja-Inspiron-1525:~$ sudo fdisk -l
[sudo] password for suja: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307335168   312578047     2621440    c  W95 FAT32 (LBA)
/dev/sda2          129024    21100543    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21100544   104986623    41943040    7  HPFS/NTFS/exFAT
/dev/sda4       104988670   312578047   103794689    f  W95 Ext'd (LBA)
/dev/sda5       104988672   236584951    65798140    7  HPFS/NTFS/exFAT
/dev/sda6       307335168   312578047     2621440   dd  Unknown
/dev/sda7       236584960   252209151     7812096   82  Linux swap / Solaris
/dev/sda8       252211200   307322879    27555840   83  Linux

Partition table entries are not in disk order
suja@suja-Inspiron-1525:~$ ^C


kindly help me to solve this issue.
[/COLOR]

---

### Post by oldfred on 2012-04-05
Windows will not boot if you have the Windows boot loader in the MBR as you have two boot flags. With MBR partitioning you can only have one boot flag on a primary partiiton. Windows uses the boot flag to know where to chainload to from the MBR. Grub does not use boot flag.

May be best to post boot info script from this. 

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

I do not see a partition overlap type issue which is often the issue. Sometimes a chkdsk from a Windows repairCD may fix issues on NTFS partitions. I have had similar issue where my XP booted, but gparted would not even show my sda drive until after I ran chkdsk.

---

### Post by achu91 on 2012-04-06
i have run boot repair,But not booting windows is not real issue/problem .When i try to reisnatll ubuntu ,it doesnt show any existing partition.When i use gparted editor it shows full disk space as un allocated.Also when i try to delete a partition in disk utility it shows error.(i have attached screen shot).more over it shows two partions with same name and same size..As per you instruction i hace run boot repair and the link is  [http://paste.ubuntu.com/916935/](http://paste.ubuntu.com/916935/).

please do help me to solve my issue and reinstall ubuntu.. i am attaching the screensot of the disk utility and error i received when i tried to delete the partition.

---

### Post by oldfred on 2012-04-06
The Boot-Repair will run the boot info script and give you a link to its output. Post that link. The boot info script should give more information on your configuration.

---

### Post by achu91 on 2012-04-06
here is the link that boot-repair gave.

 [http://paste.ubuntu.com/916935/](http://paste.ubuntu.com/916935/).

---

### Post by oldfred on 2012-04-06
From boot script:
```

/dev/sda1 overlaps with /dev/sda4 
/dev/sda1    *    307,335,168   312,578,047     5,242,880   c W95 FAT32 (LBA)
/dev/sda4         104,988,670   312,578,047   207,589,378   f W95 Extended (LBA)
/dev/sda6         307,335,168   312,578,047     5,242,880  dd Dell Media Direct
```

sda4 is the extended partition and only logical partitions starting at sda5 and up can be inside the extended partiiton. But sda1 is inside the extended and sda1 is a primary partition. 

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table.
sudo sfdisk -d /dev/sda > parts_sda.txt

It looks like sda1 and sda6 occupy the same space. Not sure if fixparts will let you delete one or the other. If possible backup whatever data you have.

---

### Post by achu91 on 2012-05-07
i could not repair using fixparts,i rather refomated and installed 12.04 .Thanks a  lot for the help and guidance.

---

