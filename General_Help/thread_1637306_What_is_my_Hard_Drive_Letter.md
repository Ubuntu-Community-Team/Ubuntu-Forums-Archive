---
title: "What is my Hard Drive Letter"
date: 2010-12-04
forum: General Help
---

### Post by Kang 1 on 2010-12-04
I can not find my hard drive letters in ubuntu. In the "computer" window it just shows it as "file system".  I want to run chkdsk on another hdd that I connected to the computer.  It shows up as 2 icons, one called "256 GB Solid-State Disc:256GB Filesystem and the other called "256 GB Solid-State Disc:System Reserved. This disc was installed in another computer as the only hdd and I had problems with the computer so I removed it and installed disc drive. I want to check this ssd here in ubuntu to see if there are any bad sectors etc. All the instructions I can find say to Type "Run chkdsk /[drive letter]" (without quotes) in the terminal win. I entered [FONT=monospace]"[/FONT]sudo lshw" and the drive shows as "*-disc:1" I tried using 1, disc-1 and *-disc:1 as drive letters , example, "Run chkdsk/1" (without quotes), and I get command not found for all 3. There must be a drive letter to these discs as in windows I would guess, it appears that way as I search the net. NOTES, this computer has ubuntu 10.04 installed only and has 3gb native sata mobo, no microsoft at all. I want to check the quality of this ssd as much as possible and can overwrite or delete any and all files on it, reformat it etc. If it checks out good, I may remove the existing hdd on the computer and install this one as the only hdd and install ubuntu and use it a while to make sure it works fine, then remove it and install it to the original computer where i wanted it in the first place. That computer has win7 ultimate on it, but what matters is that one has the 6gig native sata mobo and that is where this ssd will work at its fastest. TYVM in advance.

---

### Post by AlphaLexman on 2010-12-04
Welcome,

Here is a good guide to explain it all: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html")

But basically there are no drive letters as in windows! It can be a little confusing at first (it was for me) but in the long run the hierarchy system is better.

---

### Post by cgroza on 2010-12-04
The notation system is different on Linux. If you have a NTFS partition and you would like to know its letter, you must boot windows and check it because drive letter are assigned at boot in Windows.

---

### Post by QLee on 2010-12-04
Kang 1,

Chkdsk is a Windows program, you will not find it on a computer running Ubuntu, in order to use chkdsk (and I think you should on native Windows filesystems), you need to be booted into Windows, where the drives(partitions) will show up as the drive letters.


[Edit] If you truly want to erase everything on it, and don't do that if you need anything that is on it, you could do so with gparted in ubuntu, it can reformat it with Linux filesystem types and check it too. But make sure that is what you want to do before you start.

---

### Post by Kang 1 on 2010-12-04
I have read through what seems to apply and browsed through the rest (it would take many hours to read it all completely) the "Linux Filesystem Hierarchy" as posted above and still can not figure out how to do a chkdsk. So I formated the ssd and when completed it shows as "256 GB Solid-State Disc:New Volume. I enter "run chkdsk/New Volume", and "Run chkdsk/256 GB Solid-State Disc:New Volume", and both times I get "Run: command not found". Any suggestions as to how I can run chkdsk on this drive? TYVM

---

### Post by Kang 1 on 2010-12-04
Oh,.. I see, then is there an equivalent or similar app in ubuntu that I can use to check the integrity and quality of this ssd? I want to know if there are any bad sectors or any problems with it. TYVM

---

### Post by Irony on 2010-12-04
System > Admin > Disk Utility

Also;

```
fsck /dev/sdb1
```

where you replace sdb1 with whatever the partition actually is - note fsck must be done on an unmounted partition.

---

### Post by QLee on 2010-12-04
How did you format it and what Linux filesystem type did you choose, when you format it would take any bad blocks into account and not use them up to the limit of bad blocks and if that was passed you would receive an error message.

---

### Post by Irony on 2010-12-04
If you format a system (I use ext4) it takes into account bad blocks so that it looks like there are no bad blocks. However if the bad blocks build up over time the filesystem will become corrupt (and so will your install).

Bad blocks are okay if they are stable but if they start appearing and increasing that is bad and signifies you need a new drive.

