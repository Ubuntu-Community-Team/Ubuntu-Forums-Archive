---
title: "Is the connection to my computer blocked?????"
date: 2009-11-05
forum: General Help
---

### Post by quimica on 2009-11-05
Hey community:

 I still have a problem because i can not connect to my machine from another machine (the message is port 22: connection refused) even the openssh is installed and i used the command 'ufw allow' to permit the access through port 22.

I really don't have idea why i can not connect, please help me.

---

### Post by Commander_Keen on 2009-11-05
Lets start with the basics.. can you ping the PC?

---

### Post by doas777 on 2009-11-05
if you can ping, the next step is to test the port. run 
```
 telnet <targethost>  22
```
and post the output.

---

### Post by Iowan on 2009-11-05
> **quimica said:**
> (the message is port 22: connection refused) even the openssh is installed Is it running? Check [B]ps -ef |grep ssh
[/B]

---

### Post by alphacrucis2 on 2009-11-05
> **quimica said:**
> Hey community:

 I still have a problem because i can not connect to my machine from another machine (the message is port 22: connection refused) even the openssh is installed and i used the command 'ufw allow' to permit the access through port 22.

I really don't have idea why i can not connect, please help me.

'Connection refused' most likely means that you don't have an SSH server running on the machine you are trying to connect to.

Edit: Whoops I see Iowan beat me to it.

---

### Post by XCan on 2009-11-06
Are you using a router as well?

---

### Post by HiImTye on 2009-11-06
make sure that:

[LIST]
[*]you are running the correct server programs
[*]your router is set to allow the traffic
[*]your ISP does not block those ports
[*]you are using your actual IP not your LAN IP
[/LIST]

---

### Post by quimica on 2009-11-06
> **Commander_Keen said:**
> Lets start with the basics.. can you ping the PC?
1.- About the ping: Yes i can ping my PC (PC1) and the other PC (PC2), where PC2 is the computer from i try to connect to my PC1.
2.- About the telnet <targethost> 22: Using the command in the PC2 to check the connection with PC1 the message is:
Trying <targethost>
telnet: Unable to connect to remote host: Connection refused
3.- About the **ps -ef |grep ssh **i checked in PC1 and the message is something like that:
6588  6587  0 13:37 pts/0    00:00:08 /usr/bin/ssh -oForwardX11 no -oForwardAgent no -oPermitLocalCommand no -oClearAllForwardings yes -oProtocol 2 -s <targethost> sftp

---

### Post by quimica on 2009-11-06
> **doas777 said:**
> if you can ping, the next step is to test the port. run 
```
 telnet <targethost>  22
```and post the output.
1.- About the ping: Yes i can ping my PC (PC1) and the other PC (PC2), where PC2 is the computer from i try to connect to my PC1.
2.- About the telnet <targethost> 22: Using the command in the PC2 to check the connection with PC1 the message is:
Trying <targethost>
telnet: Unable to connect to remote host: Connection refused
3.- About the **ps -ef |grep ssh **i checked in PC1 and the message is something like that:
6588  6587  0 13:37 pts/0    00:00:08 /usr/bin/ssh -oForwardX11 no -oForwardAgent no -oPermitLocalCommand no -oClearAllForwardings yes -oProtocol 2 -s <targethost> sftp

---

### Post by quimica on 2009-11-06
> **Iowan said:**
> Is it running? Check [B]ps -ef |grep ssh
[/B]
1.- About the ping: Yes i can ping my PC (PC1) and the other PC (PC2), where PC2 is the computer from i try to connect to my PC1.
2.- About the telnet <targethost> 22: Using the command in the PC2 to check the connection with PC1 the message is:
Trying <targethost>
telnet: Unable to connect to remote host: Connection refused
3.- About the **ps -ef |grep ssh **i checked in PC1 and the message is something like that:
6588  6587  0 13:37 pts/0    00:00:08 /usr/bin/ssh -oForwardX11 no -oForwardAgent no -oPermitLocalCommand no -oClearAllForwardings yes -oProtocol 2 -s <targethost> sftp

---

### Post by doas777 on 2009-11-06
your port is not open. are you connecting through a router? if so you will have to forward your port 22 (i recomend using a differant port number on the outside).
if not, install gufw and open the port with it.

good luck

---

