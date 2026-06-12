---
title: "Openbox + Docker + nm-applet (issues with nm-applet)"
date: 2012-01-23
forum: General Help
---

### Post by gypsumwolf on 2012-01-23
I am building a very slim client. 

I have Openbox + docker + nm-applet + a few other things.

nm-applet loads, but I can't use it unless I load it as root.

When I have it autostart in /etx/xdg/openbox/autostart
it runs, but does not let me use it since I am not running it as root.


How am I supposed to start it so the user can use it?

---

### Post by Rodney9 on 2012-01-23
Plenty of Openbox tips here -

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

and this should help you with autostart -

[http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by gypsumwolf on 2012-01-24
I already know how to do autostarts. Thats not a problem.

The problem is when I autostart nm-applet, it is locked. I have to kill it, than load it as root in-order to use the program.

How can I autostart nm-applet and use it as a regular user instead of root?

---

### Post by artjermyn on 2012-02-25
have you tried putting it in the /etc/xdg/openbox/autostart (or autostart.sh) file?  i have to put mine in the autostart.sh file.  for some reason it doesn't run from autostart.

---

### Post by gypsumwolf on 2012-04-24
Had to use openbox-session and it works, rather than just openbox.

---

### Post by techsupport on 2012-04-24
> **gypsumwolf said:**
> I am building a very slim client. 

I have Openbox + docker + nm-applet + a few other things.

nm-applet loads, but I can't use it unless I load it as root.

When I have it autostart in /etx/xdg/openbox/autostart
it runs, but does not let me use it since I am not running it as root.


How am I supposed to start it so the user can use it?

You need to install Crunchbang. It is exactly what you have done except it actually works right:

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by gypsumwolf on 2012-04-24
I probably will check it out. Can't tonight, working on my server atm.

---

### Post by techsupport on 2012-04-24
> **gypsumwolf said:**
> I probably will check it out. Can't tonight, working on my server atm.

Awesome possum. Over and out.

---

