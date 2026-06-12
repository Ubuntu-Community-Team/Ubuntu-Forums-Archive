---
title: "Transfer files: Desktop -&gt; Laptop"
date: 2010-10-17
forum: General Help
---

### Post by 1Michael1 on 2010-10-17
Hello fellow Ubunters,

So the deal is, I've a desktop where I got all of my movies, music etc stored and a laptop which is clean.
And I want to get a tip on some software or ways of moving my movies through my local network.

The reason why I want to do it is because my laptop has an HDMI port that I can hook up to my tv and my desktop doesn't.

I know of SSH and so on, but just wondering if there's an easier/better way, maybe a way to stream the movies from my desktop without any quality loss onto the laptop?
I don't prefer SSH due to having to open my ports, I'm quite paranoid about that, want to keep my things impact and secure.

(Both of the computers run Ubuntu)

Thanks a lot in advance,
Michael.

---

### Post by efflandt on 2010-10-17
Of course the most secure way to transfer files is to copy them to external (USB, etc.) flash or hard drive, then copy them to the destination.  Of course if the temporary drive has a different file system, you may want to use tar with compression so they maintain their ownership and permissions.

Otherwise I typically use scp related to ssh (have not tried sftp).  If you enable compression for ssh, despite encryption, files that are not already compressed can transfer faster than your network connection (assuming hard drives are fast enough).  ssh can be as secure as you want to make it, I always disable ssh root login and require keys only (so password cracking is futile).  As long as you do that, it should be as secure as any VPN, even if you open up ssh to the internet.  But I use it even on my home LAN because my DSL wireless/modem/router only uses 64(40) bit WEP.  Although, it is in the basement so someone would have to be in my driveway to try to crack that (I get a signal on 2nd floor, but not much past my front porch).

There are ways to stream video over a LAN, but I have not downloaded videos, so I have not tried that.  But Netflix on my standalone BluRay player can stream 720p video with a 3.5 Mbps internet connection (mine is 5+ Mbps), so it is definitely a possibility on a faster local network.

---

