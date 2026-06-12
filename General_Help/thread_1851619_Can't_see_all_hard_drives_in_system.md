---
title: "Can't see all hard drives in system"
date: 2011-09-28
forum: General Help
---

### Post by z61P on 2011-09-28
My system has 4 HDDs: 
 
#1) bootable drive w/ ext4 fs 
#2) non-bootable w/ ext4 fs 
#3) non-bootable w/ntfs fs 
#4) non-bootable, blank/never been used 
 
When I boot, I expected ubuntu to be able to "see" all of the non-bootable drives. However, the only HDD it can "see" is #2 (and of course #1). Why? What gives - do I need to do something special to see a non-ext4 file system, or a blank HDD?? 
 
Thanks,
z

---

### Post by papibe on 2011-09-28
Could you post the results of these commands?
```
$ sudo fdisk -l

$ sudo mount -l
```
Regards.

---

### Post by seawolf167 on 2011-09-28
Have you setup the drives to mount at boot time? If not, you'll need to add entries to /etc/fstab or manually mount them each time.

Please post the output of the following commands (appending the previous poster's commands)
```
sudo fdisk -l
mount
sudo blkid
cat /etc/fstab
```

---

### Post by z61P on 2011-09-28
fdisk yields the following:
/dev/sda
/dev/sdb
/dev/sdc
 
The fourth HDD apparently has a hardware problem, and the system will not boot if it's plugged in at power up. 
 
mount lists /dev/sda1 
 
I was under the impression that any drive could be "seen" in the "Computer - File Browser" app....  Is that wrong? 
 
THanks,
z

---

### Post by oldfred on 2011-09-28
You do not mount drives per se but the partition(s) on the drive. I like to label partitions with gparted or Disk Utility so I have names I understand. Otherwise in Nautilus is just shows 250GB or whatever the size is. My XP default was a serial number that became the label from the original install so it looked very strange until I changed it.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by z61P on 2011-09-28
So, if a HDD doesn't have a partition (at all - as in a new HDD), does that mean it can't be "mounted". 
 
Sorry for the density, but I'm trying to resolve an issue that may be hardware-related. It's a long story, but you actually posted some helpful stuff in another thread I (z61P) started recently. 
 
All I really need to be able to do is "see" what (if anything) is on these HDDs. As of now, I can only "see" the one with the ext4 filesystem partition. One of the others has an NTFS partition, the remaining one has nothing on it. 
 
If you can give me a vector to accomplish that, I would appreciate it. 
 
Thanks,
z

---

### Post by seawolf167 on 2011-09-28
> **z61P said:**
> So, if a HDD doesn't have a partition (at all - as in a new HDD), does that mean it can't be "mounted". 

You'll need to partition it first - this can be accomplished through the use of GParted by typing

```
gksu gparted
```into a terminal. Once it is open, simply select your new hard drive, then partition it to the required format (either etx4 if it will *only ever* be used on linux systems, or NTFS if you ever plan to use it on a Windows system).

pysdm installation:
```
sudo apt-get install pysdm
```Once it has been formatted, you can mount it and off you go.

If you would like to have it automount upon boot, either pysdm can do that or you can manually add the appropriate entry to the /etc/fstab file (click the like "fstab" in my sig for more information or ask us!).

---

### Post by z61P on 2011-09-28
> **seawolf167 said:**
> You'll need to partition it first - this can be accomplished through the use of GParted by typing
 
```
gksu gparted
```into a terminal. Once it is open, simply select your new hard drive, then partition it to the required format (either etx4 if it will *only ever* be used on linux systems, or NTFS if you ever plan to use it on a Windows system).
 
 
OK, but if the drive already has an NTFS partition on it, then this will wipe all of that off - correct?? 
 
In my previous post, I may have explained my situation a little better... I've got two HDDs. One had nothing on it, the other hat a large NTFS partition on which our Samba users stored files. I need to be able to "see" the HDDs to confirm which HDD has the user data and NTFS partition, and which one is the "blank" HDD. 
 
Complicating this, it appears that one of these HDDs is BFU - it doesn't appear in the list of drives in the "Disk Utility" app. But then maybe an NTFS-formatted drive isn't supposed to appear?? 
 
Sorry for the massive confusion, but I need to recover the user data if at all possible, and I have no experience with some of this software.

---

### Post by oldfred on 2011-09-28
First does BIOS see drive?

If so Ubuntu often will not mount a NTFS partition that needs chkdsk to prevent further damage. Have you run chkdsk from a Windows repairCD?

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by z61P on 2011-10-01
I tried this from a Windows 7 repair disk, and with another commercial "repair cd" (Active@). There appears to be something on the drive that is inhibiting any repair operations. Here's what I see: 
 
1. during boot (on a WinXP system w/ AMI BIOS), the BIOS reports "Primary slave hard disk error". I have not seen this on my Ubuntu system, but it uses a different BIOS, and has other hardware diffs. 
 
2. using the Win7 repair disk, 
 
chkdsk reports: "type fs is NTFS, vol in use by another process" 
 
chkdsk /f (and chkdsk /r) reports: "cannot lock current drive, windows cannot run disk checking on this volume because it's write-protected" 
 
3. chkdsk /x reports that the fs is OK, but then says it "Failed to transfer logged messages to the event log with status 50"... I was expecting to see a list of all the files and folders.
 
4. using the Active@ repair disk reports essentially the same thing as the Win7 repair disk 
 
 
Any ideas??? Do you think my HDD is broken, or can I remove the "write-protect" somehow, and achieve joy? 
 
Thanks,
z

---

### Post by oldfred on 2011-10-01
I do not know chkdsk well. I did find the Win7 chkdsk found more issues with my XP install than the XP chkdsk but it then put in a Win7 boot sector.

You can try this:
[http://support.microsoft.com/kb/218461](http://support.microsoft.com/kb/218461)
> Chkdsk /X: A new command parameter that runs Chkdsk /F and forces a  volume dismount to close open file handles on non-system volumes so it  can be checked immediately. This eliminates the need of a potential  reboot in order to perform the Chkdsk and repair the volume. 


---

### Post by z61P on 2011-10-02
That's a great idea, but I've already tried that with the same result. 
 
Based on all I've seen and read, I am coming to a conclusion that there is something physically wrong with this HDD. I'm going to send it off to a data recovery outfit, and let them see what they can do with it. If I learn anything useful, I'll post it here - perhaps the info would be useful to those who develop and maintain the software. 
 
More speculatively, I think that a "power event" may be the cause of the problem I see with this HDD, and the other HDD I've requested help with due to its inability to boot successfully. I'm going to start a new thread on this problem as my approach has changed from repair of the misbehaving HDD to recovery via trasnsfer to a new HDD. 
 
more to follow...
 
z

---

