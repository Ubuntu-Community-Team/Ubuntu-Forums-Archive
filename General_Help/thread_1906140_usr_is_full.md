---
title: "/usr is full"
date: 2012-01-08
forum: General Help
---

### Post by befana on 2012-01-08
I'm running Kubuntu 11.10, 64 bit, kernel 3.0.0-14-generic with /usr on a separate partition - 4,7 GB. Now /usr is full and I can't install programs and debbuging symbols. I've tried "apt-get clean", "apt-get autoclean" and "apt-get autoremove", but /usr is still full. How can I have some empty space on my /usr partition?

---

### Post by mikewhatever on 2012-01-08
If you must have /usr on a separate partition, give it at least 10GB. If that's not possible, consider a minimal installation, while staying away from full blown DEs like Gnome or KDE, as well as from metapackages like ubuntu-desktop or kubuntu-desktop.

---

### Post by Wayne_V on 2012-01-08
my /usr on a base install is 4.1G ....

you could remove any sources your have installed ...

remove man pages ...

or, mv something off /usr and link it back:

$ cd /usr
$ sudo mv games /BIGDRIVE/games
$ sudo ln -s /BIGDRIVE/games /usr/games

---

### Post by befana on 2012-01-08
Wayne_V, I don't have any games and any bigdrive - my /home is something like bigdrive - 15 GB, and root is 7 GB. And I need man pages. Any other ideas?

---

### Post by Wayne_V on 2012-01-09
1) add a new drive and move /usr there?

2) is there enough space on / to move /usr onto that partition and use the existing /usr partition for something else (would require booting to recovery mode ...)

3) look for things to delete?  I would start in /usr/share:

$ cd /usr/share
$ du -sk * | sort -n
(tuxpaint for example)
$ dpkg --search /usr/share/tuxpaint

tuxpaint-plugins-default, tuxpaint-data, tuxpaint-stamps-default: /usr/share/tuxpaint

$ sudo apt-get purge tuxpaint-plugins-default tuxpaint-data tuxpaint-stamps-default

4) move share to /home and then link it back to /usr ? (same procedure as shown previously)

5) reinstall, with a bigger partition or no separate partition for /usr?  (best solution)

---

### Post by Double.J on 2012-01-09
I'd suggest booting from the live cd and using gparted to see if you can resize your partitions to even up your disk usage? 

Don't forget to back up first ;)

---

### Post by befana on 2012-01-09
Thank you for your suggestions. I've followed gnu/mirow advice to backup and then Wayne_V's point 5), and finally removed win7 (it was only occuping my hard drive). Problem solved.

---

