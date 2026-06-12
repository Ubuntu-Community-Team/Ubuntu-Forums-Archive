---
title: "Forcing permissions on all contents of a folder??"
date: 2010-04-15
forum: General Help
---

### Post by nrajlich on 2010-04-15
Hello all, it's been a while since I've posted, so thanks for looking!

I have a folder that I share using Samba. The permissions with Samba seem to be correct, since as a Windows client, I can put new files and folders in the share.

Torrents also get downloaded into this folder on the computer through rTorrent. Files/folders downloaded are a different username/group than files/folders added as a Samba client (windows), and the Samba client has read only access to downloaded torrents.

If I manually change a download's permissions to 777 for example, then the Samba client CAN modify the download.

So what I'm trying to accomplish is a way make these downloads writable to the Samba clients. I was thinking by making everything in the root share be forced to 777 when they are placed in the folder, but I don't know how to do that. There's probably a better strategy anyways. Any advice is appreciated. Thanks! :D

---

### Post by colorlessprism on 2010-04-15
nautilus in 9.10 offers a "Share" tab when the folder is right clicked. all i had to do was check "share" name my folder, check allow other to modify, and check allow guest users. that was all i had to do. i keep my share folder in my /home/XXXX directory though.

---

### Post by nrajlich on 2010-04-19
> **colorlessprism said:**
> nautilus in 9.10 offers a "Share" tab when the folder is right clicked. all i had to do was check "share" name my folder, check allow other to modify, and check allow guest users. that was all i had to do. i keep my share folder in my /home/XXXX directory though.

Well my situation is very similar then. I set up the share using the "Share" tab in nautilus, and checked "allow others to modify", and checked "allow guests". The share is in ~/Downloads with full permissions.

Client can read and write fine. The problem only occurs when an external program (background service) running on the server adds a new file or folder to this Downloads folder. The new file or folder created by the service running on the computer has conflicting permissions than what the Samba clients have access to.

---

### Post by Morbius1 on 2010-04-19
Please post the output of the following commands so we can see how things are set up. You may just need a "force user" in smb.conf but I want to make sure I'm understanding your description first:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by nrajlich on 2010-04-21
> **Morbius1 said:**
> Please post the output of the following commands so we can see how things are set up. You may just need a "force user" in smb.conf but I want to make sure I'm understanding your description first:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

**net usershare info** gave no ouput at all...

Below is the output from **testparm -s**:

```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cdrom]"
Processing section "[Public Downloads]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	interfaces = lo, eth1
	bind interfaces only = Yes
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[cdrom]
	comment = Samba server's CD-ROM
	path = /cdrom
	guest ok = Yes
	locking = No

[Public Downloads]
	comment = Public Downloads folder for all users
	path = /home/nrajlich/Downloads
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

```

The "Public Downloads" share is the share in question. Thanks for taking the time!

---

### Post by Morbius1 on 2010-04-21
Something doesn't add up here:
> I set up the share using the "Share" tab in nautilus, and checked "allow others to modify", and checked "allow guests". The share is in ~/Downloads with full permissions.If you did that then **net usershare info** should have had an output.
Unless you shared the directory as root in which case you'd see output with: **sudo net usershare info.**

What are the permissions on the target directory:
** ls -al /home/nrajlich/Downloads**

---

