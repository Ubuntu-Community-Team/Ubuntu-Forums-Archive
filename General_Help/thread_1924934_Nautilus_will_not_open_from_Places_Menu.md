---
title: "Nautilus will not open from Places Menu"
date: 2012-02-13
forum: General Help
---

### Post by cscj01 on 2012-02-13
I had a problem with installing Gimp 2.7.5 and did a partial update;  That led to an uninstall of Gimp.  To fix that, I had to add a couple of PPA's and update, upgrade, and install as follows:```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get install gimp
```That led to me not being able to open nautilus from the Places Menu (anything on the Places Menu will not open).  I can use ```
gksudo nautilus
```to open nautilus from a terminal.  However, if I just enter ```
nautilus
``` in the terminal, I get the following error:```
Could not register the application: Method `DescribeAll' returned type `(a(savbav))', but expected `(a{s(bgav)})'

```Can someone tell me what is happening here?  Thanks.

---

### Post by TedinOz on 2012-02-13
I had the same problem and fixed it with a reboot.

---

### Post by cscj01 on 2012-02-13
Sometimes the obvious is so obvious.  I guess I did not want to deal with the dreaded "Waiting for Network" and "Waiting an additional 60 seconds..." messages.  But it now works.  Thanks for the quick reply.

---

