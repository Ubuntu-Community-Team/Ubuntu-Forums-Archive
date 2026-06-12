---
title: "Stop Gnome on boot"
date: 2006-06-16
forum: General Help
---

### Post by GTStang4793 on 2006-06-16
I want to use one of my spare computers as a server so I threw in the Ubuntu CD and booted. The boot option flashes up and goes away too fast before I can enter "server" to install with out a gui. So I have a full Ubuntu install and I would like to push a little more performance out of the box by not using the gui. How can I stop gnome from loading on boot?

---

### Post by the slayer on 2006-06-16
U might consider, downloading the server cd. As far as i know the regular ubuntu cd dont ship with the server options. Yes u can remove and configure, to make it a server install. But if ur not that familar with it, i would recommend the server cd, and a reinstall.
Sorry i cant be more helpfull

---

### Post by ayoli on 2006-06-16
if you dont want gnome you can just do

sudo apt-get remove ubuntu-desktop

---

### Post by asimon on 2006-06-16
ubuntu-desktop is just a metapackage, removing it won't change anything, all gnome packages will still be there. Really removing all gnome packages is somewhat more complicated. There should exist some threads about this.

To just stop Gnome's login manager from starting during boot remove it's initrc link via
```

sudo rm /etc/rc2.d/S13gdm

```.

---

### Post by ayoli on 2006-06-17
he can also just chmod -x /etc/rc2.d/S13gdm
btw you're right asimon about the ubuntu metapackage, it can be use to install a whole desktop, but not for uninstall. I wonder what could be a simpland single command to remove whole gnome DE (i don't want to, just curious)

---

### Post by linuchsan on 2006-06-17
or, update-rc.d -f gdm remove

---

### Post by asimon on 2006-06-17
[QUOTE=ayoli]btw you're right asimon about the ubuntu metapackage, it can be use to install a whole desktop, but not for uninstall. I wonder what could be a simpland single command to remove whole gnome DE (i don't want to, just curious)[/QUOTE]
Here are some pointers:
[[howto] Gnome 5.10 - HowTo: Fully uninstall the kubuntu-desktop meta-package](http://www.ubuntuforums.org/showthread.php?t=96048)
[[howto] Kde 5.10 - HowTo: Fully Uninstall the ubuntu-desktop meta-package](http://www.ubuntuforums.org/showthread.php?t=96046)
[Getting Back to a Pure KDE on Ubuntu](http://www.psychocats.net/ubuntu/purekde)

---

### Post by ayoli on 2006-06-17
thx for links asimon ;)

---

