---
title: "Cannot Share RAID Array"
date: 2010-08-12
forum: General Help
---

### Post by sceptre0 on 2010-08-12
I am having trouble sharing folders on my new software RAID formatted as ext4.  I can share folders in my home directory and on my NTFS drive.  I compared the permissions of one of the shared NTFS folders to the ext4 folder and they are exactly the same.  I'm out of ideas for what to check next.  I attached the mdadm.conf, fstab, and samba configurations below.  Thanks in advance for any help.

> 
ls -l /media/RAID5/
drwxrwxrwx  2 user_name root 4096 2010-08-11 21:43 New


> 
ls -l /media/Media/
drwxrwxrwx 1 user_name root        24576 2010-08-01 20:47 Movies


> 
sudo mdadm --version
mdadm - v3.1.2 - 10th March 2010


> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
#CREATE owner=user_name group=disk mode=0660 auto=yes
CREATE owner=user_name group=root mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/desktop:0 metadata=1.2 name=desktop:0 UUID=88d7fb69:2373f7f1:bdc00c63:fa02236c

# This file was auto-generated on Sat, 07 Aug 2010 03:10:00 -0500
# by mkconf $Id$


> 
# Media
/dev/sdb1                                  /media/Media   ntfs         nls=iso8859-1,users,umask=000,user,owner,uid=user_name  0  0  
# RAID5
/dev/md0                                   /media/RAID5   ext4         rw,auto,user                                           0  1


> 
testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[complete]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[complete]
	comment = Complete Downloads
	path = /media/RAID5/complete
	read only = No
	guest ok = Yes


---

### Post by sceptre0 on 2010-08-12
This issue was solved in another forum.

[http://www.linuxquestions.org/questions/linux-software-2/samba-shares-not-accessible-on-raid-array-825924/](http://www.linuxquestions.org/questions/linux-software-2/samba-shares-not-accessible-on-raid-array-825924/)

---

