---
title: "need to recover the Ubuntu Linux partition"
date: 2012-09-17
forum: General Help
---

### Post by redsandvb1 on 2012-09-17
Using the default disk management software built into Windows Vista, I inadvertently deleted my Ubuntu Linux partition.   Now I need to recover the Ubuntu Linux partition but I don't know how.   Please help ASAP

---

### Post by jerrrys on 2012-09-17
check it out

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and welcome to the forums :)

---

### Post by iponeverything on 2012-09-17
Take your time -- all the data is there and can recovered fairly easily as long as the only thing you have done is delete the partition. 

For testing in past - I have deleted table on a disk - removed it from the machine - put it back in and used linux fdisk to create the partitions  with same starting and ending sectors and all the data was still there - I didn't do anything except create the partition.

Look at some of the linux data recovery tools like testdisk - google, do a little homework and comeback with questions before you do anything to your system.

---

### Post by redsandvb1 on 2012-09-18
> **iponeverything said:**
> Take your time -- all the data is there and can recovered fairly easily as long as the only thing you have done is delete the partition. 

For testing in past - I have deleted table on a disk - removed it from the machine - put it back in and used linux fdisk to create the partitions  with same starting and ending sectors and all the data was still there - I didn't do anything except create the partition.

Look at some of the linux data recovery tools like testdisk - google, do a little homework and comeback with questions before you do anything to your system.

Thank you, so far testdisk did not work.  I will try to used fdisk and let you know.

---

### Post by Bucky Ball on 2012-09-18
I find it hard to understand that Win deleted the partition as it doesn't know natively what EXT* partitions are. Usually just says 'Healthy' but as far as I know can't do much else. So as mentioned, if you haven't done *anything* else the data should still be there. As iponeverything suggests: Take your time. Win maybe just shifted the flags and mount points to its liking. Have you tried Boot Repair or run the Boot Info script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post that back here if you run it. Are you still getting a menu list when you boot and if so what happens when you choose Ubuntu?

---

### Post by redsandvb1 on 2012-09-18
His son here, this is the output of the bootinfo script.

```
ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,848,054,062 1,848,054,000   7 NTFS / exFAT / HPFS
/dev/sda2       1,848,055,806 1,855,868,927     7,813,122   5 Extended
/dev/sda5       1,848,055,808 1,855,868,927     7,813,120  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88BC7FFBBC7FE25C                       ntfs       
/dev/sda5        ad7e6c3a-1f82-44c8-850a-7ad43cbf784f   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

There is no menu when booting, grub gives an error and takes me to a rescue prompt.

I will go get that error.

---

### Post by Bucky Ball on 2012-09-18
This might also give some clues. 

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8Sg6lhQcggA4oQK5gt.?p=xz%3A%20%28stdin%29%3A%20Compressed%20data%20is%20corrupt&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8Sg6lhQcggA4oQK5gt.?p=xz%3A%20%28stdin%29%3A%20Compressed%20data%20is%20corrupt&fr=altavista&fr2=sfp")

Looks like this is an issue:

```
xz: (stdin): Compressed data is corrupt
```Perhaps Win has mashed the partition. I don't see it anywhere so not sure about recovery. When booted from the USB could you give the output of:

```
sudo blkid
```Also, what do you see in Gparted? Attach a screenshot if you like ...

PS: When at the grub prompt try typing 'startx'. You might also try Boot Repair which can be installed while booting from disk or USB. That should at least give a clearer indication of what's going on.

---

### Post by redsandvb1 on 2012-09-18
There is a screenshot of what gparted shows in the first post.


```
sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="88BC7FFBBC7FE25C" TYPE="ntfs" 
/dev/sda5: UUID="ad7e6c3a-1f82-44c8-850a-7ad43cbf784f" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660" 

```

I will try the startx thing now.

---

### Post by redsandvb1 on 2012-09-18
The grub error is no such partition, and startx gives "no command found"

---

### Post by Bucky Ball on 2012-09-19
Oh, right. Apologies. Windows has consumed the Linux partition, then. You have a /swap partition and that is it. The rest is Windows. I don't know of anyway you could retrieve the partition if it doesn't exist in any form or get anything from that situation; then again, Windows might not have written over it so the data *it now has inside its own partition* but who knows? The earlier error makes me think maybe Win compressed whatever was on the Ubuntu partition, saved somewhere, then wiped the partition and expanded itself. But I didn't think it was that smart! What exactly did you do to get to this, if you remember?

Nothing is or can be installed in /swap so nothing there. It is basically same as Win pagefile, if you follow. This was not a Ubuntu Wubi install per chance? Where you install Ubuntu inside Windows like any other Win program? If so, that is a totally different kettle of fish than a regular dual-boot, side by side Win/Ubuntu install. What you have in Gparted shows an extended partition (a holder for logical drives) with a /swap partition inside it which using all the free space available in the extended partition. The Ubuntu partition is no longer, the data it contained may or may not exist, where I wouldn't the foggiest.

I'm not sure where you would have had Ubuntu installed. If there was a separate partition for it the Win partition has now been expanded to wipe it out. Only grub would remain in the MBR.

Was this install on a separate partition? Was Ubuntu installed on a partition outside the extended partition or on a logical drive inside it? If the latter, that is even stranger. Good luck and hope someone else has some ideas or a solution. Least this gives the thread a bump ... ;)

PS: You might find oldfred's post #28 on this link informative but not sure any of it will work in your current situation. Might be worth a try:

[http://ubuntuforums.org/showthread.php?t=2058576&page=3](http://ubuntuforums.org/showthread.php?t=2058576&page=3)

---

