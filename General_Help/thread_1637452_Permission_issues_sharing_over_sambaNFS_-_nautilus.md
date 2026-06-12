---
title: "Permission issues sharing over samba/NFS - nautilus?"
date: 2010-12-04
forum: General Help
---

### Post by DarkGreen16 on 2010-12-04
I'm trying to share a folder with my media player on my ubuntu 10.10 amd64 machine but am having issues with the permissions. I did a bit of googling and it seems there is a known bug that has persisted for years that prevents you from modifying permissions via the GUI in nautilus. 

Is there any work around for that? An alternative GUI tool? I'm assuming not really so I was hoping someone could give me some command line help to get my permissions right. I've tried reading the wiki but it's not getting me what I want.

Could someone tell me how I can match the permissions in the image attached (I want the one on the right to match the one on the left)


Thanks in advance

---

### Post by Morbius1 on 2010-12-04
Not enough information to answer the question I'm afraid.

The one on the left has permissions of 755 and is the Linux standard permissions.

The one on the right has permissions of 700 and looks an awful lot like an ntfs or fat32 formatted filesystem that you are mounting dynamically as apposed to having an entry in fstab. 

Linux cannot change permissions on a windows filesystem outside of a mount or in fstab.  That's not a bug in Linux - that's the way Windows designed their filesystem.

You can use Samba as a way around this problem by using a "force user = your-user-name" in smb.conf but we need to know what method of samba sharing you are using - there are two. Post the output of the following commands and we can tell you where to put the "force user" line:
```
net usershare info --long
``````
testparm -s
```

---

### Post by DarkGreen16 on 2010-12-04
@morbius

```
[untitled]
path=/media/D420FAB520FA9E24/untitled folder
comment=
usershare_acl=Everyone:F,
guest_ok=y
```


```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Downloads]"
Processing section "[untitled folder]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = MWKHOME
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

[Downloads]
	path = /home/michael/Downloads
	read only = No
	guest ok = Yes

[untitled folder]
	path = /media/D420FAB520FA9E24/untitled folder
	read only = No
	guest ok = Yes

```


Thanks

---

### Post by Morbius1 on 2010-12-04
There are two different methods to use Samba to share folders: Usershare ( aka Nautilus-share ) and Classic shares. You're using both at the same time on the same folder. Using both methods can be done but it will cause you nothing but grief in the long run. Since you have more classic-shares than Usershares I would recommend getting rid of the Usershare:
```
 net usershare delete untitled
```Or just go back into nautilus and "unshare" /media/D420FAB520FA9E24/untitled folder.

For your original problem:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [untitled folder] section so that it looks like this:
> [untitled folder]
    path = /media/D420FAB520FA9E24/untitled folder
    read only = No
    guest ok = Yes
    [COLOR=Blue]force user = michael[/COLOR]Save smb.conf and in the terminal restart samba:
```
sudo service smbd restart
```Now see if the remote user can get access.

---

### Post by DarkGreen16 on 2010-12-04
@morbius

That worked a treat - thanks for your help.


Is there an easier way to do that - like via a GUI for example? I would hate to have to edit a txt file every time I need to add another share.

---

### Post by Morbius1 on 2010-12-05
> Is there an easier way to do that - like via a GUI for example?In a word - No. There are Samba GUI configuration utilities out there but they all tend to be destructive in that they don't start with your current smb.conf and allow you to edit it. Instead they either start with a blank slate and expect you to build one from scratch or start with what they think should be default settings. If you've got 12 years experience as a Systems administrator then go for it. I'm not one of those people.
> I would hate to have to edit a txt file every time I need to add another share.It looks like all of your shares are guest shares so for this kind of sharing environment you could move "     [COLOR=Blue]force user = michael[/COLOR]                      " out of the [untitled folder] section and place it in the [global] section. It then becomes the default and once it's done you'll never have to go back in there again. Place it under the "workgroup" line so that it looks like this:
> workgroup = MWKHOME
    [COLOR=Blue]force user = michael[/COLOR] 

---

### Post by DarkGreen16 on 2010-12-05
Aye cap'em - thanks again

---

