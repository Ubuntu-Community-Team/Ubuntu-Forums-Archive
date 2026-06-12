---
title: "Editing/Configuring Samba"
date: 2010-11-01
forum: General Help
---

### Post by Quarkrad on 2010-11-01
Newbie using 10.10.  I have two 10.10 machines, A and B, in the same room connected on a LAN - I have managed to get samba working between them that allows me to read files on B from A.  What I would like to do is to be able to write/edit/save files on B and also transfer files/documents from A to B.  As a newbie I try to do things via a GUI but am reasonably happy with the terminal.  Is it possible/easy to change my permissions to allow this?  As the two machines are both mine I do not want to have to use a password to do this.  Currently, from A, I can see the shared folder on B via Places/Network - I can see B and navigate to the shared folder.

---

### Post by HermanAB on 2010-11-01
Howdy,

Try this:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by Morbius1 on 2010-11-01
You never mentioned what method of Samba sharing you are using - there are 2: Classic-shares and Usershares ( i.e., nautilus-shares ). 

Had you used Usershares the permissions problem would not be an issue but just to make sure post the output of the following commands so we can see what method you are using and how you are set up:
```
net usershare info --long
``````
testparm -s
```
[B][COLOR=Blue]
EDIT:[/COLOR][/B] And tell us if any of the shares are pointing to a FAT32 or NTFS mounted partition. It matters only in the way permissions have to be adjusted for remote guest access.

---

### Post by Quarkrad on 2010-11-01
From A which is the client there was no output from net usershare info -- but there was from testparm -s

dad@dadubuntu:~$ sudo su
[sudo] password for dad: 
root@dadubuntu:/home/dad# net usershare info --long
root@dadubuntu:/home/dad# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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
	dns proxy = No
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
root@dadubuntu:/home/dad# 

From B - the server, this is the output for the same commands:

liz@lizubuntu:~$ sudo su
[sudo] password for liz:
root@lizubuntu:/home/liz# net usershare info --long
[home_files]
path=/media/Home_Files
comment=
usershare_acl=Everyone:F,
guest_ok=y

root@lizubuntu:/home/liz# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Home_Files]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
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

[Home_Files]
    comment = Home Files
    path = /media/Home_Files
    read only = No
    guest ok = Yes
root@lizubuntu:/home/liz# 

The shared folder on B is on a NTFS partition

---

### Post by Morbius1 on 2010-11-01
It turns out that on "B" you are using both samba methods on the same target directory:

This is a usershare ( Nautilus > Sharing Options ):
> [home_files]
path=/media/Home_Files
comment=
usershare_acl=Everyone:F,
guest_ok=yThis is a classic-share:
> [Home_Files]
    comment = Home Files
    path = /media/Home_Files
    read only = No
    guest ok = YesIt's best not to use both methods at the same time on the same target so I would delete the usershare:
```
sudo net usershare delete home_files
```Or just go back into Nautilus and remove all the checks from "Sharing Options"

As for your original dilemma one way is to adjust your parameters in fstab to accommodate "guests" by allowing "other"'s to read write or you could use samba itself around this problem.

Assumming user "liz" has read write access to /media/Home_Files change this:
> [Home_Files]
    comment = Home Files
    path = /media/Home_Files
    read only = No
    guest ok = YesTo this:
> [Home_Files]
     comment = Home Files
     path = /media/Home_Files
     read only = No
     guest ok = Yes
**[COLOR=Blue]force user = liz[/COLOR]**Save smb.conf and restart samba:
```
sudo service smbd restart
```

---

### Post by Quarkrad on 2010-11-01
Perfect - many thanks.

---

