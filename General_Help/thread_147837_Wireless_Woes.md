---
title: "Wireless Woes"
date: 2006-03-20
forum: General Help
---

### Post by TheMono on 2006-03-20
Total experience with Linux - 4 days... So please keep any help very, very simplified!

I'm currently writing this in Windows. Because, while Ubuntu (5.1) detects and activates my wireless card (a Planet WL-3560) easily enough, it gets no signal strength. Anywhere. Period. In my room, I get average to low signal under Windows, and 0% under Ubuntu... But right next to the router, I get perfect signal for windows, and still 0% under ubuntu.

I know how to install a manually downloaded .deb package, but that is about it, so I do have a very, very rough idea of the terminal. This is the only thing holding me up on making a proper effort to switch to Ubuntu, so any help would be appreciated.

I've tried looking through the forums for an answer, but it always seems to involve Ubuntu just not detecting the card at all....

(actually, there is one other thing, and that is making my second monitor work, but that is secondary at the moment...)

Thanks in advance for your help.

---

### Post by Zelut on 2006-03-20
... welcome to one of the busiest topics on the forums.  Everyone wants wireless & somehow I end up teachin' 'em how (or trying).

I'm a little tired now but if you could take a look at my wireless steps (in my signature) see what you can make sense of.  See what you can find out & let me know where you might have trouble.  (you will need some internet access to get it installed; ie wired connection).

---

### Post by TheMono on 2006-03-20
In the time it took me to move my laptop to the other room and boot up Ubuntu wired into the router, I got a reply. You guys are awesome!

I'll go through your sig links now. Thanks.

---

### Post by TheMono on 2006-03-20
Quick Question:  step one is done, step two gives me 

0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

So step three should be...?

lspci -n | grep 0000:30:00.0 gives me nothing...
lspci -n | grep0000:30:00.0 also does... 

What should I be using?

---

### Post by Zelut on 2006-03-20
how about just **lspci -n**

---

### Post by TheMono on 2006-03-20
Never mind... It works now...

---

### Post by TheMono on 2006-03-21
Alright... Next question \\:D/ 

It seems to be working ok now - except for another minor issue. It looks like Ubuntu only supports WEP encryption, and at the moment we are using WPA.... 

Is there a way to make Ubuntu play nice with WPA? 

Or am I completely misinterpreting things, and it works with WPA already and the problem is elsewhere...

---

### Post by Zelut on 2006-03-21
I believe that some people have managed to get WPA to work.  I have never tried personally so I can't help you there.  I'm sure if you do a forum search you can find some good tips.  I only use wireless on one machine & its mainly for testing so I don't bother with encryption..

---

