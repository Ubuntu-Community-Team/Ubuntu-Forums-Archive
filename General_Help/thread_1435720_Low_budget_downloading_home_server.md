---
title: "Low budget downloading home server"
date: 2010-03-21
forum: General Help
---

### Post by papibe on 2010-03-21
Hi All,

I’m planning to relieve some of the load of my main desktop by getting a new machine dedicated exclusively to downloading (headless, Ubuntu server, transmission, etc).  The only way I can do this without breaking the bank (and getting my wife mad), is going very low budget. 

So far, I’ve thought of either buying a refurbished machine or building my own. Microcenter has refurbished Pentium 4 desktops at around $130-180 (512MB-1G RAM, 40G-80G HD). BYO is a bit more expensive. Even considering a AMD  Sempron 140 processor,  and other low priced components, I get to around $200.

Any other option?   I appreciate any suggestion, idea, etc.
Regards.

---

### Post by megahost on 2010-03-21
if all you are using it for is downloading/transmission and such, I would recommend a refurbished server.

---

### Post by tommynz1975 on 2010-03-21
if you join the yahoo email group freecycle
maybe you can get something for free.

---

### Post by asmoore82 on 2010-03-21
You might be interested in the link in my Signature.

---

### Post by soltanis on 2010-03-21
Excellent! You can run Linux systems on extremely low spec computers.

The minimum for xubuntu (which I suggest for the headless case) is 192 MB RAM to install but getting a computer with that these days shouldn't cost you much. For just downloading, nothing special like encoding/transcoding files, then I suggest 400 Mhz or better processor and a lot of disk space.

I also suggest SATA; but that is generally found in newer computers. PATA/IDE hard drives wont be as big but the computers you find them in will be much cheaper.

You can install the machine with a head and then take it off later (that's much easier than trying to do the whole install headless, although this is also possible). Once you have the base installation done, set up your ssh server, ssh in from your desktop and use apt-get to strip away useless things.

If you get a machine that can't manage the Ubuntu specs, you can go lower. DSL boots on very low spec machines and I've even heard of a Linux distro that can run in as few as 10 MB of RAM.

---

### Post by papibe on 2010-03-26
Thanks for all your replays. I went the refurbished way ($150 P4).

@ tommynz1975: I already joined my local groups, amazing stuff. Thanks for the tip!

@ asmoore82: thanks for the link, I'm sure it'll be good help in the next days.

@ soltanis: I got 512Mb RAM and 40Gb in HD, so I think I'll just use Ubuntu server (Karmic).

Regards.

---

