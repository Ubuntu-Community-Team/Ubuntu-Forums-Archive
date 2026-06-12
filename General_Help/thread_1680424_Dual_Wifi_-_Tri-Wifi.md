---
title: "Dual Wifi - Tri-Wifi?"
date: 2011-02-02
forum: General Help
---

### Post by Zerocool Djx on 2011-02-02
I heard that linux might be able to connect to several different  networks at once if you have a few wifi cards laying around. Is this  true? if so,.. how is it done?

---

### Post by uRock on 2011-02-02
Very possible.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Kirboosy on 2011-02-02
uRock--wow I'm so sorry. I feel like I double posted even though you posted originally. We must of posted at the same exact time...

---

### Post by Zerocool Djx on 2011-02-02
> **uRock said:**
> Very possible.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Negative on that,.. Those are all just internet sharing with wired connections..

Anyone else?

---

### Post by Kirboosy on 2011-02-02
You should be able to just have multiple connections available in the Gnome Network manager if all the wifi cards work properly. I've never tried but it doesn't seem like it should be that complicated.

---

### Post by Zerocool Djx on 2011-02-02
Tho,. I should mention that I have a Fon router laying around,.. Something tells me Imight be able to program the Fon to connect to another router and relay that through a cat5 connection into a etho connection.. hmmm,.. I wonder? 

any thoughts on that?..

---

### Post by uRock on 2011-02-02
> **Zerocool Djx said:**
> Negative on that,.. Those are all just internet sharing with wired connections..
You are wanting to use multiple NICs to connect to other networks? If yes, then plug them in and configure them through Network Manager.
> **Zerocool Djx said:**
> Anyone else?No need to be rude.

---

### Post by Kirboosy on 2011-02-02
> **Zerocool Djx said:**
> Tho,. I should mention that I have a Fon router laying around,.. Something tells me Imight be able to program the Fon to connect to another router and relay that through a cat5 connection into a etho connection.. hmmm,.. I wonder? 

any thoughts on that?..

If you have a bridge compatible router you should be able to do that no problem.

What exactly is the point of connecting multiple cards to different APs at once? You won't really get better speeds unless you have some script to designate how the cards are used...

---

### Post by sdennie on 2011-02-02
I think you are trying to achieve something called bonding.  I've never hear of anyone doing it with wifi cards and I don't know if it's useful to do in a home setting but, here is the wikipedia page about it: [http://en.wikipedia.org/wiki/Link_aggregation](http://en.wikipedia.org/wiki/Link_aggregation)

---

### Post by Kirboosy on 2011-02-03
Have you even attempted to hook up the multiple NIC/wireless cards?

---

### Post by Zerocool Djx on 2011-02-03
While the "master" of Ubuntu was confused wither "network sharing" with Eth0 was relevant to  my dual wifi topic (Wlan0) and pointing out "rude behavior", I made a few calls and found that there really is no real way to do this.. Essentially it is a data flow issue, 1 IP connection per card. It's just the way networking is set up. There maybe a work around to have the cards alternated IP's to each website or connection Port and/or map an individual program to a specific wifi card not to clog the bandwidth down. If the two cards even connect at the same time, this is prolly what the case would be anyway and not so much a benefit, unless using torrents is something you use alot. Then this would be interesting. Like moving all nonessential data activity to a secondary connection instead of a dual one.

Anyway,.. Just a thought.. thanks for the help...

---

### Post by sdennie on 2011-02-04
> **Zerocool Djx said:**
> While the "master" of Ubuntu was confused wither "network sharing" with Eth0 was relevant to  my dual wifi topic (Wlan0) and pointing out "rude behavior", I made a few calls and found that there really is no real way to do this.. Essentially it is a data flow issue, 1 IP connection per card. It's just the way networking is set up. There maybe a work around to have the cards alternated IP's to each website or connection Port and/or map an individual program to a specific wifi card not to clog the bandwidth down. If the two cards even connect at the same time, this is prolly what the case would be anyway and not so much a benefit, unless using torrents is something you use alot. Then this would be interesting. Like moving all nonessential data activity to a secondary connection instead of a dual one.

Anyway,.. Just a thought.. thanks for the help...

Like I said, it's called bonding or sometimes multiplexing.  It's possible to do with wired network cards and I don't see why it wouldn't be possible with wireless cards.  It's non-trivial to setup and is unlikely to benefit a home user.

I'm closing this thread because I think the technical details have been pointed out and it has become unnecessarily personal.

---

