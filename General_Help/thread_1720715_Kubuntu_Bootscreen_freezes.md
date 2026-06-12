---
title: "Kubuntu Bootscreen freezes"
date: 2011-04-03
forum: General Help
---

### Post by biberbb on 2011-04-03
Hello Together!

I have two Kubuntu machines running, my Laptop and a normal Computer. Current Kernel is 2.6.32-24.
On the Laptop I have mentioned the problem already months ago:

Every once in a while a boot process fails the following way. After grub I get the normal kubuntu boot screen with the 5 (or 6?) blue/white dot progress bar. Everything seems perfect. As usual when ready, all progress dots become blue, but then nothing happens. (Normally then the NVidia Screen should splash for a second and then I should see the log in screen.)

I never paid much attention to this bug, because it happend only every tenth boot or so and only on the Laptop.
Some days ago, I had the same problem on my tower PC, and my Laptop boots only every fifth till tenth time without this problem, so it's getting a bit ..... sticky! :(


Please help friends!
Bb

---

### Post by techunit on 2011-04-03
Could it be a plymouth problem, I wonder? I wish there was more information to work with.

Can you get onto your machine? If you can install start-up manager. And disable plymouth and see if that works.

---

### Post by biberbb on 2011-04-03
Hi! Thanks for the fast answer!

I actually AM on the Laptop right now.
Installed startupmanager, but it throws an error when starting it:

Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) erhalten Sie weitere Informationen (Details &#8211;  1: Verbindung zur Sitzung konnte nicht abgerufen werden: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

It seems to contact an external Server which confuses me a bit.



A Thing I forgot to metion:
After Boot,Fail,Reboot,Fail,Reboot,Fail I sometimes got angry and just killed it by unplugging the power. After this, the next boot always seemed to work....!


Please help further ;)

Bb

---

