---
title: "disable avahi daemon"
date: 2010-01-16
forum: General Help
---

### Post by Fika on 2010-01-16
When I try to use this command 

gksu gedit /etc/avahi/avahi-daemon.config

the file comes up blank. How can I edit this file to stop avahi from starting? 

Is the file supposed to be under /etc/default/avahi-daemon in ubuntu 9.10? Mine shows in it's own file /etc/avahi.

---

### Post by Fika on 2010-01-16
I got it off the system with 

sudo apt-get remove avahi

---

### Post by Riverside on 2010-12-20
> **Fika said:**
> I got it off the system with 

sudo apt-get remove avahiRemoving avahi-daemon and its dependencies using Synaptic (or aptitude, or apt-get) appears to work also.

---

### Post by Light-kun on 2010-12-30
Thanks, avahi-autoipd made me crazy already (every n minutes my ethernet connect  failed). Uninstalled it, disabled in Services. 
Thanks!

---

### Post by Ibidem on 2011-01-27
Well, it can do worse:
I just had to deal with avahi-daemon doing a core dump and locking up my laptop right after boot.  (I was using it at school, and a wireless printer was around...no idea why it did that, though.  I can't file a bug without some clue on that.)
When I booted in GUI mode, I got a black screen and hard freeze.
In "Recovery" mode, I logged in and then...
the core dump showed up-with avahi-daemon at the start.  I tried Ctrl+Alt+Del, which reboots a working system in CLI mode, and the cursor was still frozen (no response at all).
Reboot (manual)->more of same
So I fixed it like so:
Reboot ->edit boot prompt for "recovery"->change 'ro single' to 'rw init=/bin/bash'->boot
("No job control on tty1" or some such nonsense)
openvt 2 /bin/bash; Ctrl-Alt-F2 to switch VT
root@(nowhere)#aptitude remove avahi-daemon
(asks about removing mdns-something-say yes)
And it now works.

---