---

### Post by Kang 1 on 2010-12-04
> **Irony said:**
> System > Admin > Disk Utility

Also;

```
fsck /dev/sdb1
```where you replace sdb1 with whatever the partition actually is - note fsck must be done on an unmounted partition.
I tried that before and again now, but it just checks it in a milisecond and the window pops open and says "File system is clean". I cant imagine that it completely inspected the integrity (checked for bad sectors or equivalent)  in a millisecond.  It takes windows around an hour to do that on a 256 gb hd. But maybe Ubuntu is much faster, lol. I really want to make the most of Linux and get into the technical aspects of it, as I am real good at those things. I don't want to do it, (it would be considered giving up, something I cant recall the last time I done) but I may install the drive in a windows machine and check it there, really don't want to though cause there must be a way to check it in Ubuntu.

---

### Post by oldfred on 2010-12-04
chkdsk can only be run from windows on NTFS formated partitions as posted above:

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

The Linux equivalent is fsck or e2fsck, but it can only be run on Linux formated partitions.

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Kang 1 on 2010-12-04
> **Irony said:**
> If you format a system (I use ext4) it takes into account bad blocks so that it looks like there are no bad blocks. However if the bad blocks build up over time the filesystem will become corrupt (and so will your install).

Bad blocks are okay if they are stable but if they start appearing and increasing that is bad and signifies you need a new drive.

ok I will format it that way if needed, but what i really need to know is if there are any bad sectors, blocks, or whatever on the drive. I need to know if I should get a rma (return material authorization) on the drive and send it back to the mfr for a replacement. I have to test the drive to find any evidence that it may be or is not defective.

---

### Post by AlphaLexman on 2010-12-04
If you have a live-CD of ubuntu 9.10 or 10.04, there is a 'Disk Utility' that will check for bad sectors without un-mounting the drives. Of course you will need to un-mount the drive to fix the errors.

---

### Post by QLee on 2010-12-04
[QUOTE=Kang 1]I tried that before and again now, but it just checks it in a milisecond and the window pops open and says "File system is clean". I cant imagine that it completely inspected the integrity (checked for bad sectors or equivalent)  in a millisecond.  It takes windows around an hour to do that on a 256 gb hd.[/QUOTE]
Well it shouldn't take long to check a freshly formatted partition, when you checked the Windows drive it had data on it, eh?


[QUOTE=Kang 1]... I really want to make the most of Linux and get into the technical aspects of it, as I am real good at those things. ...[/QUOTE]

Excellent, start your education by opening a terminal window and entering the command, man badblocks, that is the manual page for the badblocks command which is what you are seeking. especially notice the "-o"  option if you want a list.

Welcome to Ubuntu!

---

### Post by Kang 1 on 2010-12-04
TYVM to all who have helped me here. Here is what I am going to do,. I will install the ssd in a win machine and check it there because of the possibility that the mfr may not accept test results or even the installation of the drive in Linux.  This will not be a give up though as I will install a regular hdd drive that I already know has 3 or 4 errors/bad sectors that I removed from another computer because it had a virus that bitdefender and 2 antimaleware apps could not remove, and I could not manually remove, couldn't find the exe file and registry entries would come back upon reboot. I will format it as "ext4" and read this thread again and try to check it for bad blocks. I will post here again once I do that and let you all know the results. My goal is to understand how to check the quality of a hard drive, ssd or disc to determine if it is within manufacturers new spec, and or to see if it is in safe to use spec. I will do a read write benchmark before installing it too.

---

### Post by oldfred on 2010-12-04
I do not know if it works on SSDs or not. But new hard drives support smart monitor.

From synaptic:
smartmontools - lists harddrive detail info
smartctl and smartd

and:
GSmartControl is a graphical user interface for smartctl

The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks. It is derived from the smartsuite package, and includes support
for ATA/ATAPI-5 disks. It should run on any modern Linux system.

---

### Post by Irony on 2010-12-04
As I said earlier: **System > Administration > Disk Utility**

Also all the major manufacturer's have programmes you can download to test their drives - usually you burn these to CD and test the drive like a live CD.

---

