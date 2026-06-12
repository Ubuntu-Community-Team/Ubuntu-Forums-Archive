---
title: "udevd and udevd-work preventing boot of Ubuntu 10.04.3 LTS"
date: 2011-10-29
forum: General Help
---

### Post by northd_tech on 2011-10-29
I've been attempting to get an old external USB Backpack CDRW drive working under 64-bit Ubuntu 10.04.3 LTS. This drive needs firmware loaded using **fxload**. That saga is documented on this Ubuntuforums thread:

**Micro Solutions Backpack USB External CDRW module/driver build**
[http://ubuntuforums.org/showthread.php?t=1864695&page=2](http://ubuntuforums.org/showthread.php?t=1864695&page=2)

Apparently, **usbfs** was removed from the Ubuntu kernels sometime around/after Ubuntu 9.10, and my external USB appears to need **usbfs** support to work under Linux.

I tried to get that working using this code found in post #15 on that thread:

> usbfs is no longer supported by the kernel (not since ~2.6.31-17 IIRC)   so quite a few older printers cause problems. There is a workaround, not   terribly satisfactory, but usually does the job. The following   commands:
     
     ```
sudo mount --bind /dev/bus /proc/bus
 sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices 
```before printing should do the necessary. After printing it's probably advisable to reverse the above with:
     
     ```
sudo umount   /proc/bus 
```as you may well break something else.I entered that code (actually the first 2 lines ONLY and I have been unable to get in to Ubuntu to enter the 3rd "undo" line since) and nothing seemed to happen or change with the Backpack external USB CDRW drive.  

Under 64-bit VMware, I setup a WindowsXP 32-bit virtual machine, and got the Win9X/NT/XP Backpack drivers to run/install on the 'virtual' WinXP, and eventually I got the external Backpack drive to read and spin up.  After shutting down the VMware window, I got some strange behavior out of Ubuntu like it was partially recognizing the Backpack external CDRW drive (now that the 'virtual' WinXP drivers had uploaded the firmware into the external CDRW drive).

After I shut down Ubuntu later that night, I have been unable to boot into any of my Ubuntu kernels (Grub2 acts normally and allows me to boot my Vista partition, but I need to use a rescue USB stick or rescue CD/DVD or my Ubuntu Live DVD in order to boot my Ubuntu partition on **/dev/sda5**. )

Luckily, I had installed **bootchart** so I am able to look at some before/after snapshots of the system.  The Oct 26 should be a 'normal' configuration, while the Oct. 28 is a 'broken' setup:

Oct. 26th "working":
[http://imageshack.us/photo/my-images/259/hpdv9820lucid201110261.png/](http://imageshack.us/photo/my-images/259/hpdv9820lucid201110261.png/)
[[IMG]http://img259.imageshack.us/img259/6981/hpdv9820lucid201110261.th.png[/IMG]]("http://imageshack.us/photo/my-images/259/hpdv9820lucid201110261.png/")

Oct 28th "broken":
[http://imageshack.us/photo/my-images/98/hpdv9820lucid201110281.png/](http://imageshack.us/photo/my-images/98/hpdv9820lucid201110281.png/)
[[IMG]http://img98.imageshack.us/img98/7956/hpdv9820lucid201110281.th.png[/IMG]]("http://imageshack.us/photo/my-images/98/hpdv9820lucid201110281.png/")

From that last image, it appears to me that my Ubuntu boot process is 'freezing' in the **udevd** section (and there were several error messages about **/sbin/modprobe** ).  When my system hangs, even **Ctrl-Alt-Del** is disabled, and there are error messages about that, but I did not write those down.

Looking through **/var/log/** (using Disk Internals Linux Reader), I found this output for **/var/log/syslog.1**:

> Oct 27 00:18:27 HP-DV9820 kernel: [25498.530242] usb-storage: device scan complete
Oct 27 00:18:27 HP-DV9820 kernel: [25498.539954] scsi 10:0:0:0: Direct-Access     SAMSUNG  HD103SI               PQ: 0 ANSI: 2
Oct 27 00:18:27 HP-DV9820 kernel: [25498.540761] sd 10:0:0:0: Attached scsi generic sg2 type 0
Oct 27 00:18:27 HP-DV9820 kernel: [25498.543076] sd 10:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct 27 00:18:27 HP-DV9820 kernel: [25498.547982] sd 10:0:0:0: [sdc] Write Protect is off
Oct 27 00:18:27 HP-DV9820 kernel: [25498.547988] sd 10:0:0:0: [sdc] Mode Sense: 38 00 00 00
Oct 27 00:18:27 HP-DV9820 kernel: [25498.547992] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Oct 27 00:18:27 HP-DV9820 kernel: [25498.552941] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Oct 27 00:18:27 HP-DV9820 kernel: [25498.552949]  sdc: sdc1 sdc2 sdc3 sdc4 < sdc5 sdc6 sdc7 sdc8 sdc9 >
Oct 27 00:18:27 HP-DV9820 kernel: [25498.663936] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Oct 27 00:18:27 HP-DV9820 kernel: [25498.663943] sd 10:0:0:0: [sdc] Attached SCSI disk
Oct 27 00:18:28 HP-DV9820 usbmount[23270]: /dev/sdc does not contain a filesystem or disklabel
Oct 27 00:18:30 HP-DV9820 kernel: [25501.280060] usb 1-2: reset high speed USB device using ehci_hcd and address 13
Oct 27 00:18:30 HP-DV9820 kernel: [25501.590645] usb 1-2: reset high speed USB device using ehci_hcd and address 13
Oct 27 00:18:31 HP-DV9820 kernel: [25501.930089] usb 1-2: reset high speed USB device using ehci_hcd and address 13
Oct 27 00:18:31 HP-DV9820 kernel: [25502.220050] usb 1-2: reset high speed USB device using ehci_hcd and address 13
Oct 27 00:18:34 HP-DV9820 udevd-work[23263]: inotify_add_watch(6, /dev/sdc4, 10) failed: No such file or directory
Oct 27 00:18:34 HP-DV9820 udevd-work[23298]: inotify_add_watch(6, /dev/sdc6, 10) failed: No such file or directory
Oct 27 00:18:44 HP-DV9820 udevd-work[23299]: inotify_add_watch(6, /dev/sdc7, 10) failed: No such file or directory
Oct 27 00:18:44 HP-DV9820 udevd-work[23262]: inotify_add_watch(6, /dev/sdc3, 10) failed: No such file or directoryThere were a few other instances of "udevd-work" in that logfile, but they all appear to be linked to the **usbmount** process (and/or devices).

I also found this output related to "udevd-work" in /var/log/daemon.log (which is probably for the older 'working' configuration on Oct. 26th):

> Oct 26 17:19:32 HP-DV9820 ntpd[1540]: kernel time sync status change 2001
Oct 26 17:20:40 HP-DV9820 AptDaemon: INFO: Quiting due to inactivity
Oct 26 17:20:40 HP-DV9820 AptDaemon: INFO: Shutdown was requested
Oct 26 17:31:13 HP-DV9820 ntpd[1540]: synchronized to 91.189.94.4, stratum 2
Oct 26 20:21:08 HP-DV9820 udevd-work[31132]: inotify_add_watch(6, /dev/sdb2, 10) failed: No such file or directory
Oct 26 20:21:08 HP-DV9820 udevd-work[563]: inotify_add_watch(6, /dev/sdb3, 10) failed: No such file or directory
Oct 26 20:21:25 HP-DV9820 ntfs-3g[1048]: Version 2010.3.6 external FUSE 28
Oct 26 20:21:25 HP-DV9820 ntfs-3g[1048]: Mounted /dev/sdb2 (Read-Write, label "4_Media", NTFS 3.1)
Oct 26 20:21:25 HP-DV9820 ntfs-3g[1048]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 26 20:21:25 HP-DV9820 ntfs-3g[1048]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb2,blkdev,blksize=4096,default_permissions
Oct 26 20:21:25 HP-DV9820 ntfs-3g[1048]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:22:06 HP-DV9820 ntfs-3g[1048]: Unmounting /dev/sdb2 (4_Media)
Oct 26 20:22:22 HP-DV9820 ntfs-3g[1711]: Version 2010.3.6 external FUSE 28
Oct 26 20:22:22 HP-DV9820 ntfs-3g[1711]: Mounted /dev/sdb5 (Read-Write, label "SergioL505_RecoveryD", NTFS 3.1)
Oct 26 20:22:22 HP-DV9820 ntfs-3g[1711]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 26 20:22:22 HP-DV9820 ntfs-3g[1711]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096,default_permissions
Oct 26 20:22:22 HP-DV9820 ntfs-3g[1711]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:22:44 HP-DV9820 ntfs-3g[1920]: Version 2010.3.6 external FUSE 28
Oct 26 20:22:44 HP-DV9820 ntfs-3g[1920]: Mounted /dev/sdb1 (Read-Write, label "Bakup_NTFS1", NTFS 3.1)
Oct 26 20:22:44 HP-DV9820 ntfs-3g[1920]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 26 20:22:44 HP-DV9820 ntfs-3g[1920]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Oct 26 20:22:44 HP-DV9820 ntfs-3g[1920]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:57 HP-DV9820 ntfs-3g[2564]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:57 HP-DV9820 ntfs-3g[2564]: Mounted /dev/sdb2 (Read-Write, label "4_Media", NTFS 3.1)
Oct 26 20:24:57 HP-DV9820 ntfs-3g[2564]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:57 HP-DV9820 ntfs-3g[2564]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb2,blkdev,blksize=4096,default_permissions
Oct 26 20:24:57 HP-DV9820 ntfs-3g[2564]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2579]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2579]: Mounted /dev/sdb3 (Read-Write, label "9G_storage", NTFS 3.1)
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2579]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2579]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb3,blkdev,blksize=4096,default_permissions
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2579]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2592]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2592]: Mounted /dev/sdb7 (Read-Write, label "Recover2", NTFS 3.1)
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2592]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2592]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb7,blkdev,blksize=4096,default_permissions
Oct 26 20:24:58 HP-DV9820 ntfs-3g[2592]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2597]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2597]: Mounted /dev/sdb8 (Read-Write, label "DualRecovery", NTFS 3.1)
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2597]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2597]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb8,blkdev,blksize=4096,default_permissions
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2597]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2602]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2602]: Mounted /dev/sdb9 (Read-Write, label "Spare172G", NTFS 3.1)
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2602]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2602]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb9,blkdev,blksize=4096,default_permissions
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2602]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2611]: Version 2010.3.6 external FUSE 28
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2611]: Mounted /dev/sda2 (Read-Write, label "HP_RECOVERY", NTFS 3.1)
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2611]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2611]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096,default_permissions
Oct 26 20:24:59 HP-DV9820 ntfs-3g[2611]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:25:24 HP-DV9820 ntfs-3g[1920]: Unmounting /dev/sdb1 (Bakup_NTFS1)
Oct 26 20:25:25 HP-DV9820 ntfs-3g[2699]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:25 HP-DV9820 ntfs-3g[2699]: Mounted /dev/sdb1 (Read-Write, label "Bakup_NTFS1", NTFS 3.1)
Oct 26 20:25:25 HP-DV9820 ntfs-3g[2699]: Cmdline options: rw,nosuid,nodev,locale=en_US.utf8
Oct 26 20:25:25 HP-DV9820 ntfs-3g[2699]: Mount options: rw,nosuid,nodev,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Oct 26 20:25:25 HP-DV9820 ntfs-3g[2699]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2564]: Unmounting /dev/sdb2 (4_Media)
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2714]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2714]: Mounted /dev/sdb2 (Read-Write, label "4_Media", NTFS 3.1)
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2714]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2714]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb2,blkdev,blksize=4096
Oct 26 20:25:27 HP-DV9820 ntfs-3g[2714]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2579]: Unmounting /dev/sdb3 (9G_storage)
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2728]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2728]: Mounted /dev/sdb3 (Read-Write, label "9G_storage", NTFS 3.1)
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2728]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2728]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb3,blkdev,blksize=4096
Oct 26 20:25:29 HP-DV9820 ntfs-3g[2728]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:34 HP-DV9820 ntfs-3g[1711]: Unmounting /dev/sdb5 (SergioL505_RecoveryD)
Oct 26 20:25:34 HP-DV9820 ntfs-3g[2790]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:34 HP-DV9820 ntfs-3g[2790]: Mounted /dev/sdb5 (Read-Write, label "SergioL505_RecoveryD", NTFS 3.1)
Oct 26 20:25:34 HP-DV9820 ntfs-3g[2790]: Cmdline options: rw,nosuid,nodev,locale=en_US.utf8
Oct 26 20:25:34 HP-DV9820 ntfs-3g[2790]: Mount options: rw,nosuid,nodev,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096
Oct 26 20:25:34 HP-DV9820 ntfs-3g[2790]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2592]: Unmounting /dev/sdb7 (Recover2)
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2807]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2807]: Mounted /dev/sdb7 (Read-Write, label "Recover2", NTFS 3.1)
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2807]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2807]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb7,blkdev,blksize=4096
Oct 26 20:25:35 HP-DV9820 ntfs-3g[2807]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2597]: Unmounting /dev/sdb8 (DualRecovery)
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2821]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2821]: Mounted /dev/sdb8 (Read-Write, label "DualRecovery", NTFS 3.1)
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2821]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2821]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb8,blkdev,blksize=4096
Oct 26 20:25:36 HP-DV9820 ntfs-3g[2821]: Ownership and permissions disabled, configuration type 1
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2602]: Unmounting /dev/sdb9 (Spare172G)
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2835]: Version 2010.3.6 external FUSE 28
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2835]: Mounted /dev/sdb9 (Read-Write, label "Spare172G", NTFS 3.1)
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2835]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2835]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb9,blkdev,blksize=4096
Oct 26 20:25:38 HP-DV9820 ntfs-3g[2835]: Ownership and permissions disabled, configuration type 1
Oct 26 20:26:42 HP-DV9820 ntfs-3g[2714]: Unmounting /dev/sdb2 (4_Media)
Oct 26 20:26:42 HP-DV9820 ntfs-3g[2728]: Unmounting /dev/sdb3 (9G_storage)
Oct 26 20:26:42 HP-DV9820 ntfs-3g[2699]: Unmounting /dev/sdb1 (Bakup_NTFS1)
Oct 26 20:27:48 HP-DV9820 ntfs-3g[2821]: Unmounting /dev/sdb8 (DualRecovery)
Oct 26 20:27:48 HP-DV9820 ntfs-3g[2807]: Unmounting /dev/sdb7 (Recover2)
Oct 26 20:27:48 HP-DV9820 ntfs-3g[2790]: Unmounting /dev/sdb5 (SergioL505_RecoveryD)
Oct 26 20:27:48 HP-DV9820 ntfs-3g[2835]: Unmounting /dev/sdb9 (Spare172G)
Oct 26 20:27:48 HP-DV9820 ntfs-3g[1037]: Unmounting /dev/sda1 (Vista64_JonHP)
Oct 26 20:27:49 HP-DV9820 ntfs-3g[3418]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:49 HP-DV9820 ntfs-3g[3418]: Mounted /dev/sdb2 (Read-Write, label "4_Media", NTFS 3.1)
Oct 26 20:27:49 HP-DV9820 ntfs-3g[3418]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:49 HP-DV9820 ntfs-3g[3418]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb2,blkdev,blksize=4096,default_permissions
Oct 26 20:27:49 HP-DV9820 ntfs-3g[3418]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3435]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3435]: Mounted /dev/sdb3 (Read-Write, label "9G_storage", NTFS 3.1)
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3435]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3435]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb3,blkdev,blksize=4096,default_permissions
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3435]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3442]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3442]: Mounted /dev/sdb1 (Read-Write, label "Bakup_NTFS1", NTFS 3.1)
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3442]: Cmdline options: rw,nosuid,nodev,nls=utf8,umask=0222
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3442]: Mount options: rw,nosuid,nodev,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Oct 26 20:27:50 HP-DV9820 ntfs-3g[3442]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Mounted /dev/sda4 (Read-Write, label "CommonSpace1", NTFS 3.1)
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda4,blkdev,blksize=4096,default_permissions
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3449]: Unmounting /dev/sda4 (CommonSpace1)
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3460]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3460]: Mounted /dev/sdb8 (Read-Write, label "DualRecovery", NTFS 3.1)
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3460]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3460]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb8,blkdev,blksize=4096,default_permissions
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3460]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3465]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3465]: Mounted /dev/sdb7 (Read-Write, label "Recover2", NTFS 3.1)
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3465]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3465]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb7,blkdev,blksize=4096,default_permissions
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3465]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3470]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3470]: Mounted /dev/sdb5 (Read-Write, label "SergioL505_RecoveryD", NTFS 3.1)
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3470]: Cmdline options: rw,nosuid,nodev,nls=utf8,umask=0222
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3470]: Mount options: rw,nosuid,nodev,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096,default_permissions
Oct 26 20:27:51 HP-DV9820 ntfs-3g[3470]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3475]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3475]: Mounted /dev/sdb9 (Read-Write, label "Spare172G", NTFS 3.1)
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3475]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3475]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sdb9,blkdev,blksize=4096,default_permissions
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3475]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3480]: Version 2010.3.6 external FUSE 28
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3480]: Mounted /dev/sda1 (Read-Write, label "Vista64_JonHP", NTFS 3.1)
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3480]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3480]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096,default_permissions
Oct 26 20:27:52 HP-DV9820 ntfs-3g[3480]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:27:56 HP-DV9820 ntfs-3g[3418]: Unmounting /dev/sdb2 (4_Media)
Oct 26 20:27:56 HP-DV9820 ntfs-3g[3435]: Unmounting /dev/sdb3 (9G_storage)
Oct 26 20:27:57 HP-DV9820 ntfs-3g[3442]: Unmounting /dev/sdb1 (Bakup_NTFS1)
Oct 26 20:27:57 HP-DV9820 ntfs-3g[3460]: Unmounting /dev/sdb8 (DualRecovery)
Oct 26 20:27:57 HP-DV9820 ntfs-3g[2611]: Unmounting /dev/sda2 (HP_RECOVERY)
Oct 26 20:27:57 HP-DV9820 ntfs-3g[3465]: Unmounting /dev/sdb7 (Recover2)
Oct 26 20:28:06 HP-DV9820 ntfs-3g[3470]: Unmounting /dev/sdb5 (SergioL505_RecoveryD)
Oct 26 20:28:06 HP-DV9820 ntfs-3g[3475]: Unmounting /dev/sdb9 (Spare172G)
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3480]: Unmounting /dev/sda1 (Vista64_JonHP)
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3617]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3617]: Mounted /dev/sdb2 (Read-Write, label "4_Media", NTFS 3.1)
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3617]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3617]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb2,blkdev,blksize=4096
Oct 26 20:28:11 HP-DV9820 ntfs-3g[3617]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:12 HP-DV9820 ntfs-3g[3625]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:12 HP-DV9820 ntfs-3g[3625]: Mounted /dev/sdb3 (Read-Write, label "9G_storage", NTFS 3.1)
Oct 26 20:28:12 HP-DV9820 ntfs-3g[3625]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:12 HP-DV9820 ntfs-3g[3625]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb3,blkdev,blksize=4096
Oct 26 20:28:12 HP-DV9820 ntfs-3g[3625]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3670]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3670]: Mounted /dev/sdb1 (Read-Write, label "Bakup_NTFS1", NTFS 3.1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3670]: Cmdline options: rw,nosuid,nodev,locale=en_US.utf8
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3670]: Mount options: rw,nosuid,nodev,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3670]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Mounted /dev/sda4 (Read-Write, label "CommonSpace1", NTFS 3.1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sda4,blkdev,blksize=4096
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3675]: Unmounting /dev/sda4 (CommonSpace1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3684]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3684]: Mounted /dev/sdb8 (Read-Write, label "DualRecovery", NTFS 3.1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3684]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3684]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb8,blkdev,blksize=4096
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3684]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3692]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3692]: Mounted /dev/sda2 (Read-Write, label "HP_RECOVERY", NTFS 3.1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3692]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3692]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3692]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3697]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3697]: Mounted /dev/sdb7 (Read-Write, label "Recover2", NTFS 3.1)
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3697]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3697]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb7,blkdev,blksize=4096
Oct 26 20:28:13 HP-DV9820 ntfs-3g[3697]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3702]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3702]: Mounted /dev/sdb5 (Read-Write, label "SergioL505_RecoveryD", NTFS 3.1)
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3702]: Cmdline options: rw,nosuid,nodev,locale=en_US.utf8
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3702]: Mount options: rw,nosuid,nodev,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3702]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3707]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3707]: Mounted /dev/sdb9 (Read-Write, label "Spare172G", NTFS 3.1)
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3707]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3707]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb9,blkdev,blksize=4096
Oct 26 20:28:14 HP-DV9820 ntfs-3g[3707]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:15 HP-DV9820 ntfs-3g[3714]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:15 HP-DV9820 ntfs-3g[3714]: Mounted /dev/sda1 (Read-Write, label "Vista64_JonHP", NTFS 3.1)
Oct 26 20:28:15 HP-DV9820 ntfs-3g[3714]: Cmdline options: rw,locale=en_US.utf8
Oct 26 20:28:15 HP-DV9820 ntfs-3g[3714]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Oct 26 20:28:15 HP-DV9820 ntfs-3g[3714]: Ownership and permissions disabled, configuration type 1
Oct 26 20:28:23 HP-DV9820 ntfs-3g[3692]: Unmounting /dev/sda2 (HP_RECOVERY)
Oct 26 20:28:24 HP-DV9820 ntfs-3g[3733]: Version 2010.3.6 external FUSE 28
Oct 26 20:28:24 HP-DV9820 ntfs-3g[3733]: Mounted /dev/sda2 (Read-Write, label "HP_RECOVERY", NTFS 3.1)
Oct 26 20:28:24 HP-DV9820 ntfs-3g[3733]: Cmdline options: rw,nls=utf8,umask=0222
Oct 26 20:28:24 HP-DV9820 ntfs-3g[3733]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096,default_permissions
Oct 26 20:28:24 HP-DV9820 ntfs-3g[3733]: Global ownership and permissions enforced, configuration type 1
Oct 26 20:35:08 HP-DV9820 vmnetBridge: Bridge process created.
Oct 26 20:35:08 HP-DV9820 vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003
Oct 26 20:35:08 HP-DV9820 vmnetBridge: RTM_NEWLINK: name:eth1 index:3 flags:0x00011043
Oct 26 20:35:08 HP-DV9820 vmnetBridge: Adding interface eth1 index:3
Oct 26 20:35:08 HP-DV9820 vmnetBridge: Started bridge eth1 to virtual network 0.
Oct 26 20:35:08 HP-DV9820 vmnetBridge: RTM_NEWROUTE: index:3
Oct 26 20:35:09 HP-DV9820 avahi-daemon[1117]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.6.1.
Oct 26 20:35:09 HP-DV9820 avahi-daemon[1117]: New relevant interface vmnet1.IPv4 for mDNS.
Oct 26 20:35:09 HP-DV9820 avahi-daemon[1117]: Registering new address record for 172.16.6.1 on vmnet1.IPv4.
Oct 26 20:35:09 HP-DV9820 vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Oct 26 20:35:09 HP-DV9820 vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.This appears to be about when the USB and/or NTFS filesystems started having trouble on the night of Oct 26th:

