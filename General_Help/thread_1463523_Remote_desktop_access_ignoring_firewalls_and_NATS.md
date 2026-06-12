---
title: "Remote desktop access ignoring firewalls and NATS"
date: 2010-04-27
forum: General Help
---

### Post by bigred1 on 2010-04-27
How can I get remote desktop access ignoring firewalls and NATs? I succeeded in creating a remote desktop session within my home LAN. 

Though I configured my router to pass through port 5900, and learned the correct external IP, I am unable to create a remote desktop session inbound to my machine, nor outbound to a machine on a remote network (with static IP).


This is caused by various network complications like NATs and firewalls.

Fogcreek's Copilot or Skype on Windows manage to connect with no network reconfiguration. 

Is there some remote desktop alternative that "just works"?

---

### Post by P4man on 2010-04-27
If you correctly configured the router(s) and firewalls, then remote desktop really just works, assuming the port is not blocked by a router or firewall outside your control.

It might be helpful if you could describe your usage scenario in a bit more detail, because there are indeed other ways to circumvent such problems, or if you have no control over part of the network. You can set up a reverse ssh tunnel if its okay to initiate the connection from the computer you want to connect to (the 'server"). If that "server" is being operated by a human being (say someone who needs your help and wants to share his screen) then have a look at gitso:

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

which uses reverse ssh to tunnel vnc and works just like for instance skype.

If you want to initiate the connection automatically, without user input on the server, either figure out what you are doing wrong with the network setup, or look in to establishing reverse ssh tunnels (does require static IP or some no-ip workaround on the *client*, since the server will be establishing a connection to it).

---

### Post by bigred1 on 2010-04-27
Thank you for the reply. The person on the other side is quite non- technical and so I cannot learn more about his setup or ask him to take technical steps. On my side, I have an ordinary DLink wireless router (which I configured with port passthrough) and an out-of-the-box Ubuntu Karmic.

Also, and less importantly, I have a Windows machine which I can use to experiment as client, whether inside my LAN or outside.

---

### Post by P4man on 2010-04-27
> **bigred1 said:**
> Thank you for the reply. The person on the other side is quite non- technical and so I cannot learn more about his setup or ask him to take technical steps. On my side, I have an ordinary DLink wireless router (which I configured with port passthrough) and an out-of-the-box Ubuntu Karmic.

Also, and less importantly, I have a Windows machine which I can use to experiment as client, whether inside my LAN or outside.

Use gitso. Its available for windows and linux (it has .deb package) and is drop dead easy to use. Just give that person your public IP and let him click on "get help". if there is no firewall blocking stuff on your end, it will just work.

---

### Post by bigred1 on 2010-04-28
Thank you. I experimented with both VNC and gitso using my own computers. I will now try to connect to the other person.

I'd still say that a zero-config option like Skype  or CoPilot would be a very good thing.

(By the way, a tip: Even if you configure your router to correctly passthrough the port for VNC and/or Gitso, you will not be able to connect from a computer inside your LAN to a computer inside your LAN using the public IP address, as you might try to do to verify your setup.)

---

### Post by P4man on 2010-04-28
> **bigred1 said:**
> Thank you. I experimented with both VNC and gitso using my own computers. I will now try to connect to the other person.

I'd still say that a zero-config option like Skype  or CoPilot would be a very good thing.

(By the way, a tip: Even if you configure your router to correctly passthrough the port for VNC and/or Gitso, you will not be able to connect from a computer inside your LAN to a computer inside your LAN using the public IP address, as you might try to do to verify your setup.)

gitso is rather zero config Id say ?

Also, I think you are doing something wrong. it should work on your local lan using your public IP. But you dont only have to open the port, you have to **forward** it to the IP of your PC (or put your PC in the DMZ). Ill test in a bit to see if Im not terribly mistaken, but I can ssh from one PC to the other using public IP , so I dont really see why VNC wouldnt work.

---

### Post by CharlesA on 2010-04-28
> **P4man said:**
> gitso is rather zero config Id say ?

Also, I think you are doing something wrong. it should work on your local lan using your public IP. But you dont only have to open the port, you have to **forward** it to the IP of your PC (or put your PC in the DMZ). Ill test in a bit to see if Im not terribly mistaken, but I can ssh from one PC to the other using public IP , so I dont really see why VNC wouldnt work.

Are you using the public IP from within the same LAN?

I'm curious as how that is setup, since I can only use the local IP to connect via SSH on the local LAN. Using the external IP doesn't do anything (same thing as getting a busy signal I assume).

Anyway, if you are going to expose VNC to the internet, please use a very very strong password. VNC is probably responsible for 90% of "hacked" boxes.

I'd just using SSH and forward VNC over it, but that's probably going to be a pain to set up if you have a non-tech user on the other end.

---

### Post by P4man on 2010-04-28
Okay just tested with gito using my public IP. No problems at all. On the router I only forwarded port 5500 to the internal IP of the  PC running gitso as "give support"

---

### Post by bigred1 on 2010-04-28
> **P4man said:**
> gitso is rather zero config Id say ?


Yes, in most cases. But if there is a NAT at my ISP which I do not control, it won't work.

> **P4man said:**
> 
..., you have to **forward** it to the IP of your PC (or put your PC in the DMZ)
Yes, I forwarded too.

> **P4man said:**
> ...but I can ssh from one PC to the other using public IP , so I dont really see why VNC wouldnt work.
You would think so. But it was not working. Specifically, I got dialogs saying a connection was being formed, but I never got as far as screen sharing. Could it be that BOTH sides form sockets on 5900 (5500 for Gitso) and since I can only forward to one side, the connection never gets beyond the initial handshake?

---

### Post by P4man on 2010-04-28
> **CharlesA said:**
> Are you using the public IP from within the same LAN?

Yes, now for testing.

> 
I'm curious as how that is setup, since I can only use the local IP to connect via SSH on the local LAN. Using the external IP doesn't do anything (same thing as getting a busy signal I assume).

You have to configure your router to forward your ssh port to the (internal!) ip address of the pc you want to reach
> 
Anyway, if you are going to expose VNC to the internet, please use a very very strong password. VNC is probably responsible for 90% of "hacked" boxes.
Dont worry. Its not open usually, just opened it now for testing. And yes, I have seen a worm/bot/script once asking permission to connect when I had a 3 letter password. I allowed it and it started "typing" a windows command to download something from an infected ftp server, giving me the login and password to access it lol.

---

### Post by bigred1 on 2010-04-28
> **CharlesA said:**
> Are you using the public IP from within the same LAN?



I tried that as an test of the public IP address, to check that there was no additional NAT out there.

> **CharlesA said:**
> 
I'm curious as how that is setup, since I can only use the local IP to connect via SSH on the local LAN. Using the external IP doesn't do anything (same thing as getting a busy signal I assume).

That is in effect what I got with VNC and Gitso.

---

### Post by P4man on 2010-04-28
> **bigred1 said:**
> Yes, I forwarded too.

You would think so. But it was not working. Specifically, I got dialogs saying a connection was being formed, but I never got as far as screen sharing. Could it be that BOTH sides form sockets on 5900 (5500 for Gitso) and since I can only forward to one side, the connection never gets beyond the initial handshake?

Nope, cant be. That would never work. Maybe there is a nat router between your LAN and the network the public IP belongs to? in that case.. you might be in trouble.

---

### Post by jerome1232 on 2010-04-28
> **P4man said:**
> gitso is rather zero config Id say ?

Also, I think you are doing something wrong. it should work on your local lan using your public IP. But you dont only have to open the port, you have to **forward** it to the IP of your PC (or put your PC in the DMZ). Ill test in a bit to see if Im not terribly mistaken, but I can ssh from one PC to the other using public IP , so I dont really see why VNC wouldnt work.

Some nat devices aren't capable of letting a computer inside the lan use the public ip to "loopback" into the lan (if you get what I mean). Other nat devices are capable of this feature. I know my router can't do it.

---

### Post by P4man on 2010-04-28
> **jerome1232 said:**
> Some nat devices aren't capable of letting a computer inside the lan use the public ip to "loopback" into the lan (if you get what I mean). Other nat devices are capable of this feature. I know my router can't do it.

Aha. Thats good to know. Here is me thinking *I* had a crappy router lol. Well, lets just hope then that is the issue the OP has.

---

