---
title: "Please advise me on buying a wifi card that would work."
date: 2006-05-29
forum: General Help
---

### Post by 1002285 on 2006-05-29
Hi,
I have been trying to get my wifi card working - it is Canyon CN-WF518 - but I just haven't found a driver (actually I did find one file, but it wasn't possible to install it).
I'm willing to buy a new card, because I think this card wasn't very good anyway - I wasn't very happy with how it worked on Windows either.
So I'm giving a short list of cards available from a local store, and if some of you can tell me that "yes, there is a driver for it and it will work", please do.
My computer is an old Dell Latitude CPi.
I have two PCMCIA slots and LAN internet connection with a PCMCIA card worked right from the installation (though it did not work any more after upgrading to Dapper - that is why I'm back to Breezy). 

- Chronos Wireless PCMCIA adapter 54M
- SMC Wireless PCMCIA CARDBUS adapter 11 Mbps 2635W
- 54Mbps Wireless PCMCIA Card Trendnet TEW-421PC (my computer doesn't really support 54 Mbps - can that be a problem? my old wifi card was 54 Mbps, too, and Windows kept saying sth about that, still, it worked with the speed 11 Mbps).
- Micronet Wireless LAN Adapters 54Mbps PCI external antenna SP906GK

The prices are all about the same, in the range of 22-25 euros.

---

### Post by Falados on 2006-05-29
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Those are the cards (Fairly old listing) that the Linux WLAN project supports.
Usually anything with a Prism Chipset is good.

---

### Post by rcarring on 2006-05-29
The PC Card support under Dapper may need attention, that's why your wifi card doesn't work under Dapper.

A wifi base station would allow you to use traditional eth0 as your network outlet and then connect to your wireless network from the station itself.

---

### Post by 1002285 on 2006-05-29
[QUOTE=rcarring]The PC Card support under Dapper may need attention, that's why your wifi card doesn't work under Dapper.

A wifi base station would allow you to use traditional eth0 as your network outlet and then connect to your wireless network from the station itself.[/QUOTE]

I'm not using Dapper. Wifi is not working under Breezy either, but I don't have driver either.
On Dapper the wired LAN, that worked well on Breezy, did not work any more.

Now I use 5.10 and I think I'll stick to it, because with Dapper this old computer got slower, too.

But I ave to admit that I don't understand the last sentence in your post - what is the wifi base station, and do you think I should keep trying with my old wifi card for which I don't have a driver file?

---

### Post by tkjacobsen on 2006-05-29
Ubuntus own list on supportet network devices:

Wireless:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Wired:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

Note: The RT2500 chipset (wireless) works very well for me under Dapper (out of the box). Also worked under breezy, I just don't remember if it was out of the box, or if I should follow the provided howto: [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500)

---

### Post by 1002285 on 2006-05-29
[QUOTE=Falados][http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Those are the cards (Fairly old listing) that the Linux WLAN project supports.
Usually anything with a Prism Chipset is good.[/QUOTE]

Thank you for directing me to that list. I need to ask a little more to be sure.
* How do I know what chipset I have and what chipset should the card have?
* For example SMC 2635W is on that list, there is "cardbus" in the "host I/F" column (what does that mean, isn't it a PCMCIA card then?), and a remark that "ADMtek offers linux driver".

How do I understand this information? There is a driver and it should work?

---

### Post by 1002285 on 2006-05-29
[QUOTE=tkjacobsen]Ubuntus own list on supportet network devices:

Wireless:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
[/QUOTE]
Thank you for the answer.
So if the cards I found in the pricelist, aren't in this list, does this mean they won't work or that hey haven't been tried?

---

### Post by FLeiXiuS on 2006-05-29
I'm a total fan of the MADWIFI team.  

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

This would be my conclusive list on which you look into.  Their drivers are probably the most compatible for linux in general.

---

### Post by tkjacobsen on 2006-05-29
This just mean that noone have documented the card yet. Byt many differend brands actually uses the same chipset..  Youl see that the rt2500 chipset along with the prism54 and orinoco_cs 
 chipsets etc. works well.. Those (as you see) are made by different manufacturors..


Ask your manufacturor which chipset is in the card

This is analouge to laptop producents: both dell and hp provides laptops with amd chips...

---

### Post by sadjack on 2006-05-29
Don't know where you are based but the below companies have provided me with good service and sell cards that work with linux

networkned.co.uk

linuxemporium.co.uk

perhaps they can help you with your choice.

---

### Post by dschaller on 2006-05-29
I've had good experiences with cards that use the RaLink RT2500 chipset. In fact, it's the only chipset I ever buy for Linux wireless. I have three different RT2500 cards, one a PCMCIA on my laptop. They all worked right out of the box on Ubuntu. Note though that the drivers for the USB versions of the RT2500 are not in the Breezy kernel (although they are in Dapper). You can get the USB ones going with Breezy, you just have to compile the driver yourself.

---

### Post by 1002285 on 2006-05-29
Chipsets is a subject i don't really understand. I can see from my device manager that my wired -LAN card uses Realtek chipset - does this mean that I need a card with Realtek chipset? Does it mean anything?
I read from one of the sources offered here that they recommend RaLink AND Realtek.
Probably Realtek will be fine for me, too, then? But I don't understand - do I need to make REALLY sure, that a Linux driver exists or will it be enough to have the "right" chipset?

---

### Post by tkjacobsen on 2006-05-29
Allmost any wireless cards can use the windows drivers via ndiswrapper. But it mignt work better if linux has native support for the card. So it would be best if you bought a card supported by the linux kernel.

The chipset is just some part of the card, many different brands uses the same chipset. But the driver needed to use the card is the driver for the chipset not the manufacturor (as of my knowledge, PLEASE CONFIRM). That is why people is talking so much about chipsets.

It doesn't matter which chipset your wired lan device uses when choosing a wireless network card.

---

### Post by 1002285 on 2006-05-30
Hmm.
I was looking for really wrong cards for a while, and already posted a question about them here.
Sorry ...

---

### Post by 1002285 on 2006-05-30
Ok
trendnet tew-441pc is available.
[http://www.trendnet.com/products/TEW-441PC.htm](http://www.trendnet.com/products/TEW-441PC.htm)
Will probably work, i guess, if madwifi says so?
421PC is also available, but it's not listed among supported cards.

So this TEW-441PC is probably a working solution? Not very cheap, though, 33 euros.

---

### Post by 1002285 on 2006-05-30
[QUOTE=FLeiXiuS]I'm a total fan of the MADWIFI team.  

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

This would be my conclusive list on which you look into.  Their drivers are probably the most compatible for linux in general.[/QUOTE]

Thanks, I looked at that list. I have found only one card that is available from a shop in my town, and that is also listed there - Trendnet TEW-441PC.
I tried to find out more about what the madwifi is, but I couldn't get everything clear. In the "requirements" section it says what kernel I should have etc, but as my computer is a rather old one, I'm still worried about the hardware requirements. Or isn't that a problem? I have 133 Mhz P II and 128 Mb memory.
About the requirements listed in the page - [http://madwifi.org/wiki/Requirements](http://madwifi.org/wiki/Requirements) - 
if I am using 5.10 and it is up-to-date, can I assume that the requirements are met?
And generally - do you think Trendnet TEW-441PC could be a good card?

---

### Post by FLeiXiuS on 2006-06-01
You should be fine with the current system specs.  Just take note of your batter if you rusing a laptop. WIFI eats battery life for breakfast!

---

### Post by 1002285 on 2006-06-19
Thanks to everybody who answered.
I finally got back to it and bought a D-Link DWL-G630. (But I also tried a lot more things with the old card and didn't get anything out of it).
DWL-630 seemed to work out of the box, though I tried ti first in the store and there it didn't work  - may-be it just needed another reboot, because the connection was named "ath0" in one place and the network that the system "tried to use" was "eth0" - like the LAN-connection that worked before. Anyway, I was courageos enough to buy the card without getting a connection in the store, and haveing booted the system at home, I was able to change "eth0" to "ath0" and it works fine.

---

