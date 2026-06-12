---
title: "Vuze constantly tries to update"
date: 2009-07-31
forum: General Help
---

### Post by Clove7 on 2009-07-31
For anyone that uses the vuze torrent client, has anyone ever run into the problem that it always tries to update it's self to it's current version? I can't figure out why, and haven't been able to find much on the subject but this happened to me both in debian and ubuntu.

---

### Post by kcbnac on 2009-08-04
I just hit this as well.

Just installed Vuze/Azureus, 

Running Jaunty, 32-bit, i386.  Ran the initial update, had two things to update - accepted that, it wanted a restart I gave it one - and it keeps looping on the update for 2.4.0.4.  Attempted running via 'sudo azureus %f' (Same as the shortcut, except as root) and got the same looping.

---

### Post by philinux on 2009-08-04
Disable the feature in prefs.

---

### Post by mbauwens on 2009-09-12
I have the same probem (4.2.0.8), even if feature disabled in prefs. Any idea?

specs: iMac 24/2.16 - Os/x 10.6 (snow leopard)

---

### Post by dumblebee100 on 2009-09-12
Why dont u try deluge client for linux 

Im using that from a long time ..and I didnt face any problem as such

---

### Post by stuart221 on 2009-10-16
This is how I solve the problem. Open terminal type in sudo nautilus hit enter. using nautilus go to file system usr/share/vuze right click properties then permissions make every box create and delete file. Close nautilus. I hope this helps.

---

### Post by andoni on 2009-10-17
> **stuart221 said:**
> This is how I solve the problem. Open terminal type in sudo nautilus hit enter. using nautilus go to file system usr/share/vuze right click properties then permissions make every box create and delete file. Close nautilus. I hope this helps.
Thanks, I've just finally updated Vuze by doing that.

Greetings.

---

### Post by stuart221 on 2009-10-18
Good to hear remember to mark it as solved 
Cheers

---

### Post by Dubbayoo on 2009-10-18
> **stuart221 said:**
> This is how I solve the problem. Open terminal type in sudo nautilus hit enter. using nautilus go to file system usr/share/vuze right click properties then permissions make every box create and delete file. Close nautilus. I hope this helps.

I don't even have that directory. It's also not in the list of installed Vuze files:

/.
/usr
/usr/bin
/usr/bin/vuze
/usr/share
/usr/share/doc
/usr/share/doc/vuze
/usr/share/doc/vuze/copyright
/usr/share/doc/vuze/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/vuze.1.gz


What's in it?

---

### Post by stuart221 on 2009-10-20
make /usr/share/man/man1/vuze.1.gz create and delete file see if that work or uninstaller vuze then download from getdeb.net then see if you have  this directory and Open terminal type in sudo nautilus hit enter. using nautilus go to file system usr/share/vuze right click properties then permissions make every box create and delete file. Close nautilus. I hope this helps 

Cheers

---

