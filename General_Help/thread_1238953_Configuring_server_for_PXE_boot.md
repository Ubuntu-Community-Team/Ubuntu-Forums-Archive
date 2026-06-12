---
title: "Configuring server for PXE boot"
date: 2009-08-13
forum: General Help
---

### Post by Shashankj on 2009-08-13
[FONT=Calibri][SIZE=3]Hi,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have ubuntu 8.10 system. I have configured this system to work as network installation server. I would be installing Suse Enterprise 10 from this using PXE boot.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have configured following things as of now:[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]dhcpd server[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]2.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]tftp server[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]3.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]NFS &#8211; where I have mounted SuSE Enterprise 10 ISO image.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]When I boot client system and select PXE boot, I see that IP is been offered to the client machine. However client gives message below:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]&#8230;.PXE-E18: Server Response timeout[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have few doubts:[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]I think that tftp is not offering pxelinux.0 image to client.[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]2.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]I have atftp and tftp-hpa. I think there is some issue in configuration.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Should I remove atftp and just keep tftp-hpa?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I tried starting both serveices, I am not able to connect to 69 port [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Courier New][SIZE=2]telnet 192.168.1.1 69[/SIZE][/FONT] &#8211; Can&#8217;t connect to this port.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Should I able to do this? Is it mandatory?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3. However tftp command works.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Courier New][SIZE=2]tftp &#8211;v 192.168.1.1[/SIZE][/FONT] &#8211; I can download pxelinux.0 using get command.[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]4.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]I have used [FONT=Courier New][SIZE=2]pxelinux.0[/SIZE][/FONT] from ubuntu machine. Is that OK? I have copied all other files from SuSE.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]What all things are wrong in this setup?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Your help is really appreciated.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks and Regards,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Shashank[/SIZE][/FONT]

---

### Post by Shashankj on 2009-08-13
[SIZE=2]Hi,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I see message below in debug.log[/SIZE]
 
[FONT=Courier New][SIZE=2]cannot bind to local socket: Address already in use[/SIZE][/FONT]
 
[SIZE=2]I think, tftp is not starting at all.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]Regards,[/SIZE]
[SIZE=2]-Nilesh[/SIZE]

---

### Post by dcstar on 2009-08-13
> **Shashankj said:**
> [SIZE=2]Hi,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I see message below in debug.log[/SIZE]
 
[FONT=Courier New][SIZE=2]cannot bind to local socket: Address already in use[/SIZE][/FONT]
 
[SIZE=2]I think, tftp is not starting at all.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]Regards,[/SIZE]
[SIZE=2]-Nilesh[/SIZE]

Please STOP using ridiculous fonts, are you more important than anyone else posting in these forums?

You cannot install two packages trying to do the same thing, remove one of the tftp packages.

---

### Post by Shashankj on 2009-08-13
Hi,
 
I have removed atftpd. I can download file using tftp:
 
[EMAIL="test@test:~$"]test@test:~$[/EMAIL] tftp -v 192.168.1.1
Connected to 192.168.1.1 (192.168.1.1), port 69
tftp> get pxelinux.0
getting from 192.168.1.1:pxelinux.0 to pxelinux.0 [netascii]
Received 14928 bytes in 0.2 seconds [715499 bit/s]
tftp> quit

When I try telnet to 69:
test[EMAIL="test@test:~$"]@test:~$[/EMAIL] telnet 192.168.1.1 69
Trying 192.168.1.1...
telnet: Unable to connect to remote host: Connection refused
[EMAIL="test@test:~$"]test@test:~$[/EMAIL]
 
However client still not able to boot from this server. I see, dhcp is offering IP, but on client I see:
....PXE-E18: Server Response timeout.
 
 
How should I debug it?
 
Regards,
-Shashank

---

### Post by Shashankj on 2009-08-14
Hi,
 
Any idea what's wrong in the setup?
 
Help is really appriciated.,
 
 
Regards,
-Shashank

---

