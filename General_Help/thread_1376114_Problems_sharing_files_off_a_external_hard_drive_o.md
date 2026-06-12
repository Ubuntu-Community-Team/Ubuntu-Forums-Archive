---
title: "Problems sharing files off a external hard drive over a network"
date: 2010-01-08
forum: General Help
---

### Post by blakep2 on 2010-01-08
when I try to share files off of my external hard drive over my network; it says it is shared on my ubuntu machine but when I try to access the file on my windows machine it says I do not have permission.

---

### Post by Joeb454 on 2010-01-08
Thread moved to General Help :)

How did you enable the sharing on the Ubuntu machine?

It sounds like it's either configured incorrectly, or samba isn't installed, though unfortunately, I won't be able to help there, sorry.

---

### Post by LinuxRules1 on 2010-01-08
make sure the folder you are sharing has 777 permissions. that might be whats causing your problem.

---

### Post by blakep2 on 2010-01-08
joeb454: I enabled sharing using samba,  i am trying to acess the files on the windows computer, under the work groups i see the ubuntu machine and i see the folder but when i click it; it says i dont have permission

linuxrules1: how do i enable 777 permissions

---

### Post by blakep2 on 2010-01-08
if helps any i am running ubuntu 8.10

---

### Post by LinuxRules1 on 2010-01-10
> 
linuxrules1: how do i enable 777 permissions

```
chmod 777 /path/folder
```

---

### Post by blakep2 on 2010-01-10
i  got this
chmod: cannot access `/path/folder': No such file or directory

---

### Post by mk1w86 on 2010-01-10
> i got this
chmod: cannot access `/path/folder': No such file or directory 

Run chmod 777 on the folder you want to share.
e.g. Say I wanted to change permissions for the store folder in /mnt I would run:

```
sudo chmod 777 /mnt/store/
```

---

### Post by blakep2 on 2010-01-10
now i got this
chmod: cannot access `/media/SEA_DISC/Peterman': No such file or directory
chmod: cannot access `Files': No such file or directory

---

### Post by LinuxRules1 on 2010-01-10
it will be easier if you go to the directory then change the permissions of the folder in that directory.

to change directory

```
cd /media/SEA_DISC
```

then change the permissions

```
sudo chmod 777 Peterman
```

---

### Post by blakep2 on 2010-01-10
and this
chmod: cannot access `Peterman': No such file or directory

---

### Post by Morbius1 on 2010-01-10
Is the external hard drive formatted in fat32 or ntfs?

Also, please post the output of the following commands:
[B]
net usershare info
testparm -s[/B]

---

### Post by LinuxRules1 on 2010-01-10
the folder names are case sensitive so make sure the case of you letters are correct. it's either that or the folder you want to share doesn't exist.

---

### Post by blakep2 on 2010-01-10
linuxrules 1: the whole 777 thing worked but it still is saying the same thing when i try to access the folder from the windows machine
morbius1: fat 32

---

### Post by Morbius1 on 2010-01-10
chmod won't work on a windows filesystem.

> Also, please post the output of the following commands:
[B]
net usershare info
testparm -s[/B]

---

### Post by blakep2 on 2010-01-10
[blake's files]
path=/media/SEA_DISC/Blake's Files
comment=
usershare_acl=Everyone:F
guest_ok=y

[peterman server]
path=/home/blake/Documents/Peterman Server
comment=
usershare_acl=Everyone:F
guest_ok=y

[peterman]
path=/media/SEA_DISC/Petermanfiles
comment=
usershare_acl=Everyone:F
guest_ok=y

info_fn: file /var/lib/samba/usershares/screen shot is not a well formed usershare file.
info_fn: Error was Path is not a directory.

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = PETERMANNET
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
    invalid users = root

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = Ubuntu File Server Share
    path = /media/SEA_DISC/Petermanfiles
    read only = No
    create mask = 0755
    guest ok = Yes

---

### Post by Morbius1 on 2010-01-10
We're almost there.

Are you mounting this external drive through fstab?

If it's through fstab then I need to see it:

[B]cat /etc/fstab.
[/B]
If you auto mounting it by just plugging it in , let me know please

---

### Post by blakep2 on 2010-01-10
Automounting

---

### Post by Morbius1 on 2010-01-10
The fix is easy but I need to know your current setup.

Right now you have nautilus-shares set up:
> [blake's files]
path=/media/SEA_DISC/Blake's Files
comment=
usershare_acl=Everyone:F
guest_ok=y

[peterman server]
path=/home/blake/Documents/Peterman Server
comment=
usershare_acl=Everyone:F
guest_ok=y

[peterman]
path=/media/SEA_DISC/Petermanfiles
comment=
usershare_acl=Everyone:F
guest_ok=yEvery time a remote user writes to those shares it's saved with the owner set to "nobody" which means that "blake" can't write to them. Is that what you want?

---

### Post by blakep2 on 2010-01-10
I'm trying to access the files on a windows xp machine but when I try to access the files it says I don't have permission

---

### Post by Morbius1 on 2010-01-10
(1) Get rid of the "Classic Samba" share in smb.conf:

> [share]
comment = Ubuntu File Server Share
path = /media/SEA_DISC/Petermanfiles
read only = No
create mask = 0755
guest ok = Yes(2) Add **force user = blake** to the [COLOR=Blue][global][/COLOR] section of smb.conf

(3) Restart the samba service: [B]sudo service samba restart.
[/B]

---

### Post by blakep2 on 2010-01-10
i dont see add force user

---

### Post by Morbius1 on 2010-01-10
You need to add the following line to the [global] section. it's not there yet:

```
force user = blake 
```

---

### Post by blakep2 on 2010-01-10
It's there

---

### Post by Morbius1 on 2010-01-10
Save the smb.conf file

Then Open a Terminal and type: 

**sudo service samba restart**

Then see if you can access the share from Windows

---

### Post by blakep2 on 2010-03-11
i know it has been a while but i got to work a while ago and forgot my password, but i upgraded and had the same problem and followed the steps here and it works now thank you very much sorry for not responding.

---

