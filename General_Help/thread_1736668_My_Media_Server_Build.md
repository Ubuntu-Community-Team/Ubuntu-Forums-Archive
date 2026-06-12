---
title: "My Media Server Build"
date: 2011-04-22
forum: General Help
---

### Post by Don0918 on 2011-04-22
Finally decided to plunge in and assemble myself a PC server that runs Ubuntu 10.10.

After numerous weeks of reviewing hardware specs, I managed to buy the following:

Intel i3 2120 processor 3.30GHz
ASUS P8H67-M Motherboard
4Gig RAM
1 TB Western Digital Caviar Blue HDD 6Gb/s
Coolermaster casing


Not much, but I believe it's enough for my purposes - a PC server that will primarily serve mp3 files to my Squeezeboxes all over our house, video to my A/V receiver for my home theater, media files and documents to our iPads and iPhones not to mention typical file server for our laptops.

With the amount of load that this server will be doing - especially during peak hours - do you think the specs are enough?

I've never used Ubuntu before - or any Unix-like OS for that matter - and I must admit that I am pretty much excited to try my hand on this.

I've finally set-up and run x11vnc via SSH (this is what I use primarily to manage my system since I am running it headless - thus the lack of a GPU in the specs).

Now, I'm turning my attention to setting up SMB... I am now researching a way for my work laptop running Vista which is part of my office domain (which I can't change since I don't have enough privileges) to connect to my Ubuntu server which is a part of a different workgroup since it is in my home network. I can easily change the workgroup/domain of my Ubuntu server to match that of my work laptop but I will encounter the same problem with my wife's laptop (which is also part of a different domain). So what I am looking for is how to make my PC server/SMB be 'domain/workgroup-neutral. Is this even possible? LOL

Anyway, I am looking forward to complete my SMB configs so I can finally move on to installing MediaTomb. ^^

---

### Post by jerenept on 2011-04-22
> **Don0918 said:**
> Finally decided to plunge in and assemble myself a PC server that runs Ubuntu 10.10.

After numerous weeks of reviewing hardware specs, I managed to buy the following:

Intel i3 2120 processor 3.30GHz
ASUS P8H67-M Motherboard
4Gig RAM
1 TB Western Digital Caviar Blue HDD 6Gb/s
Coolermaster casing


Not much, but I believe it's enough for my purposes - a PC server that will primarily serve mp3 files to my Squeezeboxes all over our house, video to my A/V receiver for my home theater, media files and documents to our iPads and iPhones not to mention typical file server for our laptops.

With the amount of load that this server will be doing - especially during peak hours - do you think the specs are enough?

I've never used Ubuntu before - or any Unix-like OS for that matter - and I must admit that I am pretty much excited to try my hand on this.

I've finally set-up and run x11vnc via SSH (this is what I use primarily to manage my system since I am running it headless - thus the lack of a GPU in the specs).

Now, I'm turning my attention to setting up SMB... I am now researching a way for my work laptop running Vista which is part of my office domain (which I can't change since I don't have enough privileges) to connect to my Ubuntu server which is a part of a different workgroup since it is in my home network. I can easily change the workgroup/domain of my Ubuntu server to match that of my work laptop but I will encounter the same problem with my wife's laptop (which is also part of a different domain). So what I am looking for is how to make my PC server/SMB be 'domain/workgroup-neutral. Is this even possible? LOL

Anyway, I am looking forward to complete my SMB configs so I can finally move on to installing MediaTomb. ^^

Try [FreeNAS]("http://freenas.org/"). A lot simpler than messing around with x11vnc and such. 100% recommended by me, jerenept.
It has a web interface, you can manage everything from the convenience of your web browser!

P.S. those specs are more than enough. You could run XBMC on that machine, and make it into a complete home theatre system ;)

---

### Post by ugm6hr on 2011-04-22
> **jerenept said:**
> Try [FreeNAS]("http://freenas.org/"). A lot simpler than messing around with x11vnc and such. 100% recommended by me, jerenept.
It has a web interface, you can manage everything from the convenience of your web browser!

I was going to suggest the same. I haven't used FreeNAS v0.80 - but it was very simple to use as a SMB server at v0.69. It has fuppes upnp built-in, although I never found it very good (and fuppes hasn't had any updates in a long time).

I believe MediaTomb can be readily added to OpenFiler (which has similar features to FreeNAS (but uses Linux rather than BSD) - although I have never used it.

As for having a share visible to 2 different workgroups... I'm afraid I don't know. Maybe just try accessing the share by IP address?

Good luck with this project.

---

### Post by SteveHillier on 2011-06-14
> **ugm6hr said:**
> I believe MediaTomb can be readily added to OpenFiler (which has similar features to FreeNAS (but uses Linux rather than BSD) - although I have never used it.

You might like to see my comments on this thread (or you may not!).
[http://ubuntuforums.org/showthread.php?t=1749787]("http://ubuntuforums.org/showthread.php?t=1749787")

---

