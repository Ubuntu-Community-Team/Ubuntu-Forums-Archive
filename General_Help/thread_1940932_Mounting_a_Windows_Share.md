---
title: "Mounting a Windows Share"
date: 2012-03-14
forum: General Help
---

### Post by Ubun2to on 2012-03-14
I have used Ubuntu 11.10 for awhile, and can't wait for 12.04 to be released (I have the beta on my laptop, and I love it).
Anyway, I am having problems mounting my Windows Server 2007 share drives on Ubuntu.
You may wonder why I am using Windows Server 2007-well, that's what's being used where I work, and the IT guy said the software we use won't work in Wine (although I'm willing to challenge those claims, as he is really lazy, so I think he's making that up).
So, I need to mount the network drives, and I can't figure out how.
I've tried mounting it via "Connect to Server" (Network folder>File). It either tells me to check my username and password or says it was unable to connect (and yes, I put that it was a Windows share).
I've tried to find some solution, but nothing has turned up.
As you have probably figured out by now, I'm not the most knowledgeable about Ubuntu. I'm more of a PC guy, but open source and free are the words I love to hear. Plus, about 2 minutes faster boot than Windows 7, and a much nicer interface.

---

### Post by dcstar on 2012-03-15
> **Ubun2to said:**
> 
.........
So, I need to mount the network drives, and I can't figure out how.
I've tried mounting it via "Connect to Server" (Network folder>File). It either tells me to check my username and password or says it was unable to connect (and yes, I put that it was a Windows share).
I've tried to find some solution, but nothing has turned up.
As you have probably figured out by now, I'm not the most knowledgeable about Ubuntu. I'm more of a PC guy, but open source and free are the words I love to hear. Plus, about 2 minutes faster boot than Windows 7, and a much nicer interface.

Places-Connect to Server-Windows Share with the IP address immediately brings up a username/domain/password dialog when I connect to Server 2003 or Server 2007 shares on my 10.04 system. Once I connect in I have all the access my user account allows.

Make sure you can ping the server first, and don't use DNS names unless you have that set up 100% correctly.

---

### Post by Ubun2to on 2012-03-25
> **dcstar said:**
> Places-Connect to Server-Windows Share with the IP address immediately brings up a username/domain/password dialog when I connect to Server 2003 or Server 2007 shares on my 10.04 system. Once I connect in I have all the access my user account allows.

Make sure you can ping the server first, and don't use DNS names unless you have that set up 100% correctly.

It doesn't work for me-I've pinged the server, and it's online.

---

### Post by imachavel on 2012-03-25
I'm afraid you'll have to think in OSI terms. But pings are always good. So you configured samba.conf on your host machine before connecting to server? I imagine you have. I myself cannot connect from one computer to another using each others i.p. address over my home i.s.p. router on my home LAN. Perhaps configuring your own server with dcpromo using dhcp and a fully qualified domain name is supposed to remove the necessity of configuring samba.conf? Well I don't know, but I'm pretty sure samba.conf must be configured, I've googled and it seems even to share a printer server between windows and a linux based kernel OS you need samba.conf configured.

If I'm wrong may the moderators come down from heaven and ban me and black list all my public i.p. addresses as they are shown somewhere in my connection to their server and log in

---

### Post by collisionystm on 2012-03-25
> **Ubun2to said:**
> I have used Ubuntu 11.10 for awhile, and can't wait for 12.04 to be released (I have the beta on my laptop, and I love it).
Anyway, I am having problems mounting my Windows Server 2007 share drives on Ubuntu.
You may wonder why I am using Windows Server 2007-well, that's what's being used where I work, and the IT guy said the software we use won't work in Wine (although I'm willing to challenge those claims, as he is really lazy, so I think he's making that up).
So, I need to mount the network drives, and I can't figure out how.
I've tried mounting it via "Connect to Server" (Network folder>File). It either tells me to check my username and password or says it was unable to connect (and yes, I put that it was a Windows share).
I've tried to find some solution, but nothing has turned up.
As you have probably figured out by now, I'm not the most knowledgeable about Ubuntu. I'm more of a PC guy, but open source and free are the words I love to hear. Plus, about 2 minutes faster boot than Windows 7, and a much nicer interface.


For the username it needs to be

computername\username

Computername being the name of the windows computer.

---

### Post by imachavel on 2012-03-25
right, if you don't know the computer name, don't forget it's easy to get by going to start, right clicking on my computer once you see it, going to properties, then advanced system settings, then computer name, or if you don't aren't using windows 7 or vista just properties, then computer name tab

or going to cmd and typing in:

Hostname

---

### Post by Ubun2to on 2012-03-25
> **imachavel said:**
> I'm afraid you'll have to think in OSI terms. But pings are always good. So you configured samba.conf on your host machine before connecting to server? I imagine you have. I myself cannot connect from one computer to another using each others i.p. address over my home i.s.p. router on my home LAN. Perhaps configuring your own server with dcpromo using dhcp and a fully qualified domain name is supposed to remove the necessity of configuring samba.conf? Well I don't know, but I'm pretty sure samba.conf must be configured, I've googled and it seems even to share a printer server between windows and a linux based kernel OS you need samba.conf configured.

If I'm wrong may the moderators come down from heaven and ban me and black list all my public i.p. addresses as they are shown somewhere in my connection to their server and log in

Too bad I can't get Samba to work to save my life.

---

### Post by Morbius1 on 2012-03-25
Just out of curiosity: From Ubuntu what is the output of the following command:
```
smbtree
```

---

### Post by Ubun2to on 2012-03-25
> **Morbius1 said:**
> Just out of curiosity: From Ubuntu what is the output of the following command:
```
smbtree
```

Can't find out until I get it to boot.
[http://ubuntuforums.org/showthread.php?t=1946741](http://ubuntuforums.org/showthread.php?t=1946741)

---

