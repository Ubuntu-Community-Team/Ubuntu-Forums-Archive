---
title: "USB Automount"
date: 2006-06-18
forum: General Help
---

### Post by crroush on 2006-06-18
Since upgrading to Dapper, I have ran into 2 problems (not bad for an upgrade)
First was my ethernet card device was changed from eth0 to eth1, which was easily fixed.  However second problem I have not been able to solve.  I have searched both google and the forums and have not been able to resolve the issue.

Problem:
When I put in a USB thumb drive I get the KDE gui pop up message that a new medium has been detected.  Medium type: Unmounted Removable Medium.  It asks me what I would like to do, either 1. Open in New Window or Do Nothing.

When the option Open in New Window is selected, Konquereror comes up in directory /media/sdb1 and displays the following error:  
> Could not mount device.  The reported error was:  mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab.

My fstab entry says:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/sda5 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hda1 /mnt/windows ntfs noauto,uid=0,gid=0,auto,ro,nouser 0 0

my mtab says:
> 
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0


From /var/log/messages:
> 
messages:Jun 18 14:46:51 localhost kernel: [17195527.320000] SCSI device sdb: 1014784 512-byte hdwr sectors (520 MB)
messages:Jun 18 14:46:51 localhost kernel: [17195527.324000] sdb: Write Protect is off
messages:Jun 18 14:46:51 localhost kernel: [17195527.324000] SCSI device sdb: 1014784 512-byte hdwr sectors (520 MB)
messages:Jun 18 14:46:51 localhost kernel: [17195527.324000] sdb: Write Protect is off
messages:Jun 18 14:46:51 localhost kernel: [17195527.324000]  sdb: sdb1
messages:Jun 18 14:46:51 localhost kernel: [17195527.392000] sd 2:0:0:0: Attached scsi removable disk sdb


Thanks
-Craig

---

### Post by crroush on 2006-06-24
After spending some more time, I determined that I had to be a part of group **plugdev**.  Everything works as expected.  So if anyone else runs into my problem, try that :)

---

### Post by alexc_m2k on 2006-07-05
It's a good tip.\\:D/ 
THank you.

---

