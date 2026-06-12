---
title: "firefox plugins folder"
date: 2010-07-25
forum: General Help
---

### Post by NO_oB on 2010-07-25
Hi
when you download firefox from the website and extract it,you get a firefox folder..inside that folder you have a plugins folder..can i make firefox _only_ look for plugins on that folder:?:
because he's using the plugins on /usr/lib/mozilla/plugins..
and i need it to only look for them in the "built-in" plugins folder..

---

### Post by sundays211 on 2010-07-25
may i ask why you compile Firefox from source instead of using the .deb package

---

### Post by NO_oB on 2010-07-25
> **sundays211 said:**
> may i ask why you compile Firefox from source instead of using the .deb package


i was trying to say the one you download from the website,sorry for the mistake..

---

### Post by sundays211 on 2010-07-25
that is what compialling form source is. It is a lot easier to just type in the terminal ```
sudo apt-get install firefox
``` and everything should work exactly as it should. its just a lot easier than having to play around with settings, and possibly break everything.

---

### Post by lovinglinux on 2010-07-25
> **sundays211 said:**
> that is what compialling form source is. It is a lot easier to just type in the terminal ```
sudo apt-get install firefox
``` and everything should work exactly as it should.

What the OP did was to download the executable binaries. That's an alternative installation method and does not require compiling.

The command you gave is to install Firefox from the repositories, which is not what NO_oB. He/she wants (in fact already is) to run a different version of Firefox manually downloaded from Mozilla and get the plugins from the local installation instead of the system. 

> **NO_oB said:**
> Hi
when you download firefox from the website and extract it,you get a firefox folder..inside that folder you have a plugins folder..can i make firefox _only_ look for plugins on that folder:?:
because he's using the plugins on /usr/lib/mozilla/plugins..
and i need it to only look for them in the "built-in" plugins folder..

Have you created a symlink from the local plugin folder to /usr/lib/mozilla/plugins? If yes, simply delete it, create a new plugin folder on your local installation and put the plugins .so files there. If that doesn't work, then you can put them in your user profile plugin folder ~/.mozilla/plugins (you might need to create it).

---

### Post by NO_oB on 2010-07-25
It needs to be something done inside the firefox folder..i will install it on a pendrive,but i need the plugins inside the pendrive because i need to go to other person house and that person haves java "broken" and doesnt want to fix it lol..
Firefox is arledy running inside the pendrive (im using it now) with the profile inside the pendrive,so i only need the plugins..
The idea is connect the pendrive in the pc,start firefox,and have a working java :popcorn:

---

### Post by lovinglinux on 2010-07-25
> **NO_oB said:**
> It needs to be something done inside the firefox folder..i will install it on a pendrive,but i need the plugins inside the pendrive because i need to go to other person house and that person haves java "broken" and doesnt want to fix it lol..
Firefox is arledy running inside the pendrive (im using it now) with the profile inside the pendrive,so i only need the plugins..
The idea is connect the pendrive in the pc,start firefox,and have a working java :popcorn:

So, put the plugins in the profile and you should be fine.

---

### Post by NO_oB on 2010-07-25
That did the trick,thanks :biggrin:
Now a offtopic question lol:whats the best format to use in the pendrive? ext 2,ext 3,ext4,ntfs or reiserfs? :roll:

---

### Post by lovinglinux on 2010-07-25
> **NO_oB said:**
> That did the trick,thanks :biggrin:
Now a offtopic question lol:whats the best format to use in the pendrive? ext 2,ext 3,ext4,ntfs or reiserfs? :roll:

No idea.

---

