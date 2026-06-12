---
title: "Can't access shared folder from Win XP laptop."
date: 2012-05-12
forum: General Help
---

### Post by scweston on 2012-05-12
Dear all,

I've tried searching on this forum and tried several of the various how-to guides on setting up file and printer sharing but I always seem to come up with the same problem. For your information I am running a fairly fresh install of Ubuntu 12.04.

I just can't seem to access the share from my windows xp laptop. I can see my ubuntu computer listed under workgroup when I go to Start>My Network Paces>View workgroup computers. But when I click on the computer it tells me the server is not accessible. I've added a screen shot of the problem.

As you can see from the screen shot I have deactivated the windows firewall to see if that was blocking it but to no avail.

I'm assuming this is a problem with the way I have set up ubuntu as I am unable to access the share from another windows computer also. With past versions of Ubuntu I don't remember having to do anything particularly special to get file sharing working.

As things to do with file and printer sharing often involve the configuration file smb.conf . I have attached it to this message (had to attach this as the renamed smb.txt file)

Thanks in advance for your help or suggestions. I've always really appreciated the help I get on the ubuntu forums and nearly always get a workable solution to my problems. Please do let me know if you need any more information.

Regards

Stephen

---

### Post by scweston on 2012-05-12
If it helps I've got the output of the command testparm -s

Here's hoping someone can give me a hand at fixing this.

Stephen


```
stephen@stephen-X58-USB3:~$ net usershare info
stephen@stephen-X58-USB3:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = Ubuntu Server
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
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/stephen/Documents
	valid users = nobody, stephen
	read only = No
stephen@stephen-X58-USB3:~$ 
```

---

### Post by Morbius1 on 2012-05-12
Edit /etc/samba/smb.conf as root and add a line to the [global] section - right under the workgroup line:
```
netbios name = stephen-X58
```[COLOR=Blue]*It doesn't have to be that exact name but it has to be 15 characters or less in length. Yours is 16 characters long.*[/COLOR]

Then restart samba:
```
sudo service nmbd restart
sudo service smbd restart
```> [Documents]
path = /home/stephen/Documents     
valid users = nobody, stephen     
read only = NoThat's kind of confusing. Not sure if that's supposed to be a guest share or what but in any event if you really want "nobody" to have write access to the share you need to make sure "others" has write access:
```
chmod 0777 /home/stephen/Documents
```

---

### Post by scweston on 2012-05-12
Thank you Morbius1.

Adding the 'netbios name =' worked a treat to fix that problem (any reason why I had to do this for Ubuntu 12.04, but not previous versions?)

With regard to the confusion over the 'nobody' in the share. I think that earlier I was getting a bit desperate in trying to fix the problem and was just trying various options that I didn't understand to see the affect they would have and if they would fix my problem (as you can guess they didn't). This option was in the samba GUI 'system-config-samba'. When I created the share in the 'access' tab there was a user 'nobody' listed. Have no idea what selecting that does and I am confused by the presence of the user 'nobody', but thought I'de give it a go. I am still non the wiser!

Also, now I've sorted this problem out I've tried to sort out printer sharing too and ran in to more problems.

First, after a reboot of my Ubuntu pc I can only get my shared printer to show up in Win XP if I restart samba (i.e. type sudo service smbd restart in a terminal). Also, when I do manage do get it to show up I can't get my Win XP laptop to connect to it. I think the latter of these problems may be related to what's in [this]("http://ubuntuforums.org/showthread.php?t=1971847&highlight=printer+sharing&page=2") thread which you appear to have also commented in (I will try some of the solutions mentioned their tomorrow). The former of this problem I would like some help with. Perhaps it could be a repeat of a problem I was having some years back with a previous version of ubuntu ([link]("http://ubuntuforums.org/showthread.php?t=1477230") to an old thread), but this seemed to have been fixed for later versions so I'm hoping its not a regression.

Again any help would be appreciated Morbius1 (or anybody else). I really do appreciate the time people give to help.

Regards,
Stephen

---

### Post by Morbius1 on 2012-05-12
> Adding the 'netbios name =' worked a treat to fix that problem (any  reason why I had to do this for Ubuntu 12.04, but not previous  versions?)The 15 character limit on the netbios name has been a "rule" since Eisenhower was a Private so frankly I have no idea why it would have worked before.

The "you have to restart samba to see the printer" problem sounds like a timing issue. CUPS is ultimately in charge of printing not Samba. Samba passes the request to cups but cups must provide a list of it's printers for Samba to display to the client user. So during boot what should happen is the cups service starts first then smbd starts. If it happens the other way around there is noting for Samba to display.

As you noted in the other topic you linked to there seems to be an issue with samba and how it talks to cups anyway so even if you fix this timing issue you may not resolve the problem. In that topic I suggested that this is a samba problem but it appears that cups has bug reports of it's own so I'm not sure anymore. 

In any event as the other topic illustrated the best thing is to avoid samba altogether for the printer and access cups directly.

---

