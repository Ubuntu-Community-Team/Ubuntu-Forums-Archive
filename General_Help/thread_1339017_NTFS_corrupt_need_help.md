---
title: "NTFS corrupt need help"
date: 2009-11-27
forum: General Help
---

### Post by danieljcary on 2009-11-27
This is my first time posting but not my first time here.  These forums are an invaluable asset to a new Linux enthusiast such as myself.  That being said, i need help.  I was trying to cut and paste some files from my internal to an external hardrive when the power was shut off.  Now when it try to mount the external i get this:

```
daniel@daniel-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
[sudo] password for daniel: 
Failed to load runlist for $MFT/$DATA.
highest_vcn = 0xa5c7, last_vcn - 1 = 0xa5cf
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```I dont have windows available to me because im overseas away from home.  So i downloaded a vista recovery cd to try and run chkdsk  and it is not seeing the drive.  Im at a loss. any ideas?

---

### Post by zaphod777 on 2009-11-27
I have noticed that linux has a hard time dealing with ntfs that is dirty being unpluged un safley. just connecting to a windows machine will probably mount it and set to be clean. Maybe install xp in a vm and it should work.

if it is not connected by its own power and you have it connected with a usb 1.0 port you might 
if gparted can see it then the enclosure is probably fine.

try downloading hiren boot cd it has a lot of good utilities like partition magic so it might help.

if gparted can't see it then the enclosure might be bad you should be able to remove the drive and put it in a new external enclosure.

---

### Post by danieljcary on 2009-11-27
So i got chkdsk to work on the vista recovery cd using "chkdsk /f C:"  However halfway thru it got hung up.  now i get a new error when i try to mount it.

```
daniel@daniel-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory

```

then when i try to run ntfsfix i get:

```
daniel@daniel-laptop:~$ sudo ntfsfix /dev/sdb1
Mounting volume... Failed to open ntfs attribute: No such file or directory.
ntfs_mft_load(): Failed.
Failed to load $MFT: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Failed to open ntfs attribute: No such file or directory.
ntfs_mft_load(): Failed.
Failed to load $MFT: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

```

the hard-drive and enclosure are working i think since It shows up in gparted.  I think i need to fix my MFT?

---

### Post by zaphod777 on 2009-11-27
its worth a shot using partition magic from booting with a hiren boot cd

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

it should be able to fix the file system automatically for you. However you do run the risk of making it worse.

If there is really important data on the drive I highly recommend this software called Get Data Back for NTFS. It's about $70 but it has saved my *** many times even recovered data from a formated drive. The only time it hasn't worked was with hardware failure. 

it is windows only however so if there is a machine you can borrow for this I recommend you try.

