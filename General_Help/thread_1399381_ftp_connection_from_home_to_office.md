---
title: "ftp connection from home to office"
date: 2010-02-05
forum: General Help
---

### Post by nylee on 2010-02-05
Dear Ubuntu users
 
I'd like to ask some help on following problem. 
 
(Situation) I have 1 computer at home, and 2 computers at office. Each computer at office has fixed ip address, and is ftp-server and ssh-server. Let two computers at office be called as 'Server_1' and 'Server_2'. 
 
Question 1: I am using 'konqueror' as ftp client at home to connect to Server_1 and Server_2, but the response speed from Server_1 and Server_2 are differnt. 
 
Server_1 response quickly since it does not ask the login information for each dounload, but Server_2 asks login information for each download action. Which configuration file should be modified and how ? 
 
Question 2: Server_1 was stalled during downloading. So cancelled the download. After that, I cannot ftp to Server_1 from home, but I can ftp Server_1 from Server_2(I ssh to Server 2 and use ftp command at Server_2). How this thing can happen ? 
How Can I fixe it ? I tried to '/sbin/ifconfig' command the network to be re-activated. Thta didn't help at all. By the way, I didn't use any kind of firewall. 
 
Could you help me ?
 
Thanks in advance
 
nylee

---