> Oct 26 21:30:43 HP-DV9820 vmnet-dhcpd: DHCPACK on 192.168.37.128 to 00:0c:29:42:7f:de via vmnet8
Oct 26 21:46:28 HP-DV9820 acpid: client 2453[108:114] has disconnected
Oct 26 21:46:28 HP-DV9820 acpid: client connected from 12583[108:114]
Oct 26 21:46:28 HP-DV9820 acpid: 1 client rule loaded
Oct 26 21:48:59 HP-DV9820 ntfs-3g[1025]: ntfs_mst_post_read_fixup: magic: 0x00000000  size: 1024  usa_ofs: 0  usa_count: 65535: Invalid argument
Oct 26 21:50:20 HP-DV9820 ntfs-3g[1025]: last message repeated 2 times
Oct 26 21:51:20 HP-DV9820 ntfs-3g[1025]: last message repeated 2 times
Oct 26 21:52:20 HP-DV9820 ntfs-3g[1025]: last message repeated 4 times
Oct 26 21:53:20 HP-DV9820 ntfs-3g[1025]: last message repeated 4 times
Oct 26 23:36:44 HP-DV9820 acpid: client connected from 21415[0:1000]
Oct 26 23:36:44 HP-DV9820 acpid: 1 client rule loaded
Oct 27 00:18:34 HP-DV9820 udevd-work[23263]: inotify_add_watch(6, /dev/sdc4, 10) failed: No such file or directory
Oct 27 00:18:34 HP-DV9820 udevd-work[23298]: inotify_add_watch(6, /dev/sdc6, 10) failed: No such file or directory
Oct 27 00:18:44 HP-DV9820 udevd-work[23299]: inotify_add_watch(6, /dev/sdc7, 10) failed: No such file or directory
Oct 27 00:18:44 HP-DV9820 udevd-work[23262]: inotify_add_watch(6, /dev/sdc3, 10) failed: No such file or directory
Oct 27 00:18:59 HP-DV9820 udevd-work[23301]: inotify_add_watch(6, /dev/sdc9, 10) failed: No such file or directory
Oct 27 00:18:59 HP-DV9820 udevd-work[23300]: inotify_add_watch(6, /dev/sdc8, 10) failed: No such file or directory
Oct 27 00:18:59 HP-DV9820 udevd-work[23198]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory
Oct 27 00:18:59 HP-DV9820 udevd-work[23297]: inotify_add_watch(6, /dev/sdc5, 10) failed: No such file or directory
Oct 27 00:35:58 HP-DV9820 ntfs-3g[3670]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 00:35:58 HP-DV9820 ntfs-3g[3670]: Failed to read index block: Input/output error
Oct 27 00:35:58 HP-DV9820 ntfs-3g[3670]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 00:35:58 HP-DV9820 ntfs-3g[3670]: Failed to read index block: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: Failed to read vcn 0x4: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: Failed to read index block: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:17 HP-DV9820 ntfs-3g[3625]: Failed to read vcn 0x4: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: Failed to read vcn 0x4: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: Failed to read index block: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Oct 27 01:00:22 HP-DV9820 ntfs-3g[3625]: Failed to read vcn 0x4: Input/output error
Oct 27 01:02:58 HP-DV9820 ntpd[1540]: kernel time sync status change 6001
Oct 27 01:13:15 HP-DV9820 acpid: client 21415[0:1000] has disconnected
Oct 27 01:13:15 HP-DV9820 acpid: client connected from 25895[0:1000]
Oct 27 01:13:15 HP-DV9820 acpid: 1 client rule loadedThere also appears to be quite a bit more "Failed to read index block: Input/output error"-type output.

Does anyone know of a relatively-quick fix in the bootup scripts or **udev rules.d** that I can apply to get my Ubuntu 10.04.3 LTS booting again?  This does NOT appear to be a problem with Grub2- the trouble happens much later than that in the boot process (and this is the first time that I've encountered this problem).

---

