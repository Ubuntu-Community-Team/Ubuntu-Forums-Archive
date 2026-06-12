---
title: "SAMBA: Permissions changing automatically?"
date: 2006-02-01
forum: General Help
---

### Post by nuke1138 on 2006-02-01
I am trying to setup a Ubuntu box as a fileserver for my home network.  Right now I only have one client pc (XP)  My goal was to set up XP's "My Documents" folder to reside on the Ubuntu machine, then map a drive to it from XP.

First I mounted a vfat partition with the following in fstab:
```
/dev/sda3       /home/jason/media      vfat  umask=000   0  0
```

Then I set up samba with the following share
```

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam, guest
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
[Documents]
	path = /home/jason/media/Documents
	read only = No
```
These were mostly defaults from SWAT.  

I set up a Ubuntu user called "jason" and made an smb user with the same name.  I also have an XP user "jason".  Both the Ubuntu user and the XP user have the same password.  "jason" also owns "/home/jason/media/Documents".  Everthing worked fine.  I could browse to the SAMBA share from XP through Network Neighborhood and could map drives to the share from XP.  I copied all my data to the SAMBA share and realized the first problem.

XP creates a file called "Thumbs.db" that keeps thumnails of pictures in a folder.  This file is created with both the system and hidden Windows attributes.  Normally these files are not displayed beause of the "Hide protected operating system files" option in Windows.  Once I copied folders with this "Thumbs.db" file to Ubuntu, they showed up in XP even though I had the option to hide them selected.  Not a major problem but annoying none the less.

It seems that Unix permissions don't match up with Windows attributes.  SAMBA accounts from this with the "MAP SYSTEM", "MAP HIDDEN", and "MAP ARCHIVE" options.  "MAP ARCHIVE" is turned on by default but the other two are off.  OK problem solved right?

I added the following to smb.conf
```

[Documents]
	path = /home/jason/media/Documents
	read only = No
	create mask = 0755
	map system = Yes
	map hidden = Yes
```

Everything worked after that.  I could change attributes on the windows side and they were reflected on the SAMBA share.  I'm not sure what the "create mask" entry does, but it didn't seem to work without it.  I was happy until the next morning.  I opened up the SAMBA share from XP and all my files were gone!  

I looked at them on the Ubuntu side and they were still there.  I turned off the "Hide protected operating system files" in Windows and low and behold the files showed up.  I changed all the attribues again on the Windows side and everything looked good again.  I left the PC for a while and came back later that evening and the files were hidden again.  What is going on?

I assume this has to do with either "umask=000" option if fstab or the "create mask" smb.conf.  Neither of which I fully understand.

The only thing I see happening in the logs that might be pertinent is this entry in /var/log/syslog:
```
localhost /USR/SBIN/CRON[18755] (root) CMD (   run-parts --report /etc/cron.hourly)
```
I haven't timed it to see if this problem occurs after this job runs, but there is nothing in cron.hourly anyway.

How are my permissions changing?

Tonight I just stumbled across a post talking about a file system called smbfs.  Should I be using that instead of vfat?

---

