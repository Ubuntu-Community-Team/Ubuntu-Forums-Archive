---
title: "CUPS printer service on Ubuntu and Windows clients and some more"
date: 2006-05-24
forum: General Help
---

### Post by zainka on 2006-05-24
Hi

I have installed CUPS on a server running Linux and wonder if anyone have had success using the Canon MP500 ink. printer? (I havent got it my self yet so I cant try), As far as I know the CUPS suports the HP LaserJet and DeskJet printers and several EPSON printers are supported, but I cant find anything aboute Canon printers. 

The server will act as a spool server for workstations which are running the dreadfull windows XP or 2000 OS and I have heard that CUPS does not suport windows machines. (Can this be true) My idea of a spool server is that it shall only be a relay station between a client and a printer and it only task should be to hold documents in serevr memory (in spite of having them in client memory) until printer is ready and offcource not adding or restracting anything from the documeny. But by peaking into CUPS documents it look a **bit** more complicated. Some advice would be nice.

All I wanted to do with the windows client was to add a new printer by normal methodes (installing drivers and so) and then conect it to a IP printer port like IP_192.168.1.2 (in my case) on port 9100 wich is the port on the server the printer will be added (USB)...

Any help with topic will do
Best regards 
Vidar (Z)

---

### Post by drpaul on 2006-05-24
I have a Brother laser printer that is shared [through Samba] with a Windows XP machine on my network. CUPS is managing the printing for my Ubuntu printing. 

I don't know how to do your method, but using Samba works well for sharing with Windows clients.

Paul

---

### Post by zainka on 2006-05-25
Thank you

Does this mean that I have to install samba on each windows computer to make it able to print through a Linux server? How aboute using RAW protocols?

Thanks in advance
Vidar (Z)

---

### Post by jethro10 on 2006-05-25
[QUOTE=zainka]Thank you

Does this mean that I have to install samba on each windows computer to make it able to print through a Linux server?
Vidar (Z)[/QUOTE]

No, Samba is a product that 'pretends' its windows for file and print services. so all your windows PC's will see a new 'windows' server with printers available.

just put samba on the Linux box, set up the workgroup the same, share a linux printer then windows clients can be setup as normal.

Jeff

---

### Post by kwhatcher on 2006-05-29
how do you share the printer in ubuntu?

---

