---
title: "KK: where is the firewall?"
date: 2010-02-22
forum: General Help
---

### Post by XEyedBear on 2010-02-22
I am trying to use aMule, under 64 bit Kubuntu on KK. I get a low ID. When I try the connectivity test it fails. I am advised to: 'Make sure your firewall or router is allowing/forwarding this TCP service port....'.

I don't have any doubts about my router, since eMule works fine under Windows on my network.So I am persuaded to examine the firewall on my KK installation - except that I cannnot find it. 

Any clues?

In addition, how do I find the definition for my network card to be sure it is set to the correct IP address to match my router settings?

---

### Post by NCLI on 2010-02-22
First of all, you need to find out what port aMule is trying to access(I'd recommend using Bittorrent instead as it is safer though). 

Then run these commands in the terminal:

sudo ufw enable
sudo ufw allow <insert port here>

And you're done :) 

If you want a graphical way to edit the system firewall, you can install Firestarter from the Ubuntu Software Store.

---

### Post by jenaniston on 2010-02-22
iptables - in all linux - contain the firewall rules, 
so nothing in particular about Karmic Koala U9.10 or Kubuntu 9.10 - see:

[http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables)

Firewall rules were much easier to understand and configure for me by doing it all through the command line
 rather than having a gui network config manager - most people recommend the gui way though - 
but definitely use commands to save the firewall rules before making any changes - that is my advice with either method.

As it says in the Ubuntu link that follows . . . you can start by viewing your firewall rules with the command :

```
root@ubuntu:/# iptables -L
```[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

