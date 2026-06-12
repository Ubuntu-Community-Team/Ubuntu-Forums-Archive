---
title: "Lubuntu File Sharing"
date: 2012-03-12
forum: General Help
---

### Post by Jerry N on 2012-03-12
I always seem to have trouble sharing ?buntu files with Windows.  I get everything set up, Win 7 sees the share, butI get a message in Windows asking for a name and password.  I never have this problem with Linux Mint.  Currently, I am comparing Mint 12 LXDE with Lubuntu 11.10.  Mint LXDE shares OK, but I run into the name/password problem with Lubuntu.  I have installed apache2.2-bin, libapache2-mod-dnssd, and systm-config-samba (same as with Mint).  Where have I gone wrong?  This is one of the things that makes me prefer Mint over Ubuntu and, as far as I am concerned, is a showstopper.

Jerry

---

### Post by marinara on 2012-03-13
please file a bug

---

### Post by Morbius1 on 2012-03-13
> I have installed apache2.2-bin, libapache2-mod-dnssd, and systm-config-samba (same as with Mint).  Where have I gone wrong? That's 2 completely different file sharing protocols.

apache2.2-bin and libapache2-mod-dnssd have to do with "Personal File Sharing" and you would have to have gnome-user-share installed which I don't think Lubuntu installs by default.

system-config-samba is the Samba server configuration utility. Let's focus on the Samba part of this because Personal File Sharing just barely works between Linux machines.

Please post the output of the following command:
```
testparm -s
```

---

### Post by Jerry N on 2012-03-13
Testparm -s as follows.  Note:  Testparm -s shows identical results for Mint 12 LXDE and for Lubuntu 11.10

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
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

[Public]
	path = /home/jn/Public
	read only = No
	guest ok = Yes

---

### Post by Morbius1 on 2012-03-13
Without knowing any other particulars on how you are set up, the 3 things off the top of my head that would get in the way of accessing that share are:

[1] The Linux permissions on the target do not allow guest access so fix it:
```
sudo chmod 0777 /home/jn/Public
```[2] The entire path to the target does not allow "others" to access the subfolder:

/home and /home/jn should have permissions of something like this:
> drwxr-xr-x[3] You encrypted your home directory.

---

### Post by Jerry N on 2012-03-13
> **Morbius1 said:**
> Without knowing any other particulars on how you are set up, the 3 things off the top of my head that would get in the way of accessing that share are:

[1] The Linux permissions on the target do not allow guest access so fix it:
```
sudo chmod 0777 /home/jn/Public
```[2] The entire path to the target does not allow "others" to access the subfolder:

/home and /home/jn should have permissions of something like this:
[3] You encrypted your home directory.

1.  Did that - no joy
2.  Permissions at drwxrwxrwx  - no joy
3.  Of course not.

I always have this trouble with Ubuntu, never with Mint.  Way back in Ubuntu 7 and 8, I could fix it with a couple of lines I got from smb.conf in Freespire, of all places.  There may have been versions of Ubuntu that worked, I don't remember for sure now.  Anyway, Mint works.

PS Reading and writing to Win 7 folders from Ubuntu and Mint always works OK.

---

### Post by Morbius1 on 2012-03-13
> 1.  Did that - no joySo when you run the following command:
```
ls -dl /home/jn/Public
```you get:
> drwxrwxrwx>  2.  Permissions at drwxrwxrwx  - no joyYou have /home and /home/jn set at universal r/w/x access? Why would you do that?
> 3.  Of course not.I'll take your word that you remember if you have encrypted your home directory.

You using the same username on Win7 that you are using on Ubuntu by any chance?

---

