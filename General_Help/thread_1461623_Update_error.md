---
title: "Update error"
date: 2010-04-24
forum: General Help
---

### Post by schulznotee on 2010-04-24
OK, kids (my DOB 7/17/35... so I can say that), when I try to update (System > Adminstration > Update Manager) I get the following:  

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

I've tried following the instructions but keep coming back to the error message.

HELP!

---

### Post by Naitsirhc Hsem on 2010-04-24
try [http://ubuntuforums.org/showthread.php?t=653495]("http://ubuntuforums.org/showthread.php?t=653495")

---

### Post by schulznotee on 2010-04-25
Well, dang! I'm really tempted to dig out the Vista recovery discs and dump this.

I really like the concept and how it works... when it works. However, when it doesn't work, Ubuntu isn't worth a damn. I've tried all the remedies I've been able to find but I just keep going in circles. 

Too bad there isn't a knowledgeable user somewhere in Central Florida... or is there?

---

### Post by QLee on 2010-04-25
[QUOTE=schulznotee]Too bad there isn't a knowledgeable user somewhere in Central Florida... or is there?[/QUOTE]

Will Orlando do? You've missed the April 15 meeting but there will be one next month.
[http://www.leap-cf.org/](http://www.leap-cf.org/)

---

### Post by dino99 on 2010-04-25
its an index problem: when you run dpkg --configure -a it might show you one or more package names which have problems.

so, install "locate" and into console: locate that-package, when you have the path, go there and delete that package, make this for each package that have problem.

then update and upgrade, end with sudo apt-get install -f

---

