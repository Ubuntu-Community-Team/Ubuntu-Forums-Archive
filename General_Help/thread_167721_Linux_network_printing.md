---
title: "Linux network printing"
date: 2006-04-29
forum: General Help
---

### Post by galeron on 2006-04-29
Hello people. I'm running Breezy on my desktop in my office network. I have this laser printer (Brother HL-2040) connected to my D-Link DP-303 (EOL) print server through the LPT parallel port. 

My question is: How do I print to this printer. On Windows, I have to add a new TCP/IP port to do it. I have tried the network printing option under System/Adminstration/Printing but it does not work

TIA

---

### Post by tazzik on 2006-04-29
I had problems printing to a network printer, then i got a print server.
Before that though I:
1.Setup printer and file sharing on the windows pc it was connected to.
2.Make an exception in the firewall on the windows pc to allow any connections from 192.168.0.2 -- 192.168.0.12 (my networked pcs range)
3.In ubuntu 5.10 go to sytem > administartion(i tink) and then > printers
4.Make sure samba is installed 
5.use SMB (WINDOWS) printer in the setup printer screen. follow the instructions
6. Done (hopefully)!
hope that sorts u out

---

### Post by lazyrussian on 2006-05-01
I have a quesiton too. I'm in the resverse situation (and on Kuubuntu), but I found this thread so I might as well post it here.

I live in a dorm room with a few roomates. The printer is mine and connected to my computer. I ran into a problem last ngiht when I sent my desktop home (winXP) and decided to use my laptop for the last few weeks of the semester (laptop is running kubuntu breezy).
I have no idea how to share this printer thats connected on my computer on a network, let alone how I could share it and have 2 windows users be able to  print from it.

Thanks in advance!

---

### Post by rvergara on 2006-05-01
Galeron,

Use the jet direct option under when defining the network printer. You did not report if you had set this as a cups, unix, or samba printer. I set mine as jet direct and works flawlessly with my print server.

Hope this helps

Ramiro

---

