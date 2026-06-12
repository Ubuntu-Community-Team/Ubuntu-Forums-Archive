---
title: "How do you really remove firestarter"
date: 2006-04-08
forum: General Help
---

### Post by saphil on 2006-04-08
I used synaptic to remove it, and it gives an error saying it can't

I use 

sudo apt-get remove firestarter 
and it says it is already removed.

Every time I reboot, firestarter requests password to start, anyway. It is a PITA of very small moment, but I would like to know how to dump the whole thing. 
](*,)

---

### Post by ksudbury on 2006-04-08
Is it starting as a service ? if so stop it from starting on boot ? 

Also check this link will show you where the package has installed files [http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=firestarter&version=breezy&arch=i386](http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=firestarter&version=breezy&arch=i386)

Check and see if it has removed them. 

Keith

---

### Post by truNWA on 2006-04-08
Yea i had that problem too.... you have to sotp it from loading on boot. When you see it on boot and it ask you for a password, it does nothing.

---

### Post by saphil on 2006-04-08
It shows up in these places:

root@Ubuntu-Ultrix:/etc/rc1.d # locate firestarter
/etc/rc0.d/K20firestarter
/etc/rc1.d/K20firestarter
/etc/rc2.d/S20firestarter
/etc/rc3.d/S20firestarter
/etc/rc4.d/S20firestarter
/etc/rc5.d/S20firestarter
/etc/rc6.d/K20firestarter
/root/.gnome2/firestarter
/root/.gconf/apps/firestarter
/root/.gconf/apps/firestarter/client
/root/.gconf/apps/firestarter/client/filter
/root/.gconf/apps/firestarter/client/filter/%gconf.xml
/root/.gconf/apps/firestarter/client/%gconf.xml
/root/.gconf/apps/firestarter/%gconf.xml
/root/.gconf/apps/firestarter/firewall
/root/.gconf/apps/firestarter/firewall/dhcp
/root/.gconf/apps/firestarter/firewall/dhcp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/tos
/root/.gconf/apps/firestarter/firewall/tos/%gconf.xml
/root/.gconf/apps/firestarter/firewall/%gconf.xml
/root/.gconf/apps/firestarter/firewall/icmp
/root/.gconf/apps/firestarter/firewall/icmp/%gconf.xml

It does not show up as a running service in the gui services dialog, and it does not show up on the system manager.  It acts like a trojan.  Should I just root it all out in safe mode or something?  :rolleyes:

---

### Post by taurus on 2006-04-08
[QUOTE=saphil]It shows up in these places:

root@Ubuntu-Ultrix:/etc/rc1.d # locate firestarter
/etc/rc0.d/K20firestarter
/etc/rc1.d/K20firestarter
/etc/rc2.d/S20firestarter
/etc/rc3.d/S20firestarter
/etc/rc4.d/S20firestarter
/etc/rc5.d/S20firestarter
/etc/rc6.d/K20firestarter
[/QUOTE]
I think those are links to /etc/init.d/firestarter so it's safe to remove them...
> 
/root/.gnome2/firestarter
/root/.gconf/apps/firestarter
/root/.gconf/apps/firestarter/client
/root/.gconf/apps/firestarter/client/filter
/root/.gconf/apps/firestarter/client/filter/%gconf.xml
/root/.gconf/apps/firestarter/client/%gconf.xml
/root/.gconf/apps/firestarter/%gconf.xml
/root/.gconf/apps/firestarter/firewall
/root/.gconf/apps/firestarter/firewall/dhcp
/root/.gconf/apps/firestarter/firewall/dhcp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/tos
/root/.gconf/apps/firestarter/firewall/tos/%gconf.xml
/root/.gconf/apps/firestarter/firewall/%gconf.xml
/root/.gconf/apps/firestarter/firewall/icmp
/root/.gconf/apps/firestarter/firewall/icmp/%gconf.xml

It does not show up as a running service in the gui services dialog, and it does not show up on the system manager.  It acts like a trojan.  Should I just root it all out in safe mode or something?  :rolleyes:
It's safe to remove /root/.gnome2/firestarter & /root/.gconf/apps/firestart as well...

---

### Post by saphil on 2006-04-08
well, since /etc/init.d/firestarter is not there, the links might just do nothing..  They still show up using locate.  I guess I need to update the locate database

---

### Post by saphil on 2006-04-09
Halleluyah!  Firestarter is gone!  The universe is mine to add my own software firewall to!!

Thanks!

---

