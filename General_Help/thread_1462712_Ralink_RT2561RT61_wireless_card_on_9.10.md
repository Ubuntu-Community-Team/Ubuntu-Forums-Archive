---
title: "Ralink RT2561/RT61 wireless card on 9.10"
date: 2010-04-26
forum: General Help
---

### Post by Space Cowboy on 2010-04-26
About a year ago I had a different computer with this same wireless card (edimax EW-7128g) and it was recognized immediately after I installed ubuntu 8.10. I found this [COLOR="Blue"]_**[hardware compatibility page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax")**_[/COLOR], and it says it is compatible, at least on 9.04.

After reading this old guide I found:
[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

I downloaded the latest driver, and followed the instructions (i had to refer to the readme too, some things were slightly different which I'm assuming is because it's the 2010 driver not the version referred to in that tutorial) up until:

> (e) copy the rt61.ko driver file to the modules directory then load it

```
$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
$ sudo depmod
$ sudo modprobe rt61
```
I don't see where rt61.ko is... I've got the information for my wireless connection edited into /etc/Wireless/RT61STA/
rt61sta.dat

iwconfig shows pretty much default stuff, no mention of my wireless card or any type of connection, though the card does show up at the bottom of the lspci query. I added the wireless connection information into the "Network Connections" prompt in the preferences, but obviously that's not accomplished much of anything for obvious reasons.

Should I just install 9.04? Judging from _**[COLOR="Blue"][this account]("http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/")[/COLOR]**_, getting this wireless card to work would be a hell of a lot easier.

Thanks guys, I'm still pretty unfamiliar with a lot, but it's a learning experience.

---

### Post by clhsharky on 2010-04-26
HI Space Cowboy

I have that card " edimax EW-7128g "and works well. I did have trouble with early Ubuntu .32 kernels and early  generic .32 but thats Lucid. I don't remember the .31 kernel in Karmic giving me any problems but others did.
That said I would plug in to Ethernet then update, unplug Ethernet, restart, that should solve your wifi problem.

Sharky

You don't need to install drivers there in the kernel.

---

### Post by Space Cowboy on 2010-04-27
> **clhsharky said:**
> HI Space Cowboy

I have that card " edimax EW-7128g "and works well. I did have trouble with early Ubuntu .32 kernels and early  generic .32 but thats Lucid. I don't remember the .31 kernel in Karmic giving me any problems but others did.
That said I would plug in to Ethernet then update, unplug Ethernet, restart, that should solve your wifi problem.

Sharky

You don't need to install drivers there in the kernel.

Well I had to dig up a 25ft ethernet cable to reach the other room, but it worked perfectly (eventually) after an update and several restarts (the graphics were screwed up after the update)

Thanks a ton! Glad it was so simple.

---

### Post by clhsharky on 2010-04-27
HI 

What chip and driver do you have?

Sharky

---

