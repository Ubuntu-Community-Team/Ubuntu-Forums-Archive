---
title: "lost harddrive space"
date: 2011-04-13
forum: General Help
---

### Post by pieman711 on 2011-04-13
A while back I tried to install quake 4 and when I deleted it to clear  up space I've lost about 6gb of harddrive room on my / folder.

in the attached screen shot is my disk usage analyser showing my home  folder max with 20gb an about 19 gb used however the scan of / shows  only 13gb used. where are the other 6?

---

### Post by danjahner on 2011-04-13
Open a terminal and run :

```
sudo df -h
```

Paste the output.

---

### Post by pieman711 on 2011-04-15
Sorry it's taken so long to reply, I've been away from my computer for a while so couldn't try it. Here is the output from df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              21G   20G  405M  99% /
none                 1000M  288K 1000M   1% /dev
none                 1007M  220K 1006M   1% /dev/shm
none                 1007M  204K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda3              90G   61G   29G  69% /media/D
/dev/sr0              6.6G  6.6G     0 100% /media/MASH_SEASON_7_DISC_3
pieman@pieman-desktop:/$

---

### Post by pieman711 on 2011-04-15
I've found the problem but can't solve it...
I ran disk use analyser as root:
```
gksudo baobob
```And it showed the files were in my "root" trash. I've found it by opening nautilus as root
```
sudo nautilus
```and navigating to /root/.local/share/Trash/files but if i try to delete the files they just reappear in the trash folder here.
Any suggestions?

---

### Post by pieman711 on 2011-04-15
Got it!
The solution was to highlight the files in the root trash and press SHIFT + DELETE on the keyboard.

---

