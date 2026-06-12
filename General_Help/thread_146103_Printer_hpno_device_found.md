---
title: "Printer hp:/no_device_found"
date: 2006-03-17
forum: General Help
---

### Post by AndyCooll on 2006-03-17
Still waiting for assistance! So, my apologies for now re-posting this, but on a different forum. I posted it originally on the "server" forum, but after three days I'm still waiting for a reply and am guessing there's no-one who can help me there. Maybe you good folk might be able to do so. 

I'm re-installing my file server and attached to it is a HP DeskJet 990CXI. I've used the "server" install and it doesn't have a gui. I've tried to set up CUPS. And everything seems to work fine... until it comes to the actual process of printing! CUPS says the printer is ready, but when I try a test page it is immediately "aborted". "lpinfo -v" brings up the message of the thread title above.

I know I CAN set up a print server, for on a previous server install with a gui, it worked fine. My notes say make sure 'Global Settings-Detect LAN settings' are ticked (including the server). However I can't place this tick since I don't have a gui.

So ... I'm not sure what to try next. Anyone able to help?Still

---

### Post by dcstar on 2006-03-17
[QUOTE=AndyCooll]
.....
I know I CAN set up a print server, for on a previous server install with a gui, it worked fine. My notes say make sure 'Global Settings-Detect LAN settings' are ticked (including the server). However I can't place this tick since I don't have a gui.

So ... I'm not sure what to try next. Anyone able to help?Still[/QUOTE]
Do you have the various "hplip" packages installed?

---

### Post by AndyCooll on 2006-03-19
Thanks for the reply. Yes, they are installed.

---

### Post by AndyCooll on 2006-03-27
Thought I'd best share the answer to this since I've finally got my network printing working!

For me the problem was with Firestarter! On a couple of boxes I have this installed and couldn't connect to a printer, but with a newly installed box without Firestarter installed I could see the printserver broadcast fine. I found that by enabling the SMB service in Firestarter these boxes could see the printserver too

I'm not quite sure why this should resolve the issue because as far as I'm aware I have set my printserver up with CUPS and not Samba. It's true that I've installed Samba on the server for when I run a VMWare XP image. I have a smb.conf file which I always use, and part of this includes allowing access to printers though not specifically CUPS. Anyway working out why is for another investigation. :cool:

---