there is a demo version you can try to see if you can get any data from the drive.
[http://runtime.org/data-recovery-software.htm](http://runtime.org/data-recovery-software.htm)

---

### Post by mavigozler on 2009-11-27
To check myself in terms of 'no such file/directory', I would run 

$ sudo fdisk -l /dev/sdb

I suppose you did too?

---

### Post by John Bean on 2009-11-27
If the MFT no longer exists then the NTFS volume is unusable but not necessarily toast (although it may be).

I'd use Testdisk to attempt to rebuild the MFT. Testdisk is available for most OS including Ubuntu.

---

### Post by danieljcary on 2009-11-27
here is my fdisk

```
daniel@daniel-laptop:~$ sudo fdisk -l /dev/sdb
[sudo] password for daniel: 

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000048b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS
daniel@daniel-laptop:~$ 
```I am trying to use test disk right now but its not going so hot.  when i try to list the file-system there it says "Can't open filesystem. Filesystem seems damaged." then when i try to repair the mft with testdisk i get "MFT and MFT mirror are bad. Failed to repair them."  

I have the Hiren disk and i tried hdd regenerator but that was going to take 50 days to complete.  And if you think partion magic might damage my file any further ill hold off on that.

---

### Post by John Bean on 2009-11-27
> **danieljcary said:**
> when i try to repair the mft with testdisk i get "MFT and MFT mirror are bad. Failed to repair them."
In that case it's toast as a NTFS volume. Your only option is to do a low-level data recovery of some sort. I've never lost the MFT mirror and have used both chkdsk and Tesdisk to rebuild MFTs in the past, but I suspected you probably had, since chkdsk presumably failed for the same reason that Testdisk did. That's pretty catastrophic damage to a NTFS volume, I feel your pain.

---

### Post by danieljcary on 2009-11-27
*sigh*  Times like this I could use a drink.  

So how would one go about doing a low-level recovery?  It sounds like grunt-work.

---

### Post by John Bean on 2009-11-27
> **danieljcary said:**
> So how would one go about doing a low-level recovery?  It sounds like grunt-work.
There's a lot of utilities to do this sort of thing, you've already mentioned one of them. They search the raw disk sector by sector looking for patterns that may be fragments of the same file. A bit like turning the contents of the office shredder back into documents... only harder. Fragmentation makes the job much harder.

That's the slow but automatic bit; the harder part is putting names to the recovered but anonymous files. The last time I had to do  this was many years ago and it only involved a few hundred files; I wouldn't like to have to do it again.

---

### Post by zaphod777 on 2009-11-27
> **danieljcary said:**
> *sigh*  Times like this I could use a drink.  

So how would one go about doing a low-level recovery?  It sounds like grunt-work.


Get Data Back for NTFS will do a low level search it will take a few hours though or more depending on how much data and the type.

it is worth trying the demo to see if it works. But as you said you don't have access to a windows machine.

Partition magic should do the trick but I would try and get data off first before you may possibly cause more damage.

I hear you on the drink part having actually put a HDD in the freezer to try and get it to spin up long enough to get data off it. Strange as it sounds it has worked a couple times when their was hardware failure but thats not the case here just an interesting story.

I have only used that as a last resort before 1-10 times it works the other 9 times the HDD is toasted / frozen.

---

### Post by danieljcary on 2009-11-27
I just tried partition magic on the hiren boot cd and it said the partition is bad and gave me error 110.  i searched that and found:

**#110 Partition table number of sectors is inconsistent**
The hard-disk partition table contains two inconsistent descriptions of the number of sectors on the hard disk. This error is serious if both DOS and another operating system use the hard disk. Because DOS uses one description and other operating systems may use the other, data loss is likely once the partition is almost full. To resolve this problem, see the instructions in [Resolving partition table errors]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004050716430062?Open&docid=2004050712232662&nsf=powerquest.nsf&view=6c360f88152ecfce88256e91005066ac").

the problem now is that to create another backup for this drive i need another 1.5T drive.  This may delay things.  Is this worth while to pursue?

---

### Post by John Bean on 2009-11-27
Anything is worth a try, but my experience tells me that each iteration of failed methods is in reality exacerbating the damage. For example before you ran chkdisk the ntfs-3g mounter complained about a bad MFT, afterwards it reported there was no MFT at all. There was no indication at this pint that the partition table was also damaged (but it may have been) yet now that seems to be the case. It's not getting better, it's getting worse.

I know what I would do, but I don't know how important you data is and/or whether it can be replaced. There are always recovery options even when a disk is physically damaged, but the time/effort/cost of such methods has to be balanced against the value of the lost data. Only you can judge.

---

### Post by danieljcary on 2009-11-27
Well, thank you all for the advice.  I will just reformat the drive and carry on.  Sometimes you just have to let go.  I think I heard that in a movie.

---

### Post by zaphod777 on 2009-11-27
I hear that

1TB drives are pretty cheap these days might be good to get one for a backup. But we are all guilty of getting complacent at times.

---

### Post by John Bean on 2009-11-27
> **danieljcary said:**
> Well, thank you all for the advice.  I will just reformat the drive and carry on.  Sometimes you just have to let go.  I think I heard that in a movie.

That would have been my decision too. And I wouldn't have reformatted it NTFS unless I had a need to (easily) share it with a non-Linux system. Both my large USB drives are formatted ext3 and have survived the occasional erm...  let's say "unorthodox" dismount during write operations with no harmful effects whatsoever.

---

