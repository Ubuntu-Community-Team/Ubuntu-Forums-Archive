---
title: "Please help me set up openVPN"
date: 2010-12-16
forum: General Help
---

### Post by unbuntunewb on 2010-12-16
Hello,

I am running Ubuntu 10.04 from a desktop computer. I would like to be able to have this computer connect to the OpenVPN servers for secure browsing. Once I figure it out here I will get it on my laptop so I can feel safe at wifi hotspots. I really do not know much about this. I want my computer (A) to connect to OpenVPN (B). I dont know anything about point to point, bridging, etc. I dont want to network many computers I just want the computer I use to connect to OpenVPN. Does anyone know how to do this? I keep reading about clients and servers but I cant figure out if they are two separate computers. If my computer the client connecting to the server? Do I need to have my computer connect to another computer that then connects to OpenVPN? I am absolutely without knowledge on this. Please help!

:KS

---

### Post by cariboo on 2010-12-16
There is an openvpn howto [here]("https://help.ubuntu.com/community/OpenVPN"). You will need a seperate computer to use as a vpn server, or you can rent one.

---

### Post by unbuntunewb on 2010-12-16
Ive read all that but I didnt quite get what I was doing. Why do I need a second computer? can you give me the basics?

---

### Post by Absorbed on 2011-02-18
> **unbuntunewb said:**
> Ive read all that but I didnt quite get what I was doing. Why do I need a second computer? can you give me the basics?

Most of the time VPNs are used to browse the internet securely using an unsecure connection, like free wifi at a coffee shop. 

In order to do this, when you're at a coffee shop you create a secure connection to your home server, and then the server does your internet browsing for you and passes the webpages to you via a secured connection.

You need two computers because you need the server as well as the one you're using to connect. Of course, if you pay a VPN provider, then you connect to their server, and so then you only need one computer.

---

