---
title: "Can't type"
date: 2011-03-26
forum: General Help
---

### Post by ex_isp on 2011-03-26
8 month old install, been running solid.  Kernal 2.6.32-21-generic.  Gnome 2.30.2

Keyboard works, system will let me type my password and login.  Once GUI load, keystrokes are no longer accepted.  Mouse and menus work, just can't type anymore.

Ideas?

Thanks in advance!

Ex

---

### Post by alegomaster on 2011-03-26
Did you try a complete reboot of the system yet?

---

### Post by ex_isp on 2011-03-26
Yes   several times.  Also tried previous kernal and dpkg repair from command line.  Only in GUI does keyboard fail

Also, once in GUI, can't turn off numlock etc.

---

### Post by alegomaster on 2011-03-26
This once happened to me when using a live disc on a friends laptop recently so I turned off the computer and reloaded the disc and that fixed the problem. Perhaps you need to do a fresh install, or get a virtual keyboard.

Edit: your keyboard probably lost connection with the computer. Can you just check if "stdin" is inside the /dev folder.

---

### Post by ex_isp on 2011-03-26
Yes, stdin file is in /dev

do you know how to make new user from cmd line?  then i could still access the files I need to save

I thinking this is just acct corruption...

---

### Post by BrandonC19 on 2011-03-26
To make a new user on the command line type:
```
sudo useradd admin newuser
``````
sudo passwd newuser
```
Obviously change "newuser" to the UserName of your choice.

---

### Post by ex_isp on 2011-03-26
> **BrandonC19 said:**
> To make a new user on the command line type:
```
sudo useradd admin newuser
``````
sudo passwd newuser
```Obviously change "newuser" to the UserName of your choice.

Can only get to working command line in "safe mode" and is then asking for root password.  Not accepting sudo or my passwd

thoughts?

Or how to stop GUI from loading on normal boot?

---

### Post by ex_isp on 2011-03-26
Got it!  I'm in with new acct that's working and has admin perms.

Thanks so much for your help!   :)

---

### Post by linuxuser12345 on 2011-03-26
Have you tried using a different keyboard and mouse set? Sometimes what seems like the most difficult problems are fixed by the easiest things.

---

### Post by ex_isp on 2011-03-26
> **linuxuser12345 said:**
> Have you tried using a different keyboard and mouse set? Sometimes what seems like the most difficult problems are fixed by the easiest things.


Keyboard is working fine in new acct.  Something had just fallen apart in old one   New acct solved prob

copied required files to new acct with cp -r...  did chown -R   all is working

Thanks   got it!

---

### Post by BrandonC19 on 2011-03-29
Congrats, glad I could help.

---

