---
title: "Have you seen my applet?"
date: 2006-05-18
forum: General Help
---

### Post by abstracthumor on 2006-05-18
I feel a little bit like Milton right now...

I loved my linux, but now I can't seem to take seriously a system that can't even make a wireless set up better than windows...

Granted, when I had NM-applet working, Ubuntu was a thing of beauty, but one day, accidently deleting it, I turned my life into a living hell.  Not only do I not have an applet any longer, but my computer now refuses to recognize ANY wireless signal, even if I type the name of said signal into a network box.

No applet, no wireless.  I have NetworkManager installed, Network-Manager-Gnome installed, and WPA supp. installed.  I've tried tweaking my essids.  I've tried over and over and over to get wheelspin's script to work for me (that is what I originally used to get the applet working).

Please, I'm offering  eleventy billion dollars to anyone who can possibly get me on a wireless network without me having to dump dapper and reinstall.  

I'm offering eleventy billion dollars times infinity for anyone who can get me on wireless networks WITH an applet, without having to dump dapper and reinstall.

](*,)

---

### Post by dirwood on 2006-05-18
sudo apt-get install gnome-netstatus-applet *??*

---

### Post by abstracthumor on 2006-05-18
I just did that...I don't know if I should expect something, because nothing definitely happened

---

### Post by dirwood on 2006-05-18
log out, log in and add to panel.

---

### Post by abstracthumor on 2006-05-18
How do I add it?

---

### Post by dirwood on 2006-05-18
right click on a panel, choose "add to panel", find the right applet

---

### Post by abstracthumor on 2006-05-18
Well I know that, but there is no applet shown that is any different or more helpful.

---

### Post by dirwood on 2006-05-18
Theres not one labelled "Network Monitor"?

---

### Post by abstracthumor on 2006-05-18
Oh you're right, but I should have been more clear.  That's always been there, but it certainly doesn't connect me to anything but a land line, and it definitely never automatically maintained an internet connection.

---

### Post by dirwood on 2006-05-18
well, it sounds like you've uninstalled then reinstalled.  I'm not sure what you've forgotten but go through this list and see if anything looks applicable.

*sudo apt-cache search wireless*

---

### Post by abstracthumor on 2006-05-18
Are all the dbg files equally applicable as their non-dbg counterparts?

---

### Post by dirwood on 2006-05-18
I wouldn't think so.  Possibly dev, but not debug.

---

### Post by abstracthumor on 2006-05-18
Well then dirwood, it's been fun.  But it appears you will not be an eleventy billion dollar grand prize winner.  Any new takers?  I want my nm-applet to work like it did when wheelspin's script used to work.

---

