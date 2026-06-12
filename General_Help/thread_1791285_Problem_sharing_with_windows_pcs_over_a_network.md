---
title: "Problem sharing with windows pcs over a network"
date: 2011-06-26
forum: General Help
---

### Post by Newcombe on 2011-06-26
I'm trying to get a pc running xubuntu to share with a few pc's running windows vista & 7.  Right now the xubuntu pc can read & write to the windows computers, but not vice-versa.  Any suggestions?

---

### Post by Toz on 2011-06-26
To connect to Xubuntu shares you need to have samba installed on xubuntu. 

_To install:_ (using the GUI)
Open Ubuntu Software Centre and search for the package samba

_To install:_ (from the command line)
```
sudo apt-get install samba
```

You'll need to edit one file, **/etc/samba/smb.conf** to setup the shares. Have a look at the documentation here: [https://help.ubuntu.com/community/Sa...n%20-%20Manual](https://help.ubuntu.com/community/Sa...n%20-%20Manual) for more detailed information and instructions.

---

