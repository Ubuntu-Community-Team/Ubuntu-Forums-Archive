---
title: "Can't connect to samba share"
date: 2004-10-23
forum: General Help
---

### Post by BlackMac on 2004-10-23
I've got the following smb.conf on my ubuntu box:

```
[Home]
comment = My Home
path = /home/blackmac/
valid users = blackmac
writeable = yes
write list = blackmac
hide dot files = no
```

I can't connect from my Mac. I get a list of available shares [Home], but when I enter the password and username my computer sais those are invalid. I try to connect from Mac OS X, maybe that's got something to do with it ;)

Thanks Stefan

EDIT:
I also tried connecting with Windows XP now (VPC) - It requests the Username and password over and over again (seems to be invalid) - when I enter blackmac as the username the next dialog asking contains "LOCALHOST\blackmac" as preset in the user field.

---

### Post by idioteque on 2004-10-23
did U install smbsf ??

this is not installed by default

---

### Post by BlackMac on 2004-10-23
Yes I did.

I added "encrypt passwords = no" to the global part of smb.conf. Now it works (and I can live with the lowered security)

---

### Post by butters on 2004-10-23
you most likely forgot to do:

smbpasswd -a blackmac

This adds a username/password entry in samba's password database.  Then you can turn encrypt passwords back on.

You don't need smbfs support to run a samba server.  You only need it to mount samba shares.  And it is compiled as a module in the default ubuntu kernel.

A GNOME shares/mounts manager would be nice... they have this beautiful gnome-vfs layer and yet hardly leverage it.  The connect to server feature sucks, too.  It won't remember my settings for mounts and there's no way to automount at login.  The only sure-fire way to manage mounts and shares is through fstab and smb.conf, which is rather embarassing given how simple this would be to code.

---

