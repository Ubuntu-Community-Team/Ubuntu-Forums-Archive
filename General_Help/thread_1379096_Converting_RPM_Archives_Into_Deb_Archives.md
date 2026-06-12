---
title: "Converting RPM Archives Into Deb Archives"
date: 2010-01-12
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-01-12
I've found a website ([http://sulphur.freshrpms.net/](http://sulphur.freshrpms.net/)) that I've downloaded Basilisk II ([http://sulphur.freshrpms.net/rpm.html?id=3](http://sulphur.freshrpms.net/rpm.html?id=3)) and SheepShaver ([http://sulphur.freshrpms.net/rpm.html?id=6](http://sulphur.freshrpms.net/rpm.html?id=6)) from, I converted both inton deb archive using the command sudo alien, but while they both successfully converted and installed, and show up in the Applications menu, only Basilisk II launches. When I click on the SheepShaver icon, nothing happens.  I had this problem with another SheepShaver RPM I downloaded elsewhere.  I really want to use SheepShaver to run Mac OS 9 on my laptop, is there something I can do to get it to run?

TIA

---

### Post by howefield on 2010-01-12
Try starting from a terminal, it might tell you what you are missing.

---

### Post by ..::| Dave89 |::.. on 2010-01-12
Typed SheepShaver into the terminal, this is what I got:

dave2389@dave2389-laptop:~$ SheepShaver
SheepShaver: error while loading shared libraries: libreadline.so.5: cannot open shared object file: No such file or directory
dave2389@dave2389-laptop:~$ 


I searched for libreadline in Synaptic, libreadline6 is installed, though there were other entries there that weren't.

---

### Post by akakingess on 2010-01-12
> **..::| Dave89 |::.. said:**
> Typed SheepShaver into the terminal, this is what I got:

dave2389@dave2389-laptop:~$ SheepShaver
SheepShaver: error while loading shared libraries: libreadline.so.5: cannot open shared object file: No such file or directory
dave2389@dave2389-laptop:~$ 


I searched for libreadline in Synaptic, libreadline6 is installed, though there were other entries there that weren't.

The next step may be to see which dependencies SheepShaver requires as it may need a different version of libreadline, at which point you would need to install  that lib and create a symlink of it into the proper directory for SheepShaver. Just my $.02.

---

### Post by warfacegod on 2010-01-12
Under Edit, in Synaptic, select Fix Broken Packages. That might help.

---

### Post by ..::| Dave89 |::.. on 2010-01-12
I installed libreadline5, I get this error, [http://ubuntuforums.org/showthread.php?t=802457](http://ubuntuforums.org/showthread.php?t=802457)

I entered the command in the terminal, SheepShaver wouldn't even start the settings panel, until I restarted, then I got the same message as before.

EDIT: I tried to run SheepShaver under the sudo command, and got this, if it helps to diagnose the problem:

dave2389@dave2389-laptop:~$ sudo SheepShaver
SheepShaver V2.3-Pre (May 31 2007) by Christian Bauer and Mar"c" Hellwig
Segmentation fault
dave2389@dave2389-laptop:~$ 


What the heck is "Segmentation fault"?

---

### Post by ..::| Dave89 |::.. on 2010-01-12
I found another .deb archive of SheepShaver which actually works.  The one I converted may have been corrupt.  Thanks for all your help.

---

### Post by moss901 on 2010-01-20
where?
I can't find anything that doesn't give me problems.

Keep getting error:
*SheepShaver: error while loading shared libraries: libreadline.so.4: cannot openshared object file: No such file or directory*

even after doing:
*sudo ln -s /var/lib/libreadline.so.5 /var/lib/libreadline.so.4*

GH3Y!

---

