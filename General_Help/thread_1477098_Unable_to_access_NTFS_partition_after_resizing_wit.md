---
title: "Unable to access NTFS partition after resizing with GParted"
date: 2010-05-08
forum: General Help
---

### Post by manolomanolo on 2010-05-08
Hi.

I was trying to resize a NTFS partition using GParted and trying to enlarge it using some unallocated space (about 400 or 500 MB unallocated space) but something went wrong and now I am unable to access the NTFS partition. The unallocated space is still there.

The error details are reported at the bottom of this mail, plus the content of fstab and mtab
Do you have any idea on what caused the error and how to recover the partition?

Thank you.

Manolo.
Ubuntu 10.04

```
manolo@manolo-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda1 :
UUID=f2821b42-2df9-461b-a040-7bbe3084bb43    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda4 :
UUID=5513-BEBE    /WIN7    vfat    utf8,umask=007,gid=46    0    1
#Entry for /dev/sda3 :
UUID=28EF5D6B27F4AAF8    /media/COMMON    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
UUID=667a70d3-6777-46ae-9269-3f90cfa4caed    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    ro,user,noauto,exec,utf8    00

#UUID=1B14-0211    /COMMON    vfat    utf8,umask=007,gid=46    0    1

```

```
manolo@manolo-laptop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda4 /WIN7 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/manolo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=manolo 0 0
```

In attachment the content of the gparted_details.htm file about the errors produced.

---

### Post by dino99 on 2010-05-08
i hope you have not resized an active partition  :p

try to use gparted or better partedmagic , see it return warnings or errors

will force a fsck on next boot:

sudo shutdown -F -r now

---

### Post by manolomanolo on 2010-05-08
> **dino99 said:**
> i hope you have not resized an active partition  :p

Thanks for your reply. I umounted the NTFS partition using GParted before trying to resize it. Was the partition consequently not "active"?

> try to use gparted or better partedmagic , see it return warnings or errors
I tried to follow your adivices but I am not sure I understant what you are asking to me. I run gparted from terminal but then I don't understand which further operation should I do in order to see warning or errors. Please let me know.
As for partedmagic it seems to be a recovery tool that I shoud use at boot, so until I run it at boot I cannot see any errors/warning, is it right?

> will force a fsck on next boot:

sudo shutdown -F -r now

Could I perform any action to recover the partition without rebooting the machine?

---

### Post by manolomanolo on 2010-05-10
this is a GParted screenshot
[IMG]http://www.ubuntu-pics.de/bild/60361/_dev_sda___gparted_002_fHa1Eg.png[/IMG]

It is curious to see that Nautilus shows that the partition is EMPTY while ls from terminal shows there's some data:

manolo@manolo-laptop:/media/COMMON$ **ls**
ls: cannot access ATTIVISMO: Input/output error
ls: cannot access AUDIO: Input/output error
ls: cannot access Documenti vari: Input/output error
ATTIVISMO  AUDIO  Documenti vari  FOTO  Video dal ciucciariello

---

### Post by dino99 on 2010-05-10
so gparted dont complaint about errors, thats good :P

but you have made something risky: windows absolutly need to use the first 1024 bytes on hdd to place its bootloader :confused:

as you can see: your first partition use ext4.

---

### Post by efflandt on 2010-05-10
It is a good idea to **NEVER** try to resize a partition on a drive you are running Linux from.  It appears that gparted moved partition sda3 down, so the unallocated space is now after sda3 instead of before it.  But something went wrong in the process, and gparted (or Linux) can no longer read the filesystem on that partition.  Maybe directories are pointing to where things were, not where they are.

Are you able to boot Win7?  If so, it would have been best to move/resize the ntfs partition with Win7's own admin tools.  See if **chkdsk /f** from Win7 can fix it.

I have never had trouble with gparted with XP ntfs partitions (unless a drive had bad sectors).  But I never ran gparted from the drive I was changing, I either used a gparted-live CD or Ubuntu on CD or USB.  When I was playing around with a Win7 laptop before I gave it to someone, I resized its Win7 partition from Win7 (to make room for Ubuntu and after removing it).  Vista and Win7 have their own tools for resizing, which should be safest for their ntfs partitions.

---

### Post by manolomanolo on 2010-05-10
That WIN7 partition is quite empty. It was just creted but never used.So, there is no WIN7 installed on it.

Is it the same running that tool with win7 installed on virtualbox?

---

### Post by garvinrick4 on 2010-05-10
As much as it is a pain it sure seems this would work out a lot better in long run with.
Windows installed first, Ubuntu second with grub in sda. and Ubuntu in an extended partition. 
With a logical as /data or something in fat32 so Windows and Linux can both use 
 that partition for convienence. Time it takes to back up and reinstall would be well worth it in long run. Personal opinion.

---

### Post by srs5694 on 2010-05-10
> **manolomanolo]It is curious to see that Nautilus shows that the partition is EMPTY  while ls from terminal shows there's some data:

