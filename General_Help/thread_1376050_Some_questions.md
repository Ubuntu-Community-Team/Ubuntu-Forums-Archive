---
title: "Some questions"
date: 2010-01-08
forum: General Help
---

### Post by Nova49 on 2010-01-08
I've got a couple questions about Ubuntu and servers and other stuff that I would like to know the answers too. I'm very new to Ubuntu and I feel like I'm missing out on a lot of the features with it. If there are websites that answer my questions please forward them because I cant find any. 

1. I keep on hearing on the internet about Linux and ubuntu servers. I was wondering if there was a way to turn a computer we have at home into a server that other computers can interact with on our home network. Such as sharing documents or other files which each other. Preferable freely. 

2. We have always had problems with our printer on our home network. Is there a way that I could set up a server so every computer in the house can print with out having to move a whole bunch of files around on flash drives. 

3. Is there a way to create a server that will host files for me that I can access anywhere. So I could access them any were from any computer over the internet. 

I feel like this is common knowledge but I cant seem to figure out how to do any of these things. I don't even know if you can do these things but I've seen other people doing stuff like it. I don't even know if server is the right word to call what I want to do, so I'm asking in general help instead of the server section of the forum.  
Thank you for your time and help.

---

### Post by ibuclaw on 2010-01-08
1) Yes. Look up Samba (or ask here about it :))
2) Yes, granted that your printer has a Network Card on it.
3) Yes - but you'd have to ensure:
[LIST=1]
[*]The router you are behind has DHCP turned off, and you configure all computers in your local network to have **static** IP addresses.
[*]You secure / lockdown your file server to keep the risk of intrusion to a minimum (ie: strong passwords).
[/LIST]

---

