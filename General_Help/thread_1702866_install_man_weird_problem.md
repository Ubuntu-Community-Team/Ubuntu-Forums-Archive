---
title: "install man weird problem"
date: 2011-03-08
forum: General Help
---

### Post by vadimslav on 2011-03-08
Hi guys!
I have installed (at least I believe this) manpages. After that I typed:
root@myserver:~# man ls
that resulted in:
-bash: man: command not found

After that I tried to install it again:

root@myserver:~# apt-get install manpages
Reading package lists... Done
Building dependency tree
Reading state information... Done
manpages is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

After that I type again:
root@myserver:~# man ls
but it still the same:
-bash: man: command not found

What am I missing?

---

### Post by vadimslav on 2011-03-08
Jeeez, I needed
sudo apt-get install man-db
Mark as SOLVED.

---

### Post by blueridgedog on 2011-03-08
What version are you using that the db was not included?

---

