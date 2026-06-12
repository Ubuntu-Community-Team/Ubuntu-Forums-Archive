---
title: "Graphical WvDial frontend for multiple accounts?"
date: 2005-02-26
forum: General Help
---

### Post by abovett on 2005-02-26
Hi

Anyone know of a Gtk or other graphical frontend for WvDial which allows the selecting of which account you want to connect to? "GNOME PPP" only seems to support one account at the moment, though it looks like the author is considering adding multiple account support.

I want to be able to select between my laptop's internal modem and my T39 GPRS phone (connected via Bluetooth). I have them both working via WvDial (at last!) but it would be nice to be able to launch either connection graphically. I could write something to do it myself but if there's something already out there it would save me a job.

Cheers

Andy B

---

### Post by landotter on 2005-02-26
[QUOTE=abovett]Hi

Anyone know of a Gtk or other graphical frontend for WvDial which allows the selecting of which account you want to connect to? [/QUOTE]

Sort of. I think the best utility for modem configuration is a console program called pppconfig, run it as root "sudo pppconfig" It's pretty self explanatory.

Just create two accounts and you can connect with "pon accountname" and disconnect with "poff accountname". I use the modem-lights applet to start and stop the connection, or you can just type alt+f2 to get a run dialogue.

---

### Post by abovett on 2005-02-26
[QUOTE=landotter]Sort of. I think the best utility for modem configuration is a console program called pppconfig[/QUOTE]
 Thanks, but that's not really what I was looking for. I know about pppconfig, pon and poff, but wvdial is better suited to my purposes. It's easy enough to use from a command line - just wvdial <accountname> - but I'm looking for a graphical frontend to better integrate it into Gnome. So far I've only found "GNOME PPP" which as I say doesn't (yet) support multiple accounts. 

Guess I'll just have to write one myself (if I can ever find the time!)

Andy B

---

### Post by ember on 2005-02-27
I remember from my SuSE-times that there is somethin called kwvdial, also KDE has kppp, which might suit your needs. Yet both are not GTKbased.

---

