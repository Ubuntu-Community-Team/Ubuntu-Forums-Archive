---
title: "Problem connecting to hard drive"
date: 2011-05-19
forum: General Help
---

### Post by Uracle on 2011-05-19
Hi, my hard drive is having problems i think because it won't connect in ubuntu. It gives me this message

"Connecting to "250 GB Filesystem" failed

Error mounting: mount exited with exit code 13:
ntfs_attr_pread_i:ntfs_pread failed: input/output error
Failed to read of MFT, mft=43159 count=1 br=-1:input/output
error
Failed to mount '/dev/sda2':Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. in the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/directory, (e.g /dev/mapper/nvidia_eahaabcc1) Okease see the 'dmraid' documentation for more details

Someone please help :(

---

### Post by oldfred on 2011-05-19
Welcome to the forums.

It seems like sda2 is a NTFS partition with issues. Ubuntu will not mount a NTFS partition that has problems to prevent further damage that a chkdsk may not be able to repair.

Run chkdsk from a windows repair CD. Chkdsk does not repair everything on one pass, so you have to run until there are no errors. 

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Uracle on 2011-05-19
Having this information is really helpful. However, when I made the CD it doesn't load to the recovery screen. it just freezes at the pre loading screen. Is there some kind of alternative for linux i can use that can do the same thing?

---

### Post by benerivo on 2011-05-19
Is this ntfs drive trying to mount automatically (ie. is it listed in /etc/fstab) or just mounts when you click on the drive from within ubuntu?

---

### Post by Uracle on 2011-05-19
I click it from within ubuntu from remote filesystems

---

### Post by oldfred on 2011-05-19
This only does minor fixes. You really have to run chkdsk from a windows repairCD.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

