---
title: "ufw firewall setup"
date: 2011-08-03
forum: General Help
---

### Post by rng on 2011-08-03
I run ubuntu on home pc and am very happy with it. I use internet to surf and to see my email on gmail.com etc. What commands should I give to setup ufw firewall so that only this much is allowed? Also, where can I see if some other connections have been blocked?

Thanks for your help.

---

### Post by Enigmapond on 2011-08-03
This may be of some help to you. [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

The default setting is to deny everything not initiated by you. Simply do:

```
sudo ufw enable
```in the terminal and it will always start. If you need a good GUI for iptables, try gufw.

Cheers!

---

### Post by rng on 2011-08-03
Thanks for your reply. Glad to know it is as simple as this. How do I check after a few days if something has being blocked?

---

### Post by Frogs Hair on 2011-08-03
You could install the GUI from the software center(gufw) and enable logging . You can view the log in the log file viewer . I found the logs get pretty long over time and have chose to disable that option .

---

### Post by rng on 2011-08-03
I enabled ufw and checked the status (verbose): 

Status: active
Logging: on (medium)
Default: deny (incoming), allow (outgoing)
New profiles: skip


Is it sufficient? It is allowing all outgoing calls. And what is this 'New profiles: skip'?

---

### Post by 3rdalbum on 2011-08-03
> **rng said:**
> I run ubuntu on home pc and am very happy with it. I use internet to surf and to see my email on gmail.com etc. What commands should I give to setup ufw firewall so that only this much is allowed?

If you haven't enabled anything that accepts incoming connections (such as Remote Desktop, SSH or any server software) then you don't even need a firewall because nothing is listening for incoming connections on your computer.

> Also, where can I see if some other connections have been blocked?

Don't bother. There's so much malware on the internet trying to find infectable Windows computers, that you can barely go five minutes without an attempted incoming connection.

Of course, there's no program listening for connections on a default install of Ubuntu, so the incoming connection fails every single time, and is nothing to worry about.

Computers are intended to make your life easier, and worrying about every unsuccessful intrusion every five minutes will simply take up too much of your time, and is absolutely no cause for concern. If you have no outward-facing services running, you are exactly as safe as if you had a firewall as this is what a firewall does.

Web and e-mail, from your point of view, uses outgoing connections, not incoming connections, so it's not like "there's a short window while checking my e-mail when I can be attacked". Use precautions such as common sense, and maybe the NoScript extension for Firefox.

In short: For what you're doing, and since you're using Ubuntu, you don't need a firewall.

---

### Post by rng on 2011-08-03
Thanks for your detailed reply. 

My concern is following: I install additional programs for productivity and office use. I want to see/block if they are trying to send back info etc. Also, I want to prevent malware from getting into my system and connect to internet etc. 

Can I configure ufw to allow connections only from firefox only and from no other program? If not, is there any other firewall which can do the same?

Thanks again.

---

### Post by bodhi.zazen on 2011-08-04
> **rng said:**
> Thanks for your detailed reply. 

My concern is following: I install additional programs for productivity and office use. I want to see/block if they are trying to send back info etc. Also, I want to prevent malware from getting into my system and connect to internet etc. 

Can I configure ufw to allow connections only from firefox only and from no other program? If not, is there any other firewall which can do the same?

Thanks again.

Well, this is Linux not windows, so things do not work the same way.

First, and most important, relax, the kind of malware you are concerned with does not really exist in Linux.

If that is just not sufficient for you, and you really want to watch your connections, and you are new to Linux, try a sniffer such as wireshark.

If you want a tool to filter through all your thousands of packets, and alert you of suspicious activity , use snort.

Linux does not use application firewalls, so you can not limit access to port 80, or "the internet" to firefox only.

If you want fine grained control over your firewall, use iptables.

I also highly suggest you read the security sticky ;)

---

