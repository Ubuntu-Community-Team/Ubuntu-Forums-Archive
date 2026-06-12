---
title: "Backing up a Linux Root Drive (based of Heliode's post)"
date: 2011-08-16
forum: General Help
---

### Post by Spitfire1900 on 2011-08-16
[CENTER][CENTER]Backing up a Linux Root Drive[/CENTER][/CENTER]
  [CENTER][CENTER]HowTo[/CENTER][/CENTER]
  [CENTER][CENTER] [/CENTER][/CENTER]
  Create a network share location that you can place the Backup file on from Linux. 
   
  Run this command to backup the Linux system. (Make sure to do it as root).
   
  tar –cvp --exclude=/proc –exclude=/lost+found –exclude=/home/eot-it/BackupPortal[[MSOffice1]]("http://ubuntuforums.org/#_msocom_1")  –exclude=/mnt –exclude=/sys –exclude=/dev –exclude=/etc/fstab –exclude=/sbin –exclude=/bin exclude=/boot exclude=/etc/grub / | bzip2 > /home/eot-it/BackupPortal/Backup.bz2
   
  the –exclude=/usr/src likely can be included in the above command as it only include the linux drivers src repository, which doesn’t change much. But including may guarantee a restored system can recognize all device you installed post OS installation.
   
  To restore the system on a new machine grab the Ubuntu Installation disc (with same version #), install it on a new machine with sufficient resources with no additional apt programs installed. Mount the network share, enable and login as root, then run this command:
   
  tar –jxvpf /home/eot-it/BackupPortal/Backup.bz2 –C /
   
  The restoration should now commence, restart the machine when finished.
   
  **Note:** After the restoration in a test setup networking was broken. This was fixed by changing the network interface device from eth0 to eth1 in /etc/network/interfaces. Check the name of your interface by running sudo lshw.
             [[MSOffice1]]("http://ubuntuforums.org/#_msoanchor_1")This is the network share that we are backing up to. Yours may be different.

---

