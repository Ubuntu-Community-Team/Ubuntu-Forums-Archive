---
title: "problem: setting advanced power management level to 0xfe"
date: 2009-07-29
forum: General Help
---

### Post by crazyy on 2009-07-29
During uninstalling Dbus from my ubuntu I got this message: "setting advanced power management level to 0xfe [OK]" in a black screen and after that happened nothing so I decide to restart and when I did it I got:
kinit: No resume image, doing normal boot...

what the problem?
how can I solve it??

---

### Post by mikewhatever on 2009-07-29
Well, what's wrong with the normal boot? There just doesn't seem to be a problem. Can you elaborate on the purpose of this thread.

---

### Post by crazyy on 2009-07-29
For sure no problem with normal booting. The problem that it's not going to normal booting. 
Instead it stays in this black screen and start Gnome graphic manager which is like the terminal but nothing more.

---

### Post by ajgreeny on 2009-07-29
So why uninstall dbus if normal booting was OK?  If you can get a cli, and I'm not quite sure what you mean by "Instead it stays in this black screen and start Gnome graphic manager which is like the terminal but nothing more" you can gert dbus and anything else you removed with ```
sudo apt-get install dbus second-package third-package 
```or more easily with ```
sudo apt-get install ubuntu-desktop
```Your main problem as far as I can see it, is that removing dbus also gets rid of much of the gnome desktop, and the xserver and much else.

---

### Post by crazyy on 2009-07-29
Thanks ajgreeny for your quick reply.

I needed to downgrade the version of dbus so I decide to uninstall it and install an older version. but during uninstalling dbus I got the problem I expained previousely.

So as you said my problem is with gnome desktop and xserver.  I tried :
```
sudo apt-get install ubuntu-desktop
```but I have no network configurations. So I made a new network configurations:
```

ifconfig eth0 *my-ip* netmask *my-netmask *up
route add default gw *gateway-ip-add*
sudo nano /etc/resolv.conf
```and add this line:
nameserver *DNS-server-ip-add*

Then I installed dbus again just to because it's the reason of my problem and:
```

sudo apt-get install dbus
sudo dpkg-reconfigure *xserver*-*xorg*
```follow the instructions and finally reboot.
Now everything is OK eccept one thing. Know why this happened in the first place?
As I know uninstalling dbus should not do this but all what can I say is: STRANGE.

---

