---
title: "password areas greyed out"
date: 2011-05-28
forum: General Help
---

### Post by ve3rpm on 2011-05-28
It doesn't matter where I go that requires a password, it won't allow me to enter.  Password works fine in the terminal though.  Any thoughts?
Oh it's ubuntu 11.04

---

### Post by ram0042 on 2011-05-28
> **ve3rpm said:**
> It doesn't matter where I go that requires a password, it won't allow me to enter.  Password works fine in the terminal though.  Any thoughts?
Oh it's ubuntu 11.04
Check you keyrings and you may want to delete them and re-enter their passwords

---

### Post by ve3rpm on 2011-05-28
There is no password on the keyring.

---

### Post by ram0042 on 2011-05-28
> **ve3rpm said:**
> There is no password on the keyring.
So it is at the Ubuntu's password fields only and not, let's say, Firefox?

---

### Post by ve3rpm on 2011-05-28
I can't even do the listed updates.  It's very strange.  Can't get into users and groups etc.

---

### Post by ram0042 on 2011-05-28
> **ve3rpm said:**
> I can't even do the listed updates.  It's very strange.  Can't get into users and groups etc.
Are you the Administrator. if not, try to activate the root account via terminal
```
sudo passwd root
```
and log in as root

---

### Post by dnairb on 2011-05-28
A normal user should be able to enter passwords in the authentication dialog. As the OP stated, doing so in terminal works OK.

OP: can you provide a screenshot of the authentication dialog box?

---

### Post by dnairb on 2011-05-28
Just realised: print screen won't work while a password authentication box is open.

Another thought: are you using an on-screen keyboard perhaps?

---

### Post by ve3rpm on 2011-05-30
No, an actual wired keyboard... At the point where I'm tempted to just reload.

---

### Post by herderianer on 2011-09-25
This information might be outdated, but removing the fingerprint gui solved my problem wird grayed out password areas.

If you don't know how to remove fingerprintgui:

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage#Removal](http://knowledge76.com/index.php/Fingerprint_Reader_Usage#Removal)

kind regards

---

