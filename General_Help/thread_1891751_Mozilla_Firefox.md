---
title: "Mozilla Firefox"
date: 2011-12-06
forum: General Help
---

### Post by Phyl on 2011-12-06
I'm currently using Ubuntu 11.10, but for some reason mozilla doesn't opens, it appears on process list but the "window" doesn't opens.

> cezar@ubuntu:~$ firefox

None response.

> cezar     3190 83.3  1.1 450360 46920 pts/0    Rl+  12:24   0:02 /usr/lib/firefox-8.0/firefox
cezar     3192  0.0  0.0      0     0 pts/0    Z+   12:24   0:00 [firefox] <defunct>


---

### Post by mike555 on 2011-12-06
if you kill the process it should then open ......... that happens when something is trying to run in firefox, I have that happen with Yahoo games site .

---

### Post by pqwoerituytrueiwoq on 2011-12-06
try [FONT=Courier New]firefox -safe-mode[/FONT]
you may have a addon issue

---

### Post by oldtimer7777 on 2011-12-06
> **Phyl said:**
> I'm currently using Ubuntu 11.10, but for some reason mozilla doesn't opens, it appears on process list but the "window" doesn't opens.



None response.

Reboot your system, install Bleachbit, clean out everything with it, and restart firefox.

sudo apt-get install bleachbit
gksudo bleachbit

Careful that bleachbit doesn't delete your bookmarks or passwords.

---

### Post by pqwoerituytrueiwoq on 2011-12-06
> **oldtimer7777 said:**
> Reboot your system, install Bleachbit, clean out everything with it, and restart firefox.

sudo apt-get install bleachbit
gksudo bleachbit

Careful that bleachbit doesn't delete your bookmarks or passwords.
bleachbit does not need to be root to clean firefox unless you are foolishly running firefox as root

---

### Post by oldtimer7777 on 2011-12-06
> **pqwoerituytrueiwoq said:**
> bleachbit does not need to be root to clean firefox unless you are foolishly running firefox as root

To get the nasty stuff you need to use it from root and local.  If you were only thinking cookies and cache items you would be correct.

---

### Post by Phyl on 2011-12-06
Well, I did that bleachbit thing and when I open firefox on safe mode it opens a window asking which changes to make permanent, but i already tried everything and it don't opens the window, and the process continues there. (Yeah i already tried killing process and re-opening)

---

### Post by pqwoerituytrueiwoq on 2011-12-09
[FONT=Courier New]mv ~/.mozilla ~/.mozilla_bak[/FONT]
see if it opens after that (firfox will be reset but your data is backed up)
if not
[FONT=Courier New]rm -rf ~/.mozilla[/FONT]
[FONT=Courier New]mv ~/.mozilla_bak ~/.mozilla[/FONT]
reinstall firefox

---

