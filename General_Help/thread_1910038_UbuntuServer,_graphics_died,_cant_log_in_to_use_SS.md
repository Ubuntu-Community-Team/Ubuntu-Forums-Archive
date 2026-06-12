---
title: "UbuntuServer, graphics died, cant log in to use SSH/VNS"
date: 2012-01-16
forum: General Help
---

### Post by HeartBreakKid on 2012-01-16
Hello guys.

Okay, weird situation.
I have a really old desktop and yesterday I decided to setup ubuntu-server as a home server on that thing. It has no onboard graphics.
I installed gnome-desktop, so at the start of the server, I have to log in.

Today I restarted it, and it looks like the graphics card died.
I get no signal on the monitor. I can't use SSH or VNS, because the services start after I log in...

Is there a way to log in over the network? cmd? net use?
Can someone tell me what keys I have to press to log in? So I can try to do it blindy and then setup auto-login.

I tried to press Enter after the boot to select the user "Administrator" and then typed the password and enter again, but it wouldnt log in because SSH/VNC still won't work.

Ubuntu-Server 10.04 32-bit. Reeaally old computer. No other graphics-card I could use. Already tried different VGA/DVI cables...

---

### Post by efflandt on 2012-01-16
By default only the ssh client is installed, not the server (unless you installed it), so there is nothing listening on port 22 or any other port for ssh.

Do you have another computer that you could put the drive into, or usb drive enclosure, to possibly boot to it and add/configure things from there so you could access it when back in the old computer?

I have an old headless Celeron 300 MHz in my basement that has not seen a monitor for many years (SuSE 8.2 I think).  It ran 24/7 non-stop 5 years from July 2006 until I temporarily shut it down for a 14 hr power failure last summer.  The only way I have to control it is ssh (runs apache virtual hosts and keeps no-ip.com advised of my dynamic dsl IP).

---

### Post by HeartBreakKid on 2012-01-17
I have the ssh-server installed. I could login into the Server from other clients in my network (Putty), but it looks like the service starts after you log in. I guess the ssh-server-service isnt even started because my ubuntu is hanging at the login-screen.

But yeah, I can try to put the Harddisk in my other computer, configure auto-login and then put it back in my server. How could I not think of that. Thank you man! :popcorn:

---

