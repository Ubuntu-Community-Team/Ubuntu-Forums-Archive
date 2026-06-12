---
title: "Transmission Bittorent Client - always lower than 100 KB/s"
date: 2010-01-29
forum: General Help
---

### Post by altjx on 2010-01-29
I'm not sure what's going on. I'm not sure if it's a setting or what but this bittorrent client always downloading stuff slow. on windows, most of my torrents would download at no less than 200 kb/s and no more than 3 MB/s. I've never experienced downloading this slow. IDK if it's the torrents or what, I've tried 3 diff torrents and they all downloaded at like 8 kb/s and some at 20 kb/s... It downloads from like 9 of about 90 peers it says

What the hell am I doing wrong? Only thing I've changed was add the privacy and enabled the block list. Changed the "Max peers per torrent" from like 10, which it was by default i think, to 240... still no difference >_<

---

### Post by altjx on 2010-01-29
Wow, now all this time it's been going slow, I finally decided to try it again. And now it's going at 600 kb/s average -.- I don't understand why it was so damn low earlier

---

### Post by warfacegod on 2010-01-29
This will help allot, I believe:

[http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by altjx on 2010-01-29
Sigh, now it's slow again. Thanks for the link, going check it out now..

I still don't see what the problem is. Link doesn't help much.

---

### Post by warfacegod on 2010-01-29
I had similar issues with Transmission. I switched to ktorrent. It's got allot more things to tweak to get better speeds.

```
sudo apt-get install ktorrent
```

---

### Post by altjx on 2010-01-29
> **warfacegod said:**
> I had similar issues with Transmission. I switched to ktorrent. It's got allot more things to tweak to get better speeds.

```
sudo apt-get install ktorrent
```

Thanks, comes with the privacy features also?

---

### Post by warfacegod on 2010-01-29
> **altjx said:**
> Thanks, comes with the privacy features also?

I assume so but I can't say for sure. I have it on my laptop and that's been down for the last week so I can't look.

---

### Post by Vegan on 2010-01-29
It could also be your ISP throttling P2P traffic.

---

### Post by altjx on 2010-01-29
Ah, just checked it out. Didn't see any for that. I'm mainly trying to find more privacy features cause I got an email from my ISP about torrenting about 2 years ago. Just trying to avoid it again but this transmission **** is ridiculous

---

### Post by altjx on 2010-01-29
> **Vegan said:**
> It could also be your ISP throttling P2P traffic.

Why would this happen so randomly though? I've never had any problems in years on Windows when torrenting. I'm pretty new to linux and now I can't even download torrents without a 3 day download estimate on 3 gigs

---

### Post by warfacegod on 2010-01-29
It could be as Vegan says. It could be that Transmission sucks. It could be any of dozens of combining factors. I suggest reading, in depth, the link I posted and switching to ktorrent or at least something that isn't Transmission. I never got truly decent speeds with it.

---

### Post by altjx on 2010-01-29
mmkay, thanks. im surprised this crap exists in ubuntu if u only get 0.7 KB/s and stuff. doesnt even make sense

[[IMG]http://www.speedtest.net/result/699418962.png[/IMG]](http://www.speedtest.net)

---

### Post by warfacegod on 2010-01-29
> **altjx said:**
> mmkay, thanks. im surprised this crap exists in ubuntu if u only get 0.7 KB/s and stuff. doesnt even make sense

I average somewhere around 400 K/b down speed in ktorrent.

---

### Post by lovinglinux on 2010-01-29
> **altjx said:**
> I still don't see what the problem is. Link doesn't help much.

Seriously? Have you followed the troubleshooting questions?

> **altjx said:**
> Ah, just checked it out. Didn't see any for that. I'm mainly trying to find more privacy features cause I got an email from my ISP about torrenting about 2 years ago. Just trying to avoid it again but this transmission **** is ridiculous

I don't like Transmission, but it has the same "privacy" features of any other client like Ktorrent or Deluge, which are those that I recommend. 

Keep in mind that there is no such thing as "privacy" in the torrent world. Someone will always know what you download. The feature that all torrent clients have that a lot people think is for privacy enhancement, is just a list of IPs that are blocked from connecting to your client. So, everyone in the swarm is still able to see your your IP, even if they can't connect to you. So if you live in a country where downloading copyrighted files for personal use is illegal, then stay away from any p2p network.

BTW, you didn't read my tutorial, because it explains all of this and also recommends that you install a blocklist program like moblock or iplist, instead of relying on the torrent client blocklist functionality.

Keep in mind that those programs are used as security tools, not for hiding illegal activities. Besides, discussing such matters is not allowed in these forums.

---

### Post by altjx on 2010-01-29
> **lovinglinux said:**
> Seriously? Have you followed the troubleshooting questions?

Yeah, I did. According to the places I'm downloading though, there's a great amount of seeders, peers, and leachers.. Hm

---

### Post by altjx on 2010-01-29
Okay, now it's back at 1.2MB/s. I have no idea why it's jumping. I give up. I'll just leave it sitting here for a day, hopefully it'll be finished tomorrow :\

Thanks for all the help

---

### Post by lovinglinux on 2010-01-30
> **altjx said:**
> Yeah, I did. According to the places I'm downloading though, there's a great amount of seeders, peers, and leachers.. Hm

I just edited my previous post, so please read it again.

---

### Post by altjx on 2010-01-30
Thanks, I understand where you're coming from. The minute I posted about Cox sending an email, everyone recommendeded PeerBlock back then to hide such traffic from ISP. Not sure if this works the same way, I'm hoping so though. XD

---

### Post by NightwishFan on 2010-01-30
I seem to have no problem using Transmission. (I use it for Linux DVD ISOs)

In the article it suggests to disable the firewall. I was wondering if my firewall could be interfering with it. I use ufw and enabled it to deny, with no extra rules. There are no errors in the Transmission log.

---

### Post by altjx on 2010-01-30
Yeah, it's ok. I'm guessing it may just be the torrent. Download speed was at 1.2 MB/s for about 5 minutes and dropped down to about 39 kb/s lol, now it's back at 500 kb/s. too much for me. i'm satisfied now lol thanks

---

### Post by lovinglinux on 2010-01-30
> **altjx said:**
> Thanks, I understand where you're coming from. The minute I posted about Cox sending an email, everyone recommendeded PeerBlock back then to hide such traffic from ISP. Not sure if this works the same way, I'm hoping so though. XD

It works the same way (they all do). But as I said, it doesn't provide any privacy enhancement. Lot's of people think these programs hide p2p traffic from the ISP or anti-p2p outfits. They don't do that. They are basically firewalls that block specific IP numbers. These IP numbers are collected from PUBLIC blocklists and loaded into the program. So, any IP address contained on those lists will be prevented from connecting to you, but they can still see your IP on the swarm. 

Besides, is not your ISP that is monitoring your traffic. They just forward a letter from the copyright holder, which doesn't know your identity but pays lots of money to companies specialized on tracking the IP of users I like you, when they are downloading stuff they shouldn't be. The premise behind the arguments of those recommending such IP blockers to prevent receiving letters of cease and desist, is that if they can't connect to you, then they can't prove you are actually downloading, which is pretty silly, if you think about it. I don't know if it actually works, but that is what people think.

The most famous blocklist program is PeerGuardian. Like PeerBlock, it is for  Windows only. Nevertheless, moblock is better than PeerGuardian IMO. IPlist looks like PeerGuardian, but it uses java. I try to stay away from anything that uses java. Moblock is perfect for me, because I use it as firewall manager. It runs a custom script when starting and another when stopping, so I put all my iptables rules there.

Anyway, I will refrain myself from discussing this subject any further, since you are clearly trying to hide your identity for illegal reasons.  Good luck.

---

### Post by altjx on 2010-01-31
Actually it's not illegal. Torrenting isn't illegal, I'd just rather not take the chance and find out.

---

### Post by mkvnmtr on 2010-01-31
I find that the max speed that my provider can change from day to day much more than any torrent program can affect my speeds. I have used several torrent programs, download from many repositories and sometimes download from a browser. Some times my speed is just slow across all platforms. For example when a new Ubuntu distro has come out my torrrent downloads for other things seem to be affected. I think how much bandwidth your nieghbors on the same line are using has an affect also.

---

### Post by lovinglinux on 2010-01-31
> **altjx said:**
> Actually it's not illegal. Torrenting isn't illegal, I'd just rather not take the chance and find out.

I never said that. Everybody uses torrent for open source application distribution and that's perfectly legal. You will never receive a letter of cease and desist for downloading Ubuntu. That's for sure. Nevertheless, your ISP will forward you a letter if you are caught downloading unlicensed copyrighted material like Hollywood movies, music and cracked software or if you are wrongfully accused of doing so. You received a letter because you were allegedly doing exactly that. If you didn't do it, then there is nothing to worry about.

---

