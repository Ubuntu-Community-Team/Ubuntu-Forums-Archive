---
title: "Data Recovery with ubuntu"
date: 2011-08-03
forum: General Help
---

### Post by conradin on 2011-08-03
HI everyone.
 I have a hard drive with windows vista on it.
There seems to be a persistent chkdsk /f flag some where. The disk has some bad blocks but doesnt show up as failed in the disk utility. Chkdsk /f fails in windows. testdisk says the filesystem is fine, as does the ubuntu disk utility. Gparted has been rediculously non-functional for me lately. 

the dd command fails after about 30 second throwing back some garbage about being done after 60MB copy (disk is 250GB)

ntfsfix says mounting volume is OK, processing $MFT MFTMirr completed successfully, NTFS version is 3.1, and /dev/sda1 partition processed sucesfully.

Clonezilla however won't do the clone because of the chkdsk /f flag is still set somewhere. All I want to do is get this hard drives data to an alternate healthy disk. 

How can I do this??

:confused:

---

### Post by blueridgedog on 2011-08-03
Unmount the disk then try ddrescue to copy it to an image or to another drive.

---

### Post by Jouke S on 2011-08-03
Moving the files with the mv command usually works.
sudo mv /media/further/path/ /media/path/you/want/the/files/to/go/

---

### Post by conradin on 2011-08-03
> **Jouke S said:**
> Moving the files with the mv command usually works.
sudo mv /media/further/path/ /media/path/you/want/the/files/to/go/

There is no way im going to use the mv command on files that arent backed up else where, and exist only on a failing drive. 

I'll take the advice for dd-rescue.

---

### Post by blueridgedog on 2011-08-04
This is a good example, but there are plenty out there:

[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

I use ddrescue to clone drives for system upgrades.

---

### Post by conradin on 2011-08-04
Ah thanks for the pointer to the tutorial.
What I did with a windows disk was delete the file-system then attempt a recovery. Then when that failed, I used some data-recovery software to recover a bunch of the files. I'm going in with dd-rescue now to attempt to get a mirror on a good disk and maybe get the entire thing back working soon.

---

### Post by Herman on 2011-08-04
> There seems to be a persistent chkdsk /f flag some where. The disk has  some bad blocks but doesn't show up as failed in the disk utility. Chkdsk  /f fails in windows. After you get a dd mirror image of your hard disk, try running CHKDSK /R on it instead of just /F. 
The /R stands for 'scan for and attempt recovery of data from bad sectors', and includes all the functions of /F as well. That will give you a much more effective and thorough file system check. It will take a much longer time to run than CHKDSK with just /F switch, (possibly overnight or even for a couple of days), but there's a good chance it will actually fix problems.

It's good that you have a dd copy of your damaged file system, because CHKDSK /R might move files to your recovered folder or whatever the Windows equivalent to 'lost+found' is. :D

---

### Post by conradin on 2011-08-07
Thanks Herman, I saw that in the ASR part of the boot disk. This is actually someone elses hard drive Im working on, Which they say Ive recoverd more than enough for now. I never was able to regain a fully functional OS even after doing dd-rescue, then doing chkdsk /R in the windows boot disk. Apparently from what Ive been reading is once windows sets the dirty flag its very difficult (impossible?) to remove it without running a successful chkdsk scan. Im not sure why I couldnt recover to a functional copy of the OS, but so long as all the data is functional my work here is Done.. 

:)

---

### Post by Herman on 2011-08-07
One time I was able to use GParted to shrink the partition and as the bad blocks were that time concentrated in a few cylinders where the heads crashed, the dd command was never able to get past that area on the disk. GParted was able to shrink it past the damaged area. Then I dd'ed it to a good hard disk and after a CHKDSK it booted up fine.
I think GParted and ntfsprogs are great!

I am not sure if I would be so lucky every time, it depends on what caused the bad blocks, if it's old age or excessive heat the bad blocks may be evenly distributed over a wide area so that idea might not work. It the instance I described, the head crash was caused by the user slamming the laptop lid violently after becoming infuriated and losing their temper with the operating system concerned. :D

---

### Post by blueridgedog on 2011-08-07
This thread illustrates why I backup my data...and don't use MS file systems any longer.  A couple 1T drives and a hot swap SATA drive bay and I don't have to worry.

A good "save you but" write up about ddrescue:

[http://www.linuxjournal.com/magazine/hack-and-when-disaster-strikes-hard-drive-crashes?page=0,1](http://www.linuxjournal.com/magazine/hack-and-when-disaster-strikes-hard-drive-crashes?page=0,1)

---

