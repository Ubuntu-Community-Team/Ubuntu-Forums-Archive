---
title: "Red5 Installation Ubuntu Server"
date: 2010-05-14
forum: General Help
---

### Post by fmartinez78228 on 2010-05-14
Has anyone successfully installed a Red5 server on they're Ubuntu Server and had it successfully connect with outside clients. 
I've followed the basic installation for Red 5 and got the server up and running, I've installed the Demo apps and am able to browse to the Red 5 home page on port 5080. I've opened up the following ports: 1935, 5080, and 8088 and have them directed to the Red 5 Server. 
Problem: I can't connect to the Server from a client. I can't even connect locally within my own network. In the demos I substitute "localhost" for myip:1935. Ex: rtmp://myip:1935/SOSample and this is the out put on the server: 
-----------------------------------------------------------------
[INFO] [NioProcessor-1] org.red5.server.net.rtmp.RTMPHandler - Scope SOSample not found on fmartinez.dtdns.net
[WARN] [Red5_Scheduler_Worker-2] org.red5.server.net.rtmp.RTMPConnection - Closing RTMPMinaConnection from 24.153.189.146 : 3706 to fmartinez.dtdns.net (in: 3440 out 3215 ), with id 1580255587 due to long handshake
-----------------------------------------------------------------

any one have any idea on how to resolve this. I've searched but have come up with no answers.

---

### Post by fmartinez78228 on 2010-05-14
*Bump*

---

### Post by fmartinez78228 on 2010-05-14
??**Anyone**??

---

### Post by tapas_mishra on 2010-08-03
I have done it.
Read the complete method [here]("http://mightydreams.blogspot.com/2010/08/installing-red5-on-ubuntu-904-32-bit_01.html")

---

