---
title: "torrent clients make internet inaccessible"
date: 2010-04-12
forum: General Help
---

### Post by Mr_Tricorder on 2010-04-12
I just recently installed ubuntu 10.02 beta 2 on my laptop (a Toshiba Satellite that I've had since late 2006 and run every version of ubuntu since Feisty Fawn on it).  Everything is working perfectly so far except that whenever I download using a torrent client, I can no longer access the internet through any other application.

My computer is still connected and the download progresses normally, and other devices can connect and stay connected to my home network without any problems.  This does not seem like a normal case of bandwidth hogging since other devices stay connected and running smoothly while every other application on ubuntu that accesses the internet drops connectivity completely even though it shows I'm still connected (and obviously am since the torrent client continues to download).

It doesn't matter which client I use.  I have tried it with deluge, transmittion, and utorrent through wine with the same results every time.  I have never had this problem with any previous versions of ubuntu, Windows, or any other devices on my home network.

Has anyone else had this problem?

---

### Post by 98cwitr on 2010-04-12
are you using UPnP or port forwarding?

---

### Post by jedlacks on 2010-04-12
I have that same problem and it actually knocks all the other computers off the internet as well.  they all show as connected, but they all grind to a standstill until I close the program.

UPnp or port forwarding? I have no clue :-)

---

### Post by ujjwalkp on 2010-04-12
Even I faced the same problem, there are two options to solve this

1> Change the torrent priority from your client (I use transmission)
2> Limit the download and upload speed to fix value. Lets say your broadband speed is 1 MBPS you can restrict upload and download to 50% of your total speed so that remaining bandwidth you can use. 

Second option works for me always. 

Cheers
Ujjwal

---

### Post by lovinglinux on 2010-04-13
Limit your UPLOAD speed to 80% of your UPLOAD bandwidth speed. That should solve the problem.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by Mr_Tricorder on 2010-04-13
> **lovinglinux said:**
> Limit your UPLOAD speed to 80% of your UPLOAD bandwidth speed. That should solve the problem.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

It seems like it's working so far.  Thanks.

---

### Post by tuxulin on 2010-04-13
the best bet is to buy a router that can do better a
management on the incoming bandwidth

Tux

---

