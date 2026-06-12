---
title: "OpenVPN connected but not connected"
date: 2010-07-05
forum: General Help
---

### Post by veggen on 2010-07-05
I installed OpenVPN, placed conf, keys and certs into /etc/openvpn/. I did ```
sudo openvpn --conf /etc/openvpn/client.conf
```
and everything seemed alright, but when I actually try accessing something that I need VPN for, it doesn't work (it's the same as if I wasn't in VPN).
I also tried using GOpenVPN but the results are exactly the same.
I know the confs are ok as I use the exact same files on Windows 7 and everything's fine.
I even disabled ufw, restated machine etc, just to be sure.

Is there anything I might be missing or is this a curse from gods?

---

### Post by veggen on 2010-07-05
Anyone has OpenVPN?

---

### Post by The Cog on 2010-07-05
Need more info.

I believe that when OpenVPN hasd finished connecting, it says something like "initialisation sequence completed". Does it say that?

> when I actually try accessing something that I need VPN forDoes this mean you are trying to connect **through** the VPN server to something else? If so, are you sure the server is doing IP forwarding? Does it push the correct routes to the client? Are you trying to connect by name or IP address? What type of service is it?

---

### Post by veggen on 2010-07-06
> **The Cog said:**
> Need more info.

I believe that when OpenVPN has finished connecting, it says something like "initialisation sequence completed". Does it say that?

Yup, that's exactly what it says.
> **The Cog said:**
> Need more info.
Does this mean you are trying to connect **through** the VPN server to something else? If so, are you sure the server is doing IP forwarding? Does it push the correct routes to the client? Are you trying to connect by name or IP address? What type of service is it?
Well, I'm not that good with this VPN stuff, but here's how I'm using it.
I'm trying to access a company web site, reachable only from within the company or within VPN. I'm also using OpenVPN in Windows, with all the exact same conf/keys/certs, and when OpenVPN says it's connected, I can access the site through my browser (so I guess the server works perfectly). I'd like to achieve the same in Ubuntu, but after it says "initialization sequence completed", I type the URL and get the same "not available message". I tried both the gopenvpn and the command line (with the command mentioned above).

Did this help at all? If more info is needed, please give some advice on how to get it... I'm, as you can see, a total newbie to VPN.

---

### Post by cb951303 on 2010-07-06
I configured everything with NetworkManager and it works.

PS: Avoid checking "Available to all users", there is a bug with the password manager which ends up with VPN connection problems.

---

### Post by veggen on 2010-07-06
Well, I have no clue how to do manual setup... that's why I have all the confirugation already prepared. I tried dabbling with the NetworkManager, but for some reason it kept ignoring my tries to import the settings/keys. It wasn't giving any erros, just nothing happened. Anyway, the connection goes well when I just place everything inside /etc/openvpn/, so I'm guessing something else is the issue.

---

### Post by The Cog on 2010-07-06
I do this, and it works fine for me. So I think it must be a configuration issue of some sort, not merely software that doesn't work. 

Do you have a firewall running? 
You do leave the VPN command prompt window open, don't you?
Can you ping the web server while the VPN is connected?
Is your webs browser using a proxy?
What happens if you enter the command GET followed by the URL?
  e.g. GET [http://www.google.com/](http://www.google.com/)

---

### Post by veggen on 2010-07-06
> **The Cog said:**
> 
Do you have a firewall running? 

I did, but I specifically disabled it for this purpose.
> **The Cog said:**
> 
You do leave the VPN command prompt window open, don't you?

Of course.
> **The Cog said:**
> 
Can you ping the web server while the VPN is connected?

Nope.
> **The Cog said:**
> 
Is your webs browser using a proxy?

Nope.
> **The Cog said:**
> 
What happens if you enter the command GET followed by the URL?
  e.g. GET [http://www.google.com/](http://www.google.com/)
Connection times out...

Anyway, in order to keep my sanity, I decided to believe this some evil, previously undiscovered bug... From here, that sounds like the only way to go...

---

### Post by The Cog on 2010-07-07
I presume that "connection times out" means that GET was able to use DNS to resolve the hostname [www.google.com](www.google.com). That is a start. 

When you tried to ping the corporate server, was it able to get as far as resolving that address (puts the IP address in brackets)? 

From here, I would try to work out if I could ping the VPN server, but you have to work it out first. Looking at the IP address of the local tunnel interface (ifconfig) and then looking at the routing table (route -n) would be informative.

---