### Post by rng on 2011-08-04
> **bodhi.zazen said:**
> Linux does not use application firewalls, so you can not limit access to port 80, or "the internet" to firefox only.

Thanks for taking the time to reply. There are programs available in linux for almost everything. Is there an application specific firewall? It would be great if I could simply give the following commands: 

sudo ufw deny all
sudo ufw allow firefox

Is this possible thru any firewall program in linux. If not, I wonder why.

---

### Post by bodhi.zazen on 2011-08-04
> **rng said:**
> Is this possible thru any firewall program in linux. If not, I wonder why.

There have been a few attempts at such an application, but, no one has written one I would advise.

Why not ? Well, Linux  is not windows and we have a different security model ;)

---

### Post by rng on 2011-08-04
Thanks for your comments. I am trying to setup ufw. What commands should I give so that only browsing the internet and to email sites such as gmail.com, yahoo.com etc is allowed? From what I could gather, it should be: 

sudo ufw default deny
sudo ufw enable
sudo ufw logging on
sudo ufw allow www
sudo ufw allow https


What other commands should I give?

---

### Post by 3rdalbum on 2011-08-04
> **rng said:**
> Thanks for your comments. I am trying to setup ufw. What commands should I give so that only browsing the internet and to email sites such as gmail.com, yahoo.com etc is allowed? From what I could gather, it should be: 

sudo ufw default deny
sudo ufw enable
sudo ufw logging on
sudo ufw allow www
sudo ufw allow https


What other commands should I give?

You're thinking in the Windows mindset. You don't need an outbound firewall. Software installed from the Ubuntu repositories is able to be trusted; firstly because it's guaranteed unchanged from the time it was uploaded to the repository, and secondly because it's open-source and any malicious code inside it would be found by other contributors.

You're really just trying to make more work for yourself.

Sleep easy. Unlike Windows, Linux is not a security nightmare. Per-application outbound firewalling makes some sense when malware could get onto your computer, but none when it's so incredibly unlikely.

I don't even think there's per-application outbound firewalling on Linux like what you mention, because it would simply be a waste of developer effort to implement it. It's completely unnecessary here. **Think about it: If your computer is compromised by malicious code, why wouldn't it just turn off your firewall?**

---

### Post by rng on 2011-08-04
> You're thinking in the Windows mindset

There are so many things that are common in two operating systems, then why not application based firewall?

> Software installed from the Ubuntu repositories is able to be trusted

I may be installing other linux software. Also, if I run portable or other windows programs thru wine, they may also misuse the network services. 


> Per-application outbound firewalling makes some sense when malware could get onto your computer, but none when it's so incredibly unlikely.

Unlikely does not mean never. With the increasing popularity of linux, the malware is bound to increase. 


> Think about it: If your computer is compromised by malicious code, why wouldn't it just turn off your firewall?

That can happen in windows applications also; why are they so successful. 

I am a great fan of ubuntu. However, I am not very convinced with the firewall approach. It is likely to be due to the fact that I do not know enough about linux, but I have not found satisfactory explanation for the same.

---

### Post by gratou on 2011-08-16
I totally agree with rng.

There is no such thing as too much security. Saying "it won't happen", "we are much better than xxx and don't need yyy" is too complacent imho, especially when security is concerned.

Wanting to control who can connect where, how and when seems like a very sensible request. 

And this has nothing to do with the Windows mindset. I also use OSX, and have used solaris (called SunOS at the time), AIX, HP-UX and even VMS (RIP) in my time.

IP tables are powerful, though not that user-friendly, but they lack basic features like "only FF can use port 80, and only from 8 to 18". That's what app FWs are good at.

As for a rogue app turning the FW off, thankfully the security scheme in linux is much better than windows' spaghetti mess, and this is less likely to happen. 
Also , I reckon this is a lazy justification. By the same token, rogue apps would alter iptables and change passwords, so why bother having iptables and passwords?  :)

Anyways, my 2 cents, not that it matters or makes a difference. ;)

---

