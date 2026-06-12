---
title: "How do I uninstall using the terminal?"
date: 2011-09-26
forum: General Help
---

### Post by linuxuser12345 on 2011-09-26
Hi, I installed something, but the software center only shows an option to "reinstall" not "remove" Spotify for Linux. How do I remove a program successfully using the terminal?

---

### Post by Elfy on 2011-09-26
sudo apt-get remove *packagename*

---

### Post by papibe on 2011-09-26
First you need to know the exact name of the package. For example, let's say I want to delete the program transmission:
```
$ dpkg -l | grep transmission
ii  transmission-common                   2.13-0ubuntu8                              lightweight BitTorrent client (common files)
ii  transmission-gtk                      2.13-0ubuntu8                              lightweight BitTorrent client (GTK interface)

```
So there's 2 packages related to transmission. To remove them:
```
$ sudo apt-get remove transmission-common transmission-gtk
```
That's it. You can also check if there are lower dependencies that can also be uninstall by doing:
```
$ sudo apt-get autoremove
$ sudo apt-get autoclean
```
I hope this helps,
Regards.

---

### Post by linuxuser12345 on 2011-09-26
Thanks, yall! ;D

---

