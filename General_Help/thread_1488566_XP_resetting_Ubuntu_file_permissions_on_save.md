---
title: "XP resetting Ubuntu file permissions on save"
date: 2010-05-20
forum: General Help
---

### Post by kazbryan on 2010-05-20
Hi all,

Quick question for you. I've been using Ubuntu for a while now, and have it working as a local web server so I can test PHP developments without additional strain on my XP box. I've networked the XP machine and my Ubuntu box together, and have set up Samba so that I can file share in both directions. Everything had been working wonderfully for a couple of weeks, but recently (in the last couple of days) I've been getting problems whenever I save a file from my XP machine to the Ubuntu box. For some reason the access permissions are being reset on save, only allowing access for the owner with no access at all for the group and others. This means that every time I amend a web page, or an image, I have to reset the permissions through Ubuntu. I have no idea what's been changed or updated in the last few days, and wondered if anyone can recommend a fix, as this is getting very annoying!

My systems are as follows:

Windows XP Home SP3, AMD 3400+ 2.19Ghz, 448MB RAM
Ubuntu 9.10 (Karmic), Gnome 2.28.1, Kernel 2.6.31-21-generic, AMD 3200+ 2Ghz, 496MB RAM

Thanks in advance!

---

### Post by Morbius1 on 2010-05-20
Can you post your share definitions:

```
net usershare info
testparm -s
```

---

### Post by kazbryan on 2010-05-25
I get the following info:

[ubuntu_web]
path=/var/www
comment=
usershare_acl=Everyone:F,
guest_ok=n

[business docs]
path=/home/karen/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

---

### Post by Morbius1 on 2010-05-25
You didn't provide the output of "testparm -s" so I don't know if there is a conflict between the two different methods of sharing folders with Samba - Nautilus-share and Classic-share.

Based only on the info you posted I would say it's working as designed. Your shares require authentication and anything saved by that remote user will be saved with him as owner. Again, not knowing if you have any Classic-shares defined in smb.conf then I would suggest the following:

Add the following line to the [COLOR=Blue][global] [/COLOR]section of smb.conf:
```
force user = karen
```Then restart samba. Depending on what version of Ubuntu you're using it's either:
```
sudo service samba restart
```OR
```
sudo restart smbd
sudo restart nmbd
```When the remote user saves anything it will be be converted to owner=karen.

---

### Post by kazbryan on 2010-05-25
Sorry, I think I was being rather dense when using the commands! 

Is this what you were after from the testparm -s?

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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by kazbryan on 2010-05-25
> **Morbius1 said:**
> 
Add the following line to the [COLOR=Blue][global] [/COLOR]section of smb.conf:
```
force user = karen
```Then restart samba. Depending on what version of Ubuntu you're using it's either:
```
sudo service samba restart
```OR
```
sudo restart smbd
sudo restart nmbd
```When the remote user saves anything it will be be converted to owner=karen.

Thanks Morbius1, that seems to have done the trick :)

---

