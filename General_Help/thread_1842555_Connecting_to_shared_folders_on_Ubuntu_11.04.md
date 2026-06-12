---
title: "Connecting to shared folders on Ubuntu 11.04"
date: 2011-09-11
forum: General Help
---

### Post by stephenconnolly on 2011-09-11
I have an old dell desktop running Ubuntu 11.04, I also have  samba installed on it. I'm trying to access the shared folders on the Ubuntu machine from my  Mac Book Pro, so I go into 'Finder', click on 'Go' and 'Connect to Server'.


  I type in the IP address of the Ubuntu machine 'smb://xxx.xxx.x.xx' and  click connect, I can then see the list of shared folders from the Ubuntu machine so I know its making a connection. But when I try to access the  'music' folder for example, I get an error message stating:


  There was an error connecting to the server "xxx.xxx.x.xx". Check the server name or IP address, and try again.
    
I have a external hard drive attached to the server, and the folders I'm  trying to access are located on that external hard drive. The location  of the folder is /media/HD-CELU2/music, so I think the path from Finder  should be smb://xxx.xxx.x.xx/media/HD-CELU2/music, but having tested  this, I'm still not getting in.


Any thoughts anyone ?

---

### Post by Kirboosy on 2011-09-11
You could try to "connect to server" in Ubuntu.
Open up nautilus and hit File-->Connect to Server. Set the Service Type to Windows Share and enter in all the information. Make sure you enter the Mac credentials and not the Ubuntu ones. (Unless they are exactly the same ;) )

Let me know if that helps any.


~Caboose

---

### Post by stephenconnolly on 2011-09-13
Thanks Caboose, I don't think I explained myself very well. 

I'm trying to access the shared folders on the Ubuntu machine from my mac book pro. 

I've edited the post accordingly.

---

### Post by Morbius1 on 2011-09-13
To answer this question correctly we would need to know how you created the share:
```
testparm -s
net usershare info --long
```And what the permissions at the target are:
```
ls -al /media/HD-CELU2
```

---

### Post by stephenconnolly on 2011-09-13
testparm -s
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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


```net usershare info --long
```

info_fn: file /var/lib/samba/usershares/all downloads is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/mairead pictures is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[mairead pics]
path=/media/HD-CELU2/Pictures/Mairead Pics
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/all music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[media]
path=/media/HD-CELU2/SHARE
comment=
usershare_acl=Everyone:F,
guest_ok=y

[music]
path=/media/HD-CELU2/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[test]
path=/media/HD-CELU2/test
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/mairead documents is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/stephen documents is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[downloads]
path=/home/stephen/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/all videos is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[stephen pics]
path=/media/HD-CELU2/Pictures/Stephen Pics
comment=
usershare_acl=Everyone:F,
guest_ok=y

[mairead docs]
path=/home/stephen/Documents/Mairead Docs
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/test music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[video]
path=/media/HD-CELU2/Video
comment=
usershare_acl=Everyone:F,
guest_ok=y

[stephen docs]
path=/home/stephen/Documents/Stephen Docs
comment=
usershare_acl=Everyone:F,
guest_ok=y

```ls -al /media/HD-CELU2
```

total 389540
drwx------  17 stephen stephen     32768 2011-09-10 16:16 .
drwxr-xr-x   4 root    root         4096 2011-09-05 20:46 ..
drwx------   2 stephen stephen     32768 2011-05-14 14:06 Kittys Photos
drwx------ 450 stephen stephen     65536 2011-01-20 21:26 Music
drwx------   4 stephen stephen     32768 2011-01-09 17:13 Pictures
drwx------   2 stephen stephen     32768 2011-05-14 12:23 $RECYCLE.BIN
drwx------   2 stephen stephen     32768 2007-12-31 23:00 Recycled
drwx------   3 stephen stephen     32768 2008-03-16 05:38 SHARE
drwx------   2 stephen stephen     32768 2011-01-09 18:39 Shared
-rw-r--r--   1 stephen stephen       596 2008-03-23 07:36 SMBACCT.CFG
drwx------   3 stephen stephen     32768 2011-06-27 20:33 .Spotlight-V100
drwx------   5 stephen stephen     32768 2009-10-20 14:17 System Volume Information
drwx------   2 stephen stephen     32768 2011-09-10 16:16 test
drwx------   4 stephen stephen     32768 2011-01-09 16:38 .Trash-1000
drwx------   3 stephen stephen     32768 2011-06-27 20:33 .Trashes
-rw-r--r--   1 stephen stephen      4096 2011-06-27 20:33 ._.Trashes
drwx------   9 stephen stephen     32768 2011-02-14 17:52 Video


```

---

### Post by Morbius1 on 2011-09-13
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section under the workgroup line:
```
 force user = stephen
```Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down and try to access the share again.

Samba and Linux file permissions need to be in sync and your folders are only allowing you ( stephen ) to access them. My guess is they are an ntfs or fat32 formated partition. THe "force user" will convert the remote "guest" to you for the purposes of all those guest shares.

---

### Post by stephenconnolly on 2011-09-13
Thanks Morbius1, its working now.

---

