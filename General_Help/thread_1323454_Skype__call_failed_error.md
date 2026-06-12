---
title: "Skype  call failed error???"
date: 2009-11-11
forum: General Help
---

### Post by JimHebert on 2009-11-11
I am using the recently downloaded version of Ubuntu 8.1 since I figured any bugs would have been wiped out by now. However, Skype, keeps giving call failed. Synaptic offered skype and skype tools which I downloaded both. A popup said contact the forum community. So here I am.

---

### Post by Giblet5 on 2009-11-11
I was never able to get Skype 2.0+ to work under Intrepid.

I discovered that by installing an older version, it worked well enough.

Try installing skype-1.4.0.74.deb from their [old versions site]("https://developer.skype.com/Download/OldVersionsCopy#head-7c4e795cc1b9fb9c9cf168eff27098d80432e0eb").

Remove skype via ```
sudo apt-get remove skype
```

Then install the older version via ```
dpkg -i skype-1.4.0.74.deb
```

You'll get pestered a lot about updating it by Update Manager, but if you DO update it, it will break again.

---

### Post by JimHebert on 2009-11-13
I tried entering that code and got the following:

jimhebert@jimhebert-desktop:~$ sudo apt-get remove skype
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jimhebert@jimhebert-desktop:~$

---

### Post by Giblet5 on 2009-11-13
You can't run dpkg or apt if update manager or synaptic package manager are open.

Close those first.

Only one apt command (update manager, synaptic, the apt-get command, dpkg, etc) can be in use at any one time.

---

### Post by JimHebert on 2009-11-14
I entered  

dpkg -i skype-1.4.0.74.deb


Said I needed superuser privileges.


I entered the following:


jimhebert@jimhebert-desktop:~$ sudo dpkg -i skype-1.4.0.74.deb
dpkg: error processing skype-1.4.0.74.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-1.4.0.74.deb
jimhebert@jimhebert-desktop:~$

---

### Post by JimHebert on 2009-11-14
I've got the problem solved.

---

