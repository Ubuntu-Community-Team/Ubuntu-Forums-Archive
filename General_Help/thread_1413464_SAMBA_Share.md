---
title: "SAMBA Share"
date: 2010-02-22
forum: General Help
---

### Post by theozzlives on 2010-02-22
how do you setup a Samba share from the CLI?

---

### Post by Telengard C64 on 2010-02-22
Short answer:

```
sudo apt-get install samba
cd /etc/samba
sudo cp -iv smb.conf smb.ORIGINAL.conf
sudo nano smb.conf
```

Edit the workgroup variable to match the workgroup you'd like the server to join.

```
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP
```

Add at least one share definition or enable the default *HOMES* share.

```
#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

```


Longer answers:

[HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums:](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

[Samba - Community Ubuntu Documentation:](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by theozzlives on 2010-02-22
I just want to share /var/www (for web editing), and /home/ozzie/sdb (for backup reasons). There's gotta be a simple way.

---

### Post by theozzlives on 2010-02-22
Nevermind, I figured it out on my own, as usual.

---

