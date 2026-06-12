---
title: "Lucid doesn't like wireless."
date: 2010-09-24
forum: General Help
---

### Post by CuddlyCombine on 2010-09-24
Lucid started misbehaving recently. I can see wireless networks but I can't connect. The connection just hangs and drops. wpa_supplicant does nothing, I've tried iwconfig and iwlist and dmesg to find the problem; I can't find anything. It'll work sometimes, but for no apparent reason. It's not the router. My drivers are updated.

Help?

P.S. I should also note that I dual-boot with Windows 7, and Windows wireless works just fine.

---

### Post by CuddlyCombine on 2010-09-24
Bump because nobody has any idea what to do and I'm getting kinda puzzled.

Also, the wireless decided to start working for no reason (and is still giving the same readouts as before). Need a guru or something here. And yes, I've Googled my heart away; no fixes apply.

---

### Post by wombil on 2010-09-24
Hey Cuddly,
I had a similar problem lately.I set the security to wep and tried all things to make it work.Changed to WPA and connected straight away.
One clue I got,dont remember who sent it, was to make sure you have either WPA or WPA2 selected and not WPA-WPA2 alternative.
 Hope it goes for you.

---

### Post by CuddlyCombine on 2010-09-24
> **wombil said:**
> Hey Cuddly,
I had a similar problem lately.I set the security to wep and tried all things to make it work.Changed to WPA and connected straight away.
One clue I got,dont remember who sent it, was to make sure you have either WPA or WPA2 selected and not WPA-WPA2 alternative.
 Hope it goes for you.

I'm on WPA2. Nothing. :( Thanks though.

---

### Post by Nickster74 on 2010-09-24
Hey cuddly,

I'm new to this as well, i was using a dlink dwa140 dongle which to this day i cannot get to work but now i have downgraded to a belkin n1 express 34 card on my laptop in conjunction with a homehub. put the .inf file in ndiswrapper and worked instantly, never loses signal or disconnects and is rocket fast! could it be your wireless device from the comp?, however i struggle to connect to public networks.

---

### Post by bazzal1941 on 2010-09-24
I'm sure you've seen this but if not it might help.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by CuddlyCombine on 2010-09-24
> **bazzal1941 said:**
> I'm sure you've seen this but if not it might help.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

The problem isn't my driver. It was working perfectly fine until about a week ago; it's not only on this network, but it still has flawless connectivity whenever it chooses to connect. I'm just stuck on what's making it throw a tantrum every now and then. 

Thanks though.

---

### Post by coffeecat on 2010-09-24
> **CuddlyCombine said:**
> The problem isn't my driver. It was working perfectly fine until about a week ago; it's not only on this network, but it still has flawless connectivity whenever it chooses to connect. I'm just stuck on what's making it throw a tantrum every now and then. 

When you say 'not only this network' do you mean you have the same problem in different locations with different networks? But if this is just one location - your home - and it works fine at times but not others, consider outside problems such as interference. The commonest problem is too many people trying to use the same wavelength. If you can see your network in network manager, can you see many neighbours' as well? Chances are that one or more are using the same channel as you and the networks are interfering. If this might be the case, go into your router configuration and change the channel from 1 to 11, or vice versa, or 6 to 1 or 6 to 11. Whatever channel you are on now.

Or it could be interference from a neighbour's baby alarm, or your microwave or a dozen other appliances.

---

