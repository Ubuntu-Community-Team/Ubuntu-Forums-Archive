---
title: "Oops! Deleted pure-ftpd from init.d, and It won't come back!"
date: 2005-03-16
forum: General Help
---

### Post by Trickyphillips on 2005-03-16
I had pure-ftpd installed, and I decided to test proftpd, so I uninstalled pure, and downloaded + installed pro. When I looked in /etc/init.d, I still saw pure-ftpd so I decided to remove it. I decided to go back, so I uninstalled proftpd, and removed *it* from init.d as well, and now when I install either of them, they won't show up there. Anyone know how I can fix this?

Thanks in advance!

---

### Post by az on 2005-03-16
sudo apt-get install --reinstall <package>

---

### Post by Trickyphillips on 2005-03-16
[QUOTE=azz]sudo apt-get install --reinstall <package>[/QUOTE]

Nope.. No luck with that. :(

---

### Post by az on 2005-03-16
Are you installing them by tarball?

Why are you not using deb packages and apt?

Also, take a look at the dependancies. and the list of installed files in a package.  Sometimes, the file you are looking ofr is not in one package but in another related package

Example

mysql
mysql-client
mysql-common

proftpd-common?

---

### Post by Trickyphillips on 2005-03-16
Yes, I'm using apt-get, but it's still not showing in /etc/init.d. I think I'm just going to reinstall ubuntu.

---

### Post by az on 2005-03-16
I really do not think you need to reinstall.

dpkg -l|grep ftp 

to see what you have installed with regards to ftp.

---

### Post by Trickyphillips on 2005-03-17
I reinstalled anyway, and I'm glad I did... I was having connection problems with the FTP, even before my init.d problems started occurring. Now everything's working perfectly. I didn't really lose much. I only had it installed for a couple days, before reformatting.

Thanks for the help, azz. Forgive me for taking the easy way out. :p

---

