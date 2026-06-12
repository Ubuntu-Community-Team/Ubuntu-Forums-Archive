---
title: "Openssh - putty man in the middle paranoia"
date: 2009-08-13
forum: General Help
---

### Post by mox386 on 2009-08-13
Ok here it goes. Openssh server and putty client fingerprints match, but not so when prompted after starting client session, possible man in the middle attack on a fire walled network.
   
  The Setup: I’m trying to set up an openssh server on one of my machines at home. I have a hardware firewall on my router that I depend on for protecting my entire home network. I have a machine that I have installed ubuntu on and intend for it to be an always on weather display/ proxy server so I can browse encrypted from anywhere. I’ve also got other machines on this network and I forwarded a port (22) from the router to this machine.
   
  The Problem: No matter what I try I cannot get the fingerprint on the putty client to match the fingerprint that both Putty-keygen and ssh-keygen say that the public key has. I went so far as to install a clean install on the ubuntu box, this only changes what the wrong fingerprint is, as I tried it 3 times. I changed my ip (I have a dynamic IP) this did nothing. It’s always the same fingerprint no matter what the public key is. It even gives this fingerprint when I connect directly from one computer on the network to another using the local IP. I turned off all machines and disconnected the outside network and it still gave this wrong fingerprint when I started the session. The thinking behind this was that if there was a man in the middle he would be gone if only the router, and two computers were capable of talking. I even got familiar with wireshark on the ubuntu box and all the MAC addresses line up correctly.
   
  The Paranoia: I’m convinced that somehow somebody is man in the middle attacking me, the only problem is that can’t prove it, and I have no clue on how to stop it if it was. I’ve gone to extreme lengths to try to figure this out, and it’s good for me learning ubuntu because these things are hardcore for a fairly new user. However, I need some help in solving this one as it appears nobody else has this problem. 
   
  The Despair: So basically how do I get this prompt to give me the correct fingerprint, and if I (or anyone) knows that we’re being MITM attacked how do we thwart it.

---

### Post by mox386 on 2009-08-13
just to clarify the public key fingerprint on the openssh server is the same as the private key fingerprint on the putty client.

And I've also tested this behavior on another linux box I have laying around that I intend on turning into a web server once I iron out this thing.

---

### Post by Brandon Williams on 2009-08-15
You should avoid opening a new thread for an issue that you already have an active thread for. Please see your existing thread for details about the keys.

Regarding detecting MITM attacks, if you have disconnected the router from the internet and no other computers are connected to your LAN (use ethernet instead of WIFI if you want to be absolutely sure about that), then this is not a MITM attack. Even if you _are_ connected to the internet, an attacker would still need to be connected to your LAN for a successful MITM attack. It's unlikely that this is the problem, because such attacks are quite difficult to pull off. It's more likely that you are still having trouble with the SSH keys. If it really is a MITM attack, then you need to figure out how the attacker got onto your network and then kick them off.

---

### Post by mox386 on 2009-08-15
Apologies, problem solved in thread:

[http://ubuntuforums.org/showthread.php?t=1234638](http://ubuntuforums.org/showthread.php?t=1234638)

---

