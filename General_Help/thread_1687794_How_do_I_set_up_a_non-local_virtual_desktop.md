---
title: "How do I set up a non-local virtual desktop?"
date: 2011-02-14
forum: General Help
---

### Post by _eternal on 2011-02-14
Hi. I apologize in advance if this is too basic of a question, but I'm completely new to Linux and I've never even set up a virtual desktop on Windows so I'm not sure where to start. I noticed that there's a menu in Ubuntu to set this up, but I followed the instructions (can't remember what they were off hand) and it said that the computer was only accessible through a LAN. I want to leave the Ubuntu machine (my laptop) at home and be able to access it through my desktop (Win7) in college (long story but I don't think that matters). It's possible to do this, right? How would it be done? I understand that LogMeIn doesn't work with Linux, so I'm guessing I have to use Ubuntu's default virtual desktop program and a Windows program like TightVNC, but I'm not sure how to make the laptop accessible from something other than a local network.

---

### Post by mikewhatever on 2011-02-14
Take a look at Teamviewer.
[http://www.teamviewer.com/](http://www.teamviewer.com/)

The 'only accessible through LAN' message usually means that you are behind a firewall/router which doesn't allow incoming connections from the internet. In that case, making a firewall rule or forwarding a port in the router would be necessary.

By the way, the functionality you want is known as the Remote Desktop or remote access.

---

### Post by _eternal on 2011-02-14
Ahh, you're right, my mistake. I'll look into the firewall problem. Thanks!

---

### Post by _eternal on 2011-02-21
Okay, I forwarded port 5900 on my router and typed "sudo ufw allow 5900", which I believe would open that port through the firewall. I'm not using any other firewalls. Any ideas? The exact message I get is:

> Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.1.2 or **<name>**.local.(bolded part added by me of course)

---

### Post by BHEJU on 2011-02-21
Also, if you want to use vnc, then you will have to use the ip assigned to your home by your ISP. which is NOT 192.168.***.
You can find that ip in your routers config page. and use that ip in vnc from your dorm to connect to ubuntu @ home. Since you already forwarded the port, vnc will automatically go to your ubuntu machine.

Cheers

---

