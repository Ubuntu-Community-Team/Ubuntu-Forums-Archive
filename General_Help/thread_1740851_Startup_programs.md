---
title: "Startup programs?"
date: 2011-04-27
forum: General Help
---

### Post by MikeR. on 2011-04-27
Hi all,
I've been using ubuntu for about 3 weeks now and liking it a lot, but after installing a lot i've noticed a slower bootup. I like to have a snappy boot and im getting stuff popping up at startup. Is there a program like msconfig for ubuntu or something to stop some services/programs from starting up after login? Also does anybody know good ways to keep ubuntu fast?

---

### Post by Pand5461 on 2011-04-27
Check System->Preferences->Startup Applications. See also [this page]("https://help.ubuntu.com/community/AddingProgramToSessionStartup").

---

### Post by lithopsian on 2011-04-27
As a start you can examine the list of symlinks in /etc/rcS.d and /etc/rc2.d.  These are the services that are started at boot.  There are various programs that will show you them and allow you to manipulate them but I find there is nothing to beat actually seeing them with your own eyes.  These services start as root although they may kick themselves off as a different user.

In addition there are programs that are autostarted by your desktop.  These run as you the user.  Find the autostart script for your desktop manager and you will see a few to many programs getting kicked off.  If properly organised these don't impact boot much.  They are kicked off after your log in, nearly always in the background, and usually after a few seconds delay.

---

### Post by bodhi.zazen on 2011-04-27
> **MikeR. said:**
> Hi all,
I've been using ubuntu for about 3 weeks now and liking it a lot, but after installing a lot i've noticed a slower bootup. I like to have a snappy boot and im getting stuff popping up at startup. Is there a program like msconfig for ubuntu or something to stop some services/programs from starting up after login? Also does anybody know good ways to keep ubuntu fast?

Well it depends on who you ask. IMO, if you wish to improve performance and are willing to tweak ;)

1. I always do a minimal install and add only what I want.

2. Often this means adding window managers - openbox, fluxbox, awesome, etc. If you want gnome, install gnome and not ubuntu-desktop.

3. Use light weight applications. Cream or gedit rather then open office.

4. Make sure it is not a hardware problem , drivers for video cards and wireless are sometimes a problem.

IMO it is easier to build up then remove things.

---

### Post by MikeR. on 2011-04-27
Thanks for the quick responses. I took off the startup programs, but it still takes 1 minute to boot up. It used to take about 30 secs to boot up. Any other ideas besides completly changing the UI? lol I am not gonna reinstall ubuntu for a silly boot up time but I still would rather the way it was when it was starting up very quickly

---

### Post by lithopsian on 2011-04-27
Find out what is slowing down the boot.  Reprofile ureadahead.  Use bootchart.  Or just watch a non-quiet boot.

---

### Post by MikeR. on 2011-04-27
Ok so i think i found it, but I want to make it even snappier :) does anyone know if there's a desktop ui very close to gnome like a gnome mini or something? im trying to get something like xfce but more pretty to look at

---

### Post by bodhi.zazen on 2011-04-27
lubuntu , openbox + tint2 , fluxbox, awesome ...

---

