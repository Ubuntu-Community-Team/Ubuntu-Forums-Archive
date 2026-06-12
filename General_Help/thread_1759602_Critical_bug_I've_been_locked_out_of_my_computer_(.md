---
title: "Critical bug: I've been locked out of my computer (Natty) again.  Fixes?"
date: 2011-05-15
forum: General Help
---

### Post by unagimiyagi on 2011-05-15
Hi,

I have autologin set up on Natty.  I did nothing, except logout or restart, and now I"m locked out of my system. It's an endless loop where it asks me my password, I enter it, and then it just reboots the computer or tries to relogin without any error messages.

This is the second time that this has happened on a fresh install.  Of course, 2-3 days out each time.  I'm not happy with this and wonder if anyone else has this issue or not and how to fix it?  I can't get into my system right now.

Thanks!

---

### Post by doas777 on 2011-05-15
> **unagimiyagi said:**
> Hi,

I have autologin set up on Natty.  I did nothing, except logout or restart, and now I"m locked out of my system. It's an endless loop where it asks me my password, I enter it, and then it just reboots the computer or tries to relogin without any error messages.

This is the second time that this has happened on a fresh install.  Of course, 2-3 days out each time.  I'm not happy with this and wonder if anyone else has this issue or not and how to fix it?  I can't get into my system right now.

Thanks!
it sounds like somthing is crashing on the desktop load and triggering a reboot. it is possible that someone has configured your Pc to run a script on login, which reboots the machine, but that depends entirely on your environment. 

I woudl boot from a livecd, and use the log viewer to open the dmesg kernel and syslog files in /var/log on your PCs root partition. they shoudl give you a clue as to why it is shutting down.

---

