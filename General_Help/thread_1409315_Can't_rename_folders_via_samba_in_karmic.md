---
title: "Can't rename folders via samba in karmic"
date: 2010-02-17
forum: General Help
---

### Post by pdanders on 2010-02-17
Hi all,

I'm experiencing an odd problem under karmic where I can create and delete folders via Samba from an XP box, but I can not rename folders.  I get an "acccess denied" message.

I've been using linux and samba for years and I've never seen anything like this.

My samba configuration is quite simple..... I'm wondering if this is a bug.

[global]
        workgroup = HOUSE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins server = 192.168.10.5
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[VIDEO]
        comment = Video share on Custodian
        path = /archive/VIDEO
        read list = user
        write list = petea, shan
        force group = house
        read only = No
        create mask = 0775
        directory mask = 0775

Samba version is 3.4
Kernel version is 2.6.31-17-server x86_64

All files are owned by me and permissions are set to 775 (I even have a cron script that periodically goes in and sets the permissions just in case)

One thing that I did notice is that if I right-click on files/folders in my shares from XP the "read only" box is checked (but greyed)...


Any ideas out there?

---

### Post by pdanders on 2010-02-17
Seems that I can't rename on either Windows or OSX

---

### Post by jamesisin on 2010-02-17
I would look into the permissions on the share then.  You may have given create rights but denied modify rights.

---

### Post by pdanders on 2010-02-17
I think I finally fixed it!

I added the setting:

map readonly = permissions

to one of my shares and I can now rename files (at least in a few tests)

how odd... never had to add that before

---

### Post by jamesisin on 2010-02-17
This is in Samba then?

(Probably you want to mark this thread as SOLVED in Thread Tools above.)

---

