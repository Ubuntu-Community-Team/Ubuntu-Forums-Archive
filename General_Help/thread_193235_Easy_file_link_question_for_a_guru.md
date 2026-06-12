---
title: "Easy file link question for a guru"
date: 2006-06-09
forum: General Help
---

### Post by biguns on 2006-06-09
I just modfied my iptables using the howto at [http://doc.gwos.org/index.php/IptablesFirewall]("http://doc.gwos.org/index.php/IptablesFirewall") everything seemed to have gone smoothly but when I try to make the firewall script run at boot using ```
sudo update-rc.d firewall defaults
``` I get the following error. It's probably because I installed and then uninstalled Firestarter. 

```
tony@avatara:/etc/init.d$ sudo update-rc.d firewall defaults
update-rc.d: warning: /etc/rc2.d/S13firewall is not a link to ../init.d/firewall or /etc/init.d/firewall
 System startup links for /etc/init.d/firewall already exist.
```

I know there is any easy way to fix this I just don't know how. Little Help please?

Thanks

---

### Post by biguns on 2006-06-10
OK, can someone point me in the direction of a great symbolic link tutorial?

Thanks for any help.

---

### Post by aysiu on 2006-06-10
I don't know a great symbolic link tutorial, but I do know...

**For Gnome**: Alt-F2 ```
gksudo nautilus
``` and middle-click-dragging and selecting *link here*

or

**For KDE** Alt-F2 ```
kdesu konqueror
``` dragging and selecting *link here*.

---

### Post by biguns on 2006-06-10
Thank Aysiu, I see you often in this forum and I think its great that you help so many people.

---

