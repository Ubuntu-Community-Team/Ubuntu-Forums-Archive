---
title: "files copied from ext3 to ntfs doesn't exist"
date: 2011-04-14
forum: General Help
---

### Post by mohsenof on 2011-04-14
Hello everyone
I'm using a dual boot system with kubuntu 10.10 and windows vista.
When I try to copy files from kubuntu to a windows drive, I see no problem.
But when I retsart to windows usually I can't see my files. Once or twice I have seen files I copied in kubuntu.  The strange thing is that when I go to kubuntu again, I don't see files I have copied in windows drive.
Can anyone help me?

Output of "fdisk -l ":[INDENT]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f913f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15254   122521276    7  HPFS/NTFS
/dev/sda2           15254       25036    78575612    7  HPFS/NTFS
/dev/sda3           28861       30401    12378082+   7  HPFS/NTFS
/dev/sda4           25036       28860    30720001    5  Extended
/dev/sda5           25036       25401     2929664   82  Linux swap / Solaris
/dev/sda6           25401       28860    27789312   83  Linux
[/INDENT]and conetnts of my fstab:[INDENT] # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=76255cfe-a393-453a-9ea4-6b9fca167528 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ceb5fcda-0487-4077-8217-c89e0b683d4f none            swap    sw              0       0
# NTFS partition /dev/sda1
UUID=22543B0A543ADFE9 /media/winDocuments            ntfs    defaults,user,exec,rw              0       0
[/INDENT]

---

### Post by Mark Phelps on 2011-04-14
What is likely happening is that the file write is not taking place real-time but is being buffered. When you then shutdown Ubuntu, the actual file write hasn't happened, and when you then boot into Vista, the file is not there because it was never actually written.

Have seen this myself and don't have an absolute solution -- but this problem caused me to STOP automounting Windows partitions in my FSTAB and change to mounting them on demand.  Then, when I manually unmounted the partition, part of that action forced all buffered writes to be completed.

My suggestion is to try manually unmounting the Windows partition, after one of these file writes, to see if that forces the write completion.

If that doesn't work, you may need to take the line(s) out of FSTAB and resort to manual mount/unmount actions.

---

### Post by mohsenof on 2011-04-16
Thank you Mark
It does the job, at least in most cases.
When windows loads after a hibernate, it doesn't detect files that I have copied in kubuntu, but after a restart it detects.

I don't guess manual mounting help the case, because my problem started when I was mounting windows drive manually (through Dolphin).

Why kubuntu doesn't unmount these drives automatically? It seems it can prevent lots of problems.

---

