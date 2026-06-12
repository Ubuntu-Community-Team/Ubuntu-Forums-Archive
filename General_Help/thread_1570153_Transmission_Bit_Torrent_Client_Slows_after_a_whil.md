---
title: "Transmission Bit Torrent Client Slows after a while."
date: 2010-09-07
forum: General Help
---

### Post by octohedra on 2010-09-07
Heya!

Been downloading with this torrent client, i like it, a lot, and really dont want to download another one as i think its probably going to be the same, it starts @ full speed, then after some time, slows to 25% of the speed?

Strange... the seed/peer ratio is ok, so that shouldnt be a problem...

I tried scanning my ports, with no luck with ./testport (it said my ports where closed, and now i dont know why, it stopped working, so i cant even check them...)

So i installed the interface of the ubuntu firewall (dont remember its name lolol) and its currently ON, but allowing incoming and outgoing connections/traffic.

Is there any way to improvise the sspeed? Tyvm! ):P

---

### Post by kerry_s on 2010-09-07
try deluge, its the utorrent of linux bt apps. its in the repos.

---

### Post by wojox on 2010-09-07
Also have a look here. I've used lovinglinux's guides for optimizing both deluge and transmission. 

[BitTorrent optimization and troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by octohedra on 2010-09-07
Maybe my bandwith setup its not meant to use torrents, as i have 1Mb/s Dl speed, but 128Kb/s upload... (max 12 kb up)

---

### Post by kerry_s on 2010-09-07
> **octohedra said:**
> Maybe my bandwith setup its not meant to use torrents, as i have 1Mb/s Dl speed, but 128Kb/s upload... (max 12 kb up)

you can do torrents, it won't be as fast, but still usable.

---

### Post by octohedra on 2010-09-08
> **kerry_s said:**
> you can do torrents, it won't be as fast, but still usable.
cool, gonna try with deluge, and see how it goes

):P

---

### Post by cowboysaif on 2010-09-08
while trying, you can have a look on [www.btaccel.com](www.btaccel.com)

---

### Post by srs5694 on 2010-09-08
Also, some ISPs reportedly throttle BitTorrent speeds because they don't like the bandwidth consumption and/or because they've been pressured by copyright holders who think that only pirated material is transferred via BitTorrent. If you don't see the problem under another OS, then this likely isn't the explanation, but if you've only tried it under Linux, it could be the issue. What's your ISP? Perhaps somebody familiar with your ISP and/or with this issue would know whether your ISP does any BitTorrent throttling.

---

### Post by octohedra on 2010-09-09
In my country almost everything you do in the internet is legal, also, on windows i had some configurations that allowed me to dl @ my max broadband speed, but again, i dont know how to do it or if its going to work in linux.

):P

---

### Post by Rasa1111 on 2010-09-09
Transmission gave me more problems than it did good.
Always seemed to be one thing or another gone funky with it..
Now I use Deluge, and it's the best client Ive ever used, never with an issue. <3

---

### Post by kerry_s on 2010-09-09
> **Rasa1111 said:**
> Transmission gave me more problems than it did good.
Always seemed to be one thing or another gone funky with it..
Now I use Deluge, and it's the best client Ive ever used, never with an issue. <3


transmission works for some, not for others. once you figure it out it works just fine, for example: on mine transmission don't work good with my routers upnp enabled, once i turned it off, transmission now works great, torrents start as soon as i add them, i get full speed on my downloads, so much so that i have to throttle it or it consumes all the bandwidth so i can't browse the internet.
it took me sometime to figure it out, but now it's all good. ;)

---

