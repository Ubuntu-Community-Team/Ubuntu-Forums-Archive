---
title: "Lantronix Xport support"
date: 2009-07-07
forum: General Help
---

### Post by bbubble62 on 2009-07-07
Hi,
 
I would like to use some Xport modules from Lantronix using Ubuntu 8.04 LTS.
Sepcially the port redirection functionallity but cannot find a reference to it.
 
Has anyone tried (and succesfully used) it ?
 
-ben

---

### Post by danwood76 on 2009-07-07
Looking on their site I see no reason why it wouldnt work.
It connects through telnet or a serial terminal.

What exactly are you trying to achive?

---

### Post by bbubble62 on 2009-07-08
I'm trying to get a serial adapter to work using a lantronix box.
I found on the web :  
 
[INDENT]socat PTY,link=/dev/XPort TCP:192.168.1.83:10001

[/INDENT]problem is that socat is waiting to be terminated and I thought it would open a link and redirect it to /devXport
 
any idea ?
 
-ben

---

### Post by danwood76 on 2009-07-08
No idea about socat.
You could try using remtty, this utility is specifically designed to use a tcp port like a tty (pty)

Mind you I have no experiance with these Xports.
I know that we used some port servers at work which used very simple TCP packets to deliver data to multiple ports but we wrote the drivers ourselves.

---

