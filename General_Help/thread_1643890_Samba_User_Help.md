---
title: "Samba User Help"
date: 2010-12-12
forum: General Help
---

### Post by atomictaco on 2010-12-12
I am fairly new to Linux.  I have Samba installed a USB drive shared as 'Storage' and limited access to 2 users 'ryan' and 'kandi'.  The user 'ryan' is able to access 'Storage' from the windows XP machine, but the user 'kandi' is not.  It gets the standard 'You might not have permission to access this resource".  Both users are listed in the smb.conf file as valid users.  I have even reset the password for user 'kandi' using smbpasswd -a command.  I have searched all over the place and all info I have found only pertains to no user being able to access samba shares. 
Thanks for your help!

---

### Post by luvshines on 2010-12-12
Can you post output of following:
```
testparm -s

# Also long listing of shared path
ls -l <shared-path>
```

---

### Post by atomictaco on 2010-12-12
> **luvshines said:**
> Can you post output of following:
```
testparm -s

# Also long listing of shared path
ls -l <shared-path>
```

testparm -s:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ZIPPY
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
	read only = No
	guest ok = Yes

[Storage]
	path = /media/Storage
	valid users = kandi, ryan
	read only = No

ls -l:

ryan@remmy:/media$ ls -l
total 32
lrwxrwxrwx 1 root root     7 2010-12-10 20:48 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2010-12-10 20:48 floppy0
drwx------ 1 ryan ryan 28672 2010-12-12 13:44 Storage

---

### Post by luvshines on 2010-12-12
> **atomictaco said:**
> testparm -s:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ZIPPY
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

[Storage]
	path = /media/Storage
	valid users = kandi, ryan
	read only = No

ls -l:

ryan@remmy:/media$ ls -l
total 32
lrwxrwxrwx 1 root root     7 2010-12-10 20:48 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2010-12-10 20:48 floppy0
drwx------ 1 ryan ryan 28672 2010-12-12 13:44 Storage

Ok, so if Storage is owned by ryan alone and others don't have even the read access, I doubt if kandi will be able to access it

---

### Post by CharlesA on 2010-12-12
> **luvshines said:**
> Ok, so if Storage is owned by ryan alone and others don't have even the read access, I doubt if kandi will be able to access it

Yep.

Can you either add them to the 'ryan' group and change the permissions on Storage to 750 or change the permissions on Storage to 775.

---

### Post by Morbius1 on 2010-12-12
> [Storage]
    path = /media/Storage
    valid users = kandi, ryan
    read only = No>  drwx------ 1 ryan ryan 28672 2010-12-12 13:44 Storage     @luvshines, you must be having a bad day. It's probably because you never sleep ;)

"read only = No" means that samba will allow both users write access. The problem is that ryan is the only one that has access ( I'm guessing it's an NTFS partition ). 

One solution is to make everyone look like ryan:
> [Storage]
     path = /media/Storage
     valid users = kandi, ryan
     read only = No
[COLOR=Blue]force user = ryan[/COLOR]
[COLOR=Blue][B]
EDIT:[/B][/COLOR] CharlesA, didn't see your post when I hit enter. Everytime I see permissions of 0700 on something I always jump to the conclusion that it's an NTFS partition because that's how it mounts without an fstab entry. Sorry.

---

### Post by atomictaco on 2010-12-12
> **CharlesA said:**
> Yep.

Can you either add them to the 'ryan' group and change the permissions on Storage to 750 or change the permissions on Storage to 775.

What is the best option?  I don't mind changing the owner or group of the drive either, that is just what it configured itself as when I plugged it in to this computer.  I do not want user 'kandi' to have access to the home file for user 'ryan'.  'Storage' is meant to just be a catch all and storage for items that will be used by multiple computers, hence the Samba share.

---

### Post by CharlesA on 2010-12-12
> **atomictaco said:**
> What is the best option?  I don't mind changing the owner or group of the drive either, that is just what it configured itself as when I plugged it in to this computer.  I do not want user 'kandi' to have access to the home file for user 'ryan'.  'Storage' is meant to just be a catch all and storage for items that will be used by multiple computers, hence the Samba share.

force user would work best in that case.

Good catch on that Morbius..

;)

---

### Post by atomictaco on 2010-12-12
> **Morbius1 said:**
> @luvshines, you must be having a bad day. It's probably because you never sleep ;)

"read only = No" means that samba will allow both users write access. The problem is that ryan is the only one that has access ( I'm guessing it's an NTFS partition ). 

One solution is to make everyone look like ryan:

[COLOR=Blue][B]
EDIT:[/B][/COLOR] CharlesA, didn't see your post when I hit enter. Everytime I see permissions of 0700 on something I always jump to the conclusion that it's an NTFS partition because that's how it mounts without an fstab entry. Sorry.

Yes it is ntfs, it was originally setup on a Windows box.

---

### Post by CharlesA on 2010-12-12
> **Morbius1 said:**
> 
[COLOR=Blue][B]
EDIT:[/B][/COLOR] CharlesA, didn't see your post when I hit enter. Everytime I see permissions of 0700 on something I always jump to the conclusion that it's an NTFS partition because that's how it mounts without an fstab entry. Sorry.

That's fine. You probably know more about how stuff is mounted by default then I do. :)

@atomictaco: Since it's NTFS, the force user option will probably be the easiest way to go.

---

### Post by atomictaco on 2010-12-12
'force user' worked now she can access her pictures stored on the drive.

Thanks guys, you are awesome!  I figured someone would chime in with some suggestions, but didn't think I would have it fixed in less than 30 min.

---

### Post by Morbius1 on 2010-12-12
Removed post.

---

### Post by CharlesA on 2010-12-12
Don't forget to mark the thread as solved from thread tools. :)

---

### Post by atomictaco on 2010-12-12
> **CharlesA said:**
> Don't forget to mark the thread as solved from thread tools. :)

Should be done.  Thanks!

---

### Post by atomictaco on 2010-12-12
> **Morbius1 said:**
> Removed post.

Morbius, what was the 'gksu' in the post you removed?  Is it like 'sudo'?

---

### Post by CharlesA on 2010-12-12
> **atomictaco said:**
> Morbius, what was the 'gksu' in the post you removed?  Is it like 'sudo'?
It's used for running graphical apps with sudo rights.

---

