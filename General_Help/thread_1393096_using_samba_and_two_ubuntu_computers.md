---
title: "using samba and two ubuntu computers?"
date: 2010-01-28
forum: General Help
---

### Post by axima on 2010-01-28
i have two computers running ubuntu 9.10 64 bit and i would like to share files between them. how can do this with samba? is there a easy step by step guide? 

one of the computers also has a dvd writer, is it possible that i be able to control the dvd drive from the other computer? i want to be able to see the drive on the other computer that does not have a drive.

---

### Post by Iowan on 2010-01-28
Samba is certainly an option - but for Ubuntu-Ubuntu, [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is another alternative.

---

### Post by axima on 2010-01-28
> **Iowan said:**
> Samba is certainly an option - but for Ubuntu-Ubuntu, [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is another alternative.

can i run nfs and samba at the same time? the rest of the house is running windows and i assume i will need samba for sharing with them.

---

### Post by axima on 2010-01-30
is it difficult to set up a share folder between ubuntu and windows vista and xp?

---

### Post by Morbius1 on 2010-01-30
There are two completely different ways to share directories in Ubuntu - Gnome. Here is the easiest way ( Nautilus-share ):

Open Nautilus and right click on , for example, your /home/username/Documents folder.

Select "Sharing Options" > Click on all three boxes > Select "Create Share"

---

### Post by axima on 2010-01-30
this works perfectly, thanks

---

### Post by axima on 2010-01-30
> **Morbius1 said:**
> There are two completely different ways to share directories in Ubuntu - Gnome. Here is the easiest way ( Nautilus-share ):

Open Nautilus and right click on , for example, your /home/username/Documents folder.

Select "Sharing Options" > Click on all three boxes > Select "Create Share"

i am getting a lot of permission denied errors for some files now

---

### Post by Morbius1 on 2010-01-31
If it's a permissions denied error it may be a linux file permissions problem and not a samba problem. Post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **ls -dl /path-to-shared-folder**

On the last command: For example, if you shared /home/morbius/Documents, the command would be ls -dl /home/morbius/Documents.

If I'm right and it's a linux file permissions problem there is an easy fix.

---

### Post by axima on 2010-01-31
Here is the output
>    	 	 	 	 	 	   
 axima@axima-desktop:~$ net usershare info 
 [a2] 
 path=/home/axima/Desktop/A2 
 comment= 
 usershare_acl=Everyone:F, 
 guest_ok=y 
  
 info_fn: file /var/lib/samba/usershares/a234 is not a well formed usershare file. 
 info_fn: Error was Path is not a directory. 
 axima@axima-desktop:~$ testparm -s 
 Load smb config files from /etc/samba/smb.conf 
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
 	browsable = No 
  
 [print$] 
 	comment = Printer Drivers 
 	path = /var/lib/samba/printers 
 axima@axima-desktop:~$ ls -dl /home/axima/Desktop/A2 
 drwxrwxrwx 2 axima axima 4096 2010-01-30 20:15 /home/axima/Desktop/A2 
 

---

### Post by Morbius1 on 2010-01-31
This:
> [a2] 
 path=/home/axima/Desktop/A2 
 comment= 
 usershare_acl=Everyone:F, 
 guest_ok=y And this:
> ls -dl /home/axima/Desktop/A2 
 drwxrwxrwx 2 axima axima 4096 2010-01-30 20:15 /home/axima/Desktop/A2                       Look correct and yet:
> i am getting a lot of permission denied errors for some files now     Here's my guess. A guest is copying a file over to /home/axima/Desktop/A2 but the local user **axima** can't write to the file because the owner is literally "nobody" with a group "nogroup".

If I'm right then for the files that are already there you need to run the following command in a Terminal:
**sudo chown -R ****axima:****axima **[B]/home/axima/Desktop/A2

[/B]For a permanent fix for future copies:

Open **Terminal**
Type [B]gksu gedit /etc/samba/smb.conf
[/B]
Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = axima
```Save the file, exit gedit, and back in the terminal issue the following command: [B]sudo service samba restart
[/B]

---

### Post by axima on 2010-02-01
I will try and test this out when i have something to transfer

---

