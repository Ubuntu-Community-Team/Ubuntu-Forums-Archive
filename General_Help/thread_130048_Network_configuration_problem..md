---
title: "Network configuration problem."
date: 2006-02-15
forum: General Help
---

### Post by pagorek on 2006-02-15
Hello guys.
I am a linux and Kubuntu total noob. I've been configurating my network and deleted some 'aliases' like 'localhost' in configuration utility. Now i cannot use sudo and other commands (even put my password in KDE System Configuration). As result i cannot fix antything without sudo command. 
How to fix it?
My next question - i am trying to set up my network. Under Win XP it works correctly. I have good setting on my router (static IP) and port mapping, network, internet, just all - work good. How to set it up in Kubuntu? How to change my host name (because router - DLINK - doesn't recognize my host name from Linux and shows it as unknown - Windows host name works correct)?
Thx for help!

---

### Post by joey111 on 2006-02-15
well
$ **sudo pppoeconf** establishes a connection (just follow and do what it says)
$ **plog** reports status,
§ **poff** terminates it,
$ **if config ppp0** ->general interface info.

---

### Post by pagorek on 2006-02-15
Yeah, but as I said, I cannot use sudo at all. Shell shows error connected with 'gethostbyname' or something like that. And that is my first big problem, next thing is to configurate the network.

---

