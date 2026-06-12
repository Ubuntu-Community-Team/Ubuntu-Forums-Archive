---
title: "Samba guest shares - utterly baffled!!!"
date: 2011-04-14
forum: General Help
---

### Post by castalla on 2011-04-14
I'm using Mint 10.10

I installed samba (and nautilus-shares).  I just can't get guest shares to work.  

In fact I'm not even sure that samba is running (although package manager reports that it is installed) since testparm just reports that the command is available in samba-common-bin (which is also installed).

Can somebody please give me 'noobie' steps on how to get guest access working?   The guest access option in nautilus sharing is always greyed out.

I must have read dozens of how-to's - none of which really help and I'm just totally confused.

Help please!

---

### Post by Morbius1 on 2011-04-14
nautilus-shares is installed by default and the first time you use it it will install samba for you so I'm not sure what OS you're running.

Anyway you need to make sure 2 things are set to have guest shares as an available option:

[FONT=monospace][1] Open smb.conf as root:
[/FONT]```
[FONT=monospace]gksu gedit /etc/samba/smb.conf[/FONT]
```[FONT=monospace]
[/FONT][FONT=monospace]Add the following lines to the [global] section:
[/FONT]```
[FONT=monospace]usershare allow guests = yes[/FONT]
```[FONT=monospace]
Save smb.conf, exit gedit, and back in the terminal restart samba:
[/FONT]```
[FONT=monospace]sudo service smbd restart[/FONT]
```[FONT=monospace]
[/FONT][2] Make sure you a member of the right group:
```
sudo gpasswd -a your-user-name sambashare
```Logout and login again for the group membership to take affect.

If you're still having problems post the output of the following commands:
```
net usershare info --long
testparm -s
```

---

### Post by castalla on 2011-04-14
Here's the result:

mint@mint ~/Desktop $ sudo service smbd restart
smbd start/running, process 5526


mint@mint ~/Desktop $ net usershare info --long
The program 'net' can be found in the following packages:
 * samba-common-bin
 * samba4-clients

As I said above - package installer shows that samba-common-bin is installed.

I guess I'm user mint ?   So, should I enter:

sudo gpasswd -a mint sambashare

Thanks for your help.  I actually had this working following a tutorial which explained exactly the changes for smb.conf (but I stupidly didn't bookmark it!) - distro crashed and I lost the settings on reinstall.

---

### Post by Morbius1 on 2011-04-14
Your install of samba is messed up.

(1) Go into synaptic and remove all Samba4 stuff. 

(2) After you are sure all Samba4 packages are removed install the following packages:
```
samba
samba-common
samba-common-bin
smbclient
python-smbc
```

Then restart samba and do the things I posted earlier.

---

### Post by castalla on 2011-04-14
Synaptic doesn't show any samba4 packages.  I reinstalled samba-common-bin, and testparm now works ...

> int@mint ~/Desktop $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, LinuxMint)
	security = SHARE
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


Net usershare  just returns the cursor.

---

### Post by castalla on 2011-04-14
Oh-oh - just tried nautilus share and the guest user access is now available!

Hang on I'll try it out ....

---

### Post by castalla on 2011-04-14
It worked!  BUT a big problem - I've now lost the taskbar!!!  Why??????

Any tips on how to get it back from terminal?

---

### Post by Morbius1 on 2011-04-14
That I can't help you with at the moment.

It sure does sound like a bad install to me though. The thing about Mint - at least the DVD ISO is that it installs Samba and everything else you need by default. In fact you can create a Samba Server running the DVD.iso itself without an install.

The Debian Edition is another story since all the packages are installed correctly but are not configured correctly from the start - it's a Debian thing.

---

### Post by castalla on 2011-04-14
I'll persevere ... I finally got a menu taskbar back sith sudo gnome-panel ... but Quit wouldn't work ... had to shutdown from terminal.

Finally got it back.  

Saring works now - guess it was the samba-common-bin which was messed up.  

There's another problem with the folder icons - when I share the folder in nautilus then a flag is added (top-right) or bottom right if it's just guest access.

If I restart, the shares are still there but the top right flag is missing from the folder icon.  The bottom right flag is still shown.

Any ideas?

Thanks a lot for your help - I'm learning something here!

---

### Post by castalla on 2011-04-14
The missing icon flag is a bug in Mint!

It doesn't happen if you create a new folder and share that - flag disappears only on the standard home folders.

Anyway - thanks again for the help.

---

