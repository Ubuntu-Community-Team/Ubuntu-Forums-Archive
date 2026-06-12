---
title: "Dancing the SAMBA ... and going nuts"
date: 2011-04-19
forum: General Help
---

### Post by castalla on 2011-04-19
All I want is a simple Samba installation that anonymous users/guests can access.  I have modified the smb.conf file so much using 'tips' that should enable a simple folder share.  Nothing works.   

If I share the folder using Nautilus share then the folder is accessible without any credentials from only Win7 and android ES File Explorer.  XP can't see the folder, nor can any other linux device.

I've been struggling with this for days.  I want to switch to linux as a main OS but without shares it's not practical.

Does anyone have a stripped down smb.conf which provides guest access to a single folder?   

Here's the latest testparm -s

```
 $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
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
	path = /home/mint/Shared
	read only = No
	create mask = 0777
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	create mask = 0700
	guest ok = No
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes
	guest ok = No

```

---

### Post by Morbius1 on 2011-04-19
You keep forgetting to post the Usershare definitions. You can create samba shares using two different methods. The Classic method and Usershares. Classic shares have share defintions in smb.conf. Usershares have share definitions in /var/lib/samba/usershares.

The other post you had on this listed the following usershares:
> mint@mint ~/Desktop $ [COLOR=Blue]net usershare info --long[/COLOR]
[QUOTE][shared]
path=/home/mint/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

[downloads]
path=/home/mint/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/mint/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y                      I'm beginning to think that you have a firewall in the way on 2 of the 4 machines that cannot access the shares. Install the following package:
```
sudo apt-get install nmap
```Then run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Change 192.168.0.100 to the ip address of one of the boxes that can't connect to your Unbuntu machine. Yo need the following ports on that machine  for samba to work:
> 139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm


---

### Post by pricetech on 2011-04-19
I haven't manually edited an smb.conf in a long time.

Samba tutorial here:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

Back up your current smb.conf and restore the original first, then install and configure the easy way.

Have fun with it.

---

### Post by gordintoronto on 2011-04-19
> **castalla said:**
> All I want is a simple Samba installation that anonymous users/guests can access.  I have modified the smb.conf file so much using 'tips' that should enable a simple folder share.  Nothing works.   

If I share the folder using Nautilus share then the folder is accessible without any credentials from only Win7 and android ES File Explorer.  XP can't see the folder, nor can any other linux device.


I play around with half a dozen versions/distros of Linux every year. I always set up a share using Nautilus (if the distro has Nautilus) and I never, ever edit smb.conf. I have never had Windows XP or Windows 7, or the other Linux boxes, fail to access the share.

---

### Post by Morbius1 on 2011-04-19
@gordintoronto, He created his shares using Nautilus just as you described. "net usershare info --long" on his other post showed how his Nautilus-shares are set up:
> [shared]
path=/home/mint/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

[downloads]
path=/home/mint/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/mint/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y                      
He has 2 machines that have no problem accessing those shares. He  has 2 machines that don't even know the ubuntu box exists.

I truly believe there is nothing wrong with how he set up his existing shares or else no one would be able to access it. It sure sounds like something on the 2 machines that can't see the shares are the problem. 
[COLOR=Blue][B]
EDIT:[/B][/COLOR] Maybe it's a firewall. Maybe the two machines that can access it are on the same subnet and the other 2 are not.

---

### Post by castalla on 2011-04-20
here's the current share definitions:

```
mint@mint ~/Desktop $ net usershare info --long
[music]
path=/home/mint/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[shared]
path=/home/mint/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

One media player suddenly started to see the shares without a problem.

The second device still insists on a user login.  here's the netmap for this device:

```
sudo nmap -sS -sU -T4 192.168.0.128

Starting Nmap 5.21 ( http://nmap.org ) at 2011-04-20 12:32 UTC
Nmap scan report for HDFS.lan (192.168.0.128)
Host is up (0.0092s latency).
All 2000 scanned ports on HDFS.lan (192.168.0.128) are closed (1014) or open|filtered (986)
MAC Address: 00:1F:1F:03:16:2B (Edimax Technology Co.)

Nmap done: 1 IP address (1 host up) scanned in 11.32 seconds

```

This device cannot see Win7 shares either because it uses MS-RAP which was deprecated in Win7.  Same symptom - requests a login which always fails.

Is there a legacy setting which could be set for Samba?  Another user told me it works with Hardy Heron - so maybe that was using a more compatible samba version?

---

