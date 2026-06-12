---
title: "samba stalls?"
date: 2010-01-30
forum: General Help
---

### Post by Tourdog on 2010-01-30
I am trying to link my desktop "Karmic" up to an XP laptop "homegroup" for file sharing.   Both computers are on my wifi served by a router.

The following plugins were installed via Synaptics:

smb client             2:3.4.0-3ubuntu5.4
python-smbc         1.0.6-0ubuntu2
libpam-smbpass    2.3.4.0-3ubuntu5.4
libwbclienst0               "
samba-common-bin     "
sambadoc                   "  
samba                        "
samba common           "
system-config-smba  1.2.63-ubuntu4

Initially clicking on "samba" brings this up:
"warning: some lines couldn't be understood while reading the  configuration file  /etc/samba/smb.conf.  these may be unknown  configuration directives samba plugins but could also be configuration  errors."

You ignore the warning and continue on.  The results are a static "samba server  menu" accepting what you type ...but doing nothing with it upon pressing OK.

Do I need to delete 1 or > of the downloads from synaptics or am I  missing 1?
What is my next step?     :)

TIA !

---

### Post by Tourdog on 2010-01-30
tourdog@PJK3:~$ dpkg -l | grep samba


ii  samba                                 2:3.4.0-3ubuntu5.4                                            SMB/CIFS file, print, and login server for U

ii  samba-common                          2:3.4.0-3ubuntu5.4                                             common files used by both the Samba server a

ii  samba-common-bin                      2:3.4.0-3ubuntu5.3                                            common files used by both the Samba server a

ii  samba-doc                             2:3.4.0-3ubuntu5.4                                              Samba documentation

ii  system-config-samba                   1.2.63-0ubuntu4                                                GUI for managing samba shares and users

tourdog@PJK3:~$ 


Doesn't seem the extra files should be a problem.  Or?

---

### Post by cariboo on 2010-01-30
Open a terminal and type:

```
testparm
```

This will point out any errors you have in /etc/samba/smb.conf.

I just setup Win 7 in a vm, make sure both computers are in the same workgroup, or you aren't going to be able to access your Ubuntu computer from Windows.

---

### Post by Tourdog on 2010-01-30
cariboo907,

I am on it now................   thank you !   :D

---

