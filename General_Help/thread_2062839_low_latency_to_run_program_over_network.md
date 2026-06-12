---
title: "low latency to run program over network"
date: 2012-09-25
forum: General Help
---

### Post by Fittersman on 2012-09-25
I'm trying to run the netbeans IDE over the network. I have it installed on my ubuntu laptop but I want to run the program on my Windows desktop. What method has the least latency? I just tried using openssh and putty+xming, but that has a noticeable latency I would think is possible to avoid somehow since my computers are connected directly via an Ethernet cable.

---

### Post by Fittersman on 2012-09-26
I just thought of a good solution.. Make my files accessible over the network and install netbeans on windows. However, for other people trying something similar but that won't work, try FreeNX. It was fairly fast, definitely usable

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by HiImTye on 2012-09-27
generally X11 forwarding over SSH is preferable to other protocols. I can't imagine much benefit to using FreeNX rather than just SSH, unless you have severe network issues. FreeNX is basically just ssh -x with compression

---

### Post by Rexilion on 2012-09-27
The NX protocol is like windows RDP in terms of performance. Using X forwarding is very inefficiënt since the X protocol has many unnecessary roundtrips.

Definitly go with NX if you can.

---

### Post by dcstar on 2012-09-27
If you have a solution then Mark the thread.

---

### Post by asmoore82 on 2012-09-27
> **HiImTye said:**
> generally X11 forwarding over SSH is preferable to other protocols.
It's actually rather deprecated it seems to me; and for some reason it's gotten painfully slow over the last few years even while computers and networks get faster. It seems like every dev. out there is hell-bent on breaking X11 forwarding permanently with the "next big step forward" in Linux graphics.

I use VNC and/or RDP - you can see the link in my signature for all the details. Another advantage to this is fault tolerance and persistence: Does the actual program die if the network hiccups? Can you leave it running and re-attach to it later? I never could meet any of the above with X11.

---

### Post by HiImTye on 2012-09-27
with VNC and RDP you're best to use it over SSH anyways, to avoid sending plain text. they also take considerable configuration if you want to use them headless. it's true that you can't 'resume' a program, but you also don't need to have an active session to start a program, SSH takes care of that.

---

