---
title: "Port 80 has become blocked - don't know how"
date: 2006-06-27
forum: General Help
---

### Post by Etoile on 2006-06-27
Somehow my port 80 has become blocked.  I haven't installed any firewalls, so I have no idea if this is from a hacker or what.  I also can't install Firestarter or anything else because you have to have port 80 open in order to access the package archive.  I've looked at my process list and I didn't see anything particularly helpful, but I also have no idea what I'm looking for.

Port 80 is the only one that's blocked - https, ssh, gaim, and gmail notify all work fine.  I'm currently writing in Lynx; I had to ssh to my web host to do so.

If anybody could help me that would be really outstanding.  I'm almost ready to go back to XP!  (I do have a dual boot system, and I have Zone Alarm for XP, but I don't think that matters, does it?)  AIM is the easiest and fastest way to reach me, because Lynx is such a pain.  I'm online as amanitadotnet if you've got any suggestions.

Thanks!

---

### Post by moore.bryan on 2006-06-27
as far as i know, firestarter is already installed in 6.06... try

username@ubuntu:~$ sudo firestarter
(when it asks, put in your password)

firestarter should pop up and you should be good from there... it could also be your isp blocking port 80; that, apparently, is a common problem.

---

### Post by Simian on 2006-06-27
[QUOTE=moore.bryan]as far as i know, firestarter is already installed in 6.06... try

username@ubuntu:~$ sudo firestarter
(when it asks, put in your password)

firestarter should pop up and you should be good from there... it could also be your isp blocking port 80; that, apparently, is a common problem.[/QUOTE]

I didn't think that firestarter is installed by default. If it isn't you can install it:
```
sudo apt-get install firestarter
```

I think that allowing trafic to port 80 will be easier to configure with firestarter than doing it manually with iptables.

Or is it you router blocking port 80?

---

### Post by johnc4510 on 2006-06-27
This command will tell you what programs are listening at  which ports:
sudo netstat -lp

---

### Post by Etoile on 2006-06-27
I don't already have firestarter; I also can't install it because the connection to the archive requires it to go over port 80.  I ran the netstat command but I don't see port 80 mentioned anywhere.  This is the result of **sudo iptables --list**:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
So I have no idea if that has anything to do with it...is there something I can do in iptables to make this work so I can at least download Firestarter for the next time this happens, if it ever does?

---

### Post by Simian on 2006-06-27
Are you behind a router. Is the router blocking port 80 or iptables?

---

### Post by Etoile on 2006-06-27
Bingo!  Whew, that was a pain.

I figured I would boot into XP to get the .deb package for Firestarter, and then mount my XP drive in Ubuntu so I could install it.  When I opened up Firefox in XP, I discovered it was having the exact same problem.  I realized then that it must be a router issue, so I went into the router config and reset it.  Once it came back up, everything was fine.  I'm still in XP for the moment but I'm going to head back to Ubuntu and make sure everything's working - which I imagine it will be.

This turned out not to be an Ubuntu problem at all - sorry about that!

---

### Post by moore.bryan on 2006-06-28
i'm glad to hear you haven't given up on ubuntu!  :-)

---