manolo@manolo-laptop:/media/COMMON$ **ls**
ls: cannot access ATTIVISMO: Input/output error
ls: cannot access AUDIO: Input/output error
ls: cannot access Documenti vari: Input/output error
ATTIVISMO  AUDIO  Documenti vari  FOTO  Video dal ciucciariello[/quote]

This output does *not* indicate that there's data on the disk said:**
> PhotoRec[/url] in Linux to recover individual files -- but if you've got a lot of files to recover, you'll end up taking hours to sift through them all.

[QUOTE=dino99;9272957]but you have made something risky: windows absolutly need to use the first 1024 bytes on hdd to place its bootloader :confused:

as you can see: your first partition use ext4.

I'm not entirely sure what you mean by this, but I'm pretty sure you're wrong.

In a literal sense, the first 1024 bytes of a disk consist of the [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) and the following partition. On most x86 and x86-64 disks, the MBR consists of a boot loader and the primary partition table; but the boot loader need not be the Windows boot loader. GRUB can be installed to the MBR, for instance. The sector following the MBR may be empty or it may contain additional boot loader code. GRUB sometimes installs its "stage 1.5" starting there, for instance. I don't believe the Windows boot loader uses that space, but I'm not positive of that. None of this has anything to do with the identity of the first partition on the disk.

If by "the first 1024 bytes on hdd" you actually mean "the first 1024 bytes on *partition,*" then you may be correct, but that has nothing to do with the order of partitions on the disk.

I know that some old versions of Windows are picky about what partition they boot from, but AFAIK, modern versions of Windows (those based on NT) are willing to boot from any primary partition (1-4), located anywhere on the disk. I've got one installation of Windows 7 that boots from primary partition #3, which is located near the end of the disk.

---

### Post by Mark Phelps on 2010-05-10
Couple of things ...

First, Win7 will never install into the partition you created because it requires an NTFS file system.

Second, if you have a Win7 DVD, you should be able to boot using it, select command mode, and run chkdsk on the damaged partition.  That is likely to fix it.

---

### Post by manolomanolo on 2010-05-11
> you may be able to use PhotoRec in Linux to recover individual files -- but if you've got a lot of files to recover, you'll end up taking hours to sift through them all.
I am using PhotoRec and it looks like it is recovering a lot of files from the COMMON partition. I choose to store the output into WIN7 partition even tough it is not as big as the used space in COMMON.

Let's see what happens.

Stay tuned!:popcorn:

---

### Post by manolomanolo on 2010-05-11
Well, it happens that the system hanged after a while ad I had to brutally shut it down since it was impossible to interact with the system itself.

After restarting, the partition is still empty, ls gives the same output as before (it shows an error message and also some data) and the WIN7 partition has got 16 folders from recup_dir1 to recup_dir16. All of them contain 500 files except the last one containing 296, maybe because of the system hang.

Now I'll try unmounting the partition and making a raw backup, as suggested by srs5694.

Stay tuned!

---

### Post by manolomanolo on 2010-05-11
```
sudo umount /dev/sda3
[sudo] password for manolo: 
manolo@manolo-laptop:~$ cd /media/8ad46c48-0c17-4cde-b6b6-ba65dec84bde/
manolo@manolo-laptop:/media/8ad46c48-0c17-4cde-b6b6-ba65dec84bde$ sudo dd if=/dev/sda3 of=sda3-backup.img
116214210+0 records in
116214210+0 records out
59501675520 bytes **(60 GB)** copied, 2584.38 s, 23.0 MB/s

```

Even if nautilus shows that the sda3-backup.img is **55.4 GB**

[IMG]http://www.ubuntu-pics.de/bild/60902/sda3_backup_img_properties_002_a0It8o.png[/IMG]

---

### Post by srs5694 on 2010-05-11
The 60GB/55GB issues is because of different interpretations of what "GB" means. It seems that dd is using "GB" as "1,000,000,000 bytes" (10^9 bytes), whereas Nautilus is defining it as "1,073741,824 bytes" (2^30 bytes). More words have been spent on this discrepancy over the years than I care to imagine.

---

### Post by manolomanolo on 2010-05-16
> **dino99 said:**
> 
will force a fsck on next boot:

sudo shutdown -F -r now

The "-F" option is not present in the man page for "shutdown".
in fact, executing that command just rebooted the system without running any fsck at boot. Any other suggestion, please?

---

### Post by oldfred on 2010-05-16
If you need to run filechecks on sda3 which is NTFS you really only can do that from a windows CD. Linux will check its file types but only run some preliminary file checks on NTFS if you have installed ntfsprogs and use ntfsfix but that then sets a flag for windows to run it's chkdsk.

If you do not have a windows install disk you can get a repair (only) disk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by manolomanolo on 2010-05-16
thanks for your reply.

Can i do something with Win7 virtualized using Virtual Box or something else?

---

