---
title: "change primary display on dual monitor setup"
date: 2010-03-10
forum: General Help
---

### Post by badrock on 2010-03-10
Hi, I just installed Ubuntu 9.10 this evening. I have a Nvidia Geforce 8500GT video card with two monitors hooked up (one to the cards VGA, the other to the DVI). I installed Nvidia drivers and Ubuntu is working with both monitors fine.

The problem I am having is it chose the monitor plugged into VGA as the primary (uses that monitor for the toolbars) when I really want them to go on the monitor that is plugged into DVI. Is there anyway for me to switch which monitor Ubuntu treats as the primary?

Any suggestions would be appreciated.

---

### Post by stif on 2010-08-03
I am using ubuntu 10.04 with intel core i5 integrated graphics. but dispite that i have the same problem. i want to use my DVI conntected monitor as primary display with the menu-toolbar and the VGA Monitor as secundary device.
Any Ideas?

---

### Post by stif on 2010-08-11
i figured it out:

regarding to this bugreport: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/216144](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/216144)

> If you want to set a display as primary, just go in
> ~/.config/monitor.xml and change at the desired display 
> the value for the primary key from no to yes.

---

