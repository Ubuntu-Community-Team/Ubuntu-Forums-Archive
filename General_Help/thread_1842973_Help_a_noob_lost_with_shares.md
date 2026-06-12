---
title: "Help a noob lost with shares"
date: 2011-09-12
forum: General Help
---

### Post by cerulean on 2011-09-12
I've got a share that works, let's call it "Orig share"
/home/andrew/Share

and a new share I'm trying to get to work on a second hard drive
/media/hdtwo/myshare_folder

I'm trying to access both from a windows XP machine and a windows 7 machine. I can access the orig share on both, have forever. 
I've tried for 3 hours going through a few guides to get the new share to work on windows but best I can get is error in Windows 7 and an endlessly not accepted password prompt in windows xp.

I'd love to just not require passwords.

The first thing that's odd is the original share is not marked as shared in the nautilus gui and it's not listed in /etc/samba/samba.conf. There's a file in /var/lib/samba/usershares.

I have full control of that orig share from the windows boxes (create/delete/rename).

I've tried copying the file in /var/lib/samba/usershares to create the new share and it creates a visable share but error in win7, endless password in xp when I try to open it.

I tried creating an entry in samba.conf but same response:
[MyShare]
    comment = Ubuntu File Server Share
    path = /media/hdtwo/myshare_folder
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755



I tried resetting the smbpassword to my login, no help with prompted to login in xp.

It's an Ubuntu 9.04 box, been running for years as a mythtv box.



Any help appreciated =)

---

### Post by papibe on 2011-09-12
Could you post the result of this command?
```
testparm
```
(you have to press enter for the details to be shown)

Regards.

---

### Post by cerulean on 2011-09-12
(The samba.conf code I mentioned above is not currently saved there btw.)

Here's the results:

[global]
    server string = %h server (Samba, Ubuntu)
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

---

### Post by papibe on 2011-09-12
By default the security option is set to 'user'. That means that all connections to the share are mapped to a Linux user.

Since you have spend lots of time trying to connect, try this before we change any parameter:
[INDENT]When connecting using Windows 7, use this in the dialog windows:
```
user: Ubuntu_machine_name\ubuntu_user_name
pass: your_ubuntu_password
```
[/INDENT]
Replace with the appropriate values.

Let me know how it goes,
Regards.

---

### Post by cerulean on 2011-09-12
Win7 never gives me a chance to enter uid/pass, just waits and then wants to "diagnose". I tried entering uid that way in XP and it still didn't work. Tried all variations of caps.

The original share continues to work fine in both.

---

### Post by papibe on 2011-09-12
Ok, so let's change the security to 'share':
Edit the config file:
```
$ gksudo gedit /etc/samba/smb.conf
```
Look for this line:
```
#   security = user
```
And change it for this:
```
   security = **share**
```
Save the file and close it. Restart samba:
```
$ sudo service smbd restart
```
Try again connecting from Windows 7. It may necessary to restart Windows.

Tell me how it goes,
Regards.

---

### Post by cerulean on 2011-09-13
Still no luck.

---

### Post by papibe on 2011-09-13
By any change you have the same username (but different passwords) in Windows7 than in the Ubuntu Server?

Regards.

---

### Post by cerulean on 2011-09-14
Win7 - no not the same user
XP - yes but I added another admin on the ubuntu box and it still didn't take it

---

### Post by papibe on 2011-09-14
Try creating a dedicated user for the Win7 user:
```
$ smbpasswd -a win7_username
```
When the password is asked use the win7 password.

Regards.

---

