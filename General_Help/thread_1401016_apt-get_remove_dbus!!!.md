---
title: "apt-get remove dbus!!!"
date: 2010-02-07
forum: General Help
---

### Post by TheShader on 2010-02-07
Lol please don't laugh at me, I accidentally entered sudo apt-get remove dbus and entered yes. I didn't put any patch after that, sooo... you guess what happened. I interrupted the remove process. Now I have a working GDM but the mouse, wireless and Gnome is not working. I can get to a virtual terminal but I don't know what to do :( Please help.

:roll::D

---

### Post by TheShader on 2010-02-08
bump

---

### Post by falconindy on 2010-02-08
There's going to be a log file for apt in /var/log. Sift through it and determine what was deleted so you can reinstall it.

These commands should be helpful:
"less /var/log/apt.log" - pager to view the log
"sudo apt-get install <pkg>" to reinstall a package.

---

### Post by TheShader on 2010-02-08
Thanks... However the apt log doesn't contain the packages that were removed. I'm sure. Maybe it didn't write them because the process was interupted??? :/

---

### Post by falconindy on 2010-02-08
/var/log/dpkg.log has the information you want. Sorry, my previous post was just a stab in the dark (not running Ubuntu) -- I should have made that more clear.

---

### Post by TheShader on 2010-02-09
Hey thank you, that shows the packages that were removed. However I fixed this with a different way, first I completely removed dbus.

# apt-get purge dbus

then I reinstalled ubuntu-desktop...

# apt-get install ubuntu-desktop

It fixed, however I am using Linux Mint and I lost some themes, gdm, mint menu on the panel etc so I had to install the Mint package:

# apt-get install mint-meta-main

This is solved now. Thanks for the help anyway, falconindy ;)

---

### Post by jamil.farooq@hotmail.com on 2011-06-23
I have a similar problem. I have accidently deleted dbus that concludes deleting almost everything from graphic manager to network manager. so i have lost everything. when i reboot i have only command prompt/terminal for me to work. no desktop and no network

I can't help myself by reinstalling packages as i have no network connectivity as network manager is also not presents. is there any solution to have my system back?????
please reply as soon as possible as i am in dire need.


Regards
jamil

---

