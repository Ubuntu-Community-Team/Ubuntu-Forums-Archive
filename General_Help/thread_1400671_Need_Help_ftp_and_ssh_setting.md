---
title: "Need Help: ftp and ssh setting"
date: 2010-02-07
forum: General Help
---

### Post by nylee on 2010-02-07
Dear Ubuntu Users: 
 
I'd like to ask some help to fixe following problem. 
 
(Situation): I have a PC at home and two servers(call them Server_1, Server_2) at remote office. 
 
(Problem 1) After rebooting Server_1, the Server_1 is neither ftp-connectable nor ssh-connectable from home. But Server_1 is ssh- and ftp- connectable from Server_2. 
 
I'd like to ask what to do to make Server_1 is connectable from home. 
 
Since the Server_1 is connectable from Server_2, 'ftpd' and 'sshd' are not source of problem. By the way, I didn't put any firewall on Server_1. One strange thing is that by ssh-connecting Server_1 (through Server_2), I can make Server_1 ssh-connectable by doing
 
'/sbin/ifdown eth1'
'/sbin/ifconfig eth1 207.***.***.78'
'/sbin/ifup eth1'
 
But, this does not make ftp-connection work. 
 
Could you help me fix this problem ?
 
Thanks in advance
 
nylee

---

### Post by alarme on 2010-02-07
Server_1 and server_2 are in the same LAN?
If yes, you must change the ports for ssh and ftp on server_1, and configure properly NAT in router

---

### Post by nylee on 2010-02-07
Thanks for your reply

Let me explain the situation one more time. 

I have two servers(server_1, server_2) at office, and they have two lan cards(the first land card is connected to router, which forms an internal LAN, and the second lan card is connected to fixed IP).

(Problem) Server_1 is ssh-connectable from home PC(this has only dynamic IP), but not ftp-connectable from home PC. 

It is also ssh- and ftp- connectable from Server_2 by using the fixed IP of Server_1. 

It is also true that the Server_1 is ftp- and ssh- connectable from other PC that does not belong to the internal LAN(Server_1 belongs to), but has the same gateway number as Server_1 has.

Could you tell me what should I do to make Server_1 to be ftp-connectable from home ?

Thank you very much. 

nylee

---

### Post by gmargo on 2010-02-07
You've got to distill this into a better explanation.  You keep talking about ftp- and ssh-connectable, but I think you're really talking about port forwarding.  So forget ftp and ssh for the moment and just describe your network setup.  Here's a picture I drew from your explanation. It is chock full of my preconceptions of typical network setups, so please make corrections.  From your description I think you have your office router configured to forward SSH traffic to Server_1.  And I think you're asking how to forward FTP traffic to Server_1 as well.

Another point to consider is: do you need ftp?  If you have SSH working, you can use sftp or scp to transfer files.

```

OFFICE LAYOUT:

+----------+  "fixed IP??"
| Office   |-------------->???         +--------------+
| Server_1 |                           | Office       |
|          |---------------------------| Router &     |
+----------+ 172.16.1.2                | Firewall     |
                                       |              |    Internet
                                       | 172.16.1.1   |------////-----
+----------+ 172.16.1.3                | internal     |
| Office   |---------------------------|              |
| Server_2 |                           |   207.x.x.78 |
|          |-------------->???         |     external |
+----------+  "fixed IP??"             +--------------+



HOME LAYOUT:

+----------+
| Home     |                           +--------------+
| PC       |                           | Home         |
|          |---------------------------| Router &     |
+----------+ 192.168.1.100             | Firewall     |
                                       |              |    Internet
                                       | 192.168.1.1  |------////-----
                                       | internal     |
                                       |              |
                                       |      a.b.c.d |
                                       |     external |
                                       +--------------+


```

---

### Post by nylee on 2010-02-07
Thank you very much for your reply. 
 
In previous explanation, there are 4 computers and 2 routers. 
 
                             IP
Server_1                201.***.***.17(fixed ip)
                             192.168.1.3 - under Router_1(fixed ip: 201.***.***.32)
 
Server_2                201.***.***.18(fixed ip)
                             192.168.1.4 - under Router_1(fixed ip: 201.***.***.32)
 
3rd PC at Office      201.***.***.38(fixed ip)
                             Not under Router_1
 
PC at home             192.172.0.4 - under Router_2(no fixed ip)
 
# Connection is OK (using the fixed IPs of Server_1, Server_2, 3rd PC at Office)
PC at home --> Server_1(ssh), Server_2(ssh, ftp), 3rd PC at Office(ssh, ftp)
 
Server_2 --> Server_1(ssh, ftp)
 
3rd PC at Office --> Server_1(ssh, ftp)
 
# Connection is NOT OK
PC at Home --> Server_1(ftp) using the fixed IP of Server_1
 
Server_1, Server_2 and 3rd PC at Office are under the same Gateway 201.***.***.1.
 
The most curious thing to me is why Server_1 refuse ftp-connection from PC at Home while accepting ftp-connection from 3rd PC at Office. 
 
Again, thank you very much. 
 
nylee

---

### Post by cjhabs on 2010-02-07
This sounds like a router issue rather than Ubuntu.
FTP uses different ports for sending (control) and data, which causes problems with routers where typically they will only accept data on the port of an existing connection.

You can get around this by using passive mode ftp and forwarding the following ports on the server side router:
20-21 and 1024-65535

---

### Post by nylee on 2010-02-07
Dear Ubuntu Users:
 
I used the fixed IP address of Server_1, which is not under Router_1, and hence I thought 
 
if the Server_1 is ftp-connectable from '3rd PC at office' by using the fixed IP of the Server_1, 
 
then the Server_1 must be ftp-connectable from 'PC at Home' by using the same fixed IP of the Server_1. 
 
But, it didn't happen in that way. Because of this reason, I thought the source of problem is not in router. 
 
Server_1 and Server_2 are exactly same. But, I can do ftp-connection to Server_2 from Home PC, but cannot do ftp-connection to Server_1. I don't know why this thing happens. 
 
Thank you very much
 
nylee

---

### Post by nylee on 2010-02-08
[Partially Solved]
 
Thank you for replies. 
 
Somehow I solved the problem. Now the server at office is ftp connectable from Home. Strange thing is the fact that I don't what makes ftp work. 
 
I just reboot the server_1 and 'deactivate' and 'activate' the lan card in graphical tool. 
I thought that '/sbin/ifup' is 'activating lan card'. Maybe, I am wrong. 
 
I ma stii lokking for a clean answer for this problem, since ftp-disconnection happens quite often, and I want to fix it from home. 
 
Anyway, thank you very much.

---

