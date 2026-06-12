---
title: "Help getting Intel PRO/Wireless 3945ABG working? Compaq 610"
date: 2010-01-06
forum: General Help
---

### Post by Bucky Ball on 2010-01-06
What do you think? Wife just bought a new Compaq 610 series laptop. These are the wireless specs:

```
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
30:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4357 (rev 10)

```

Strange thing is when I ping the router, I get this, pings one time then dies:

```
anna@katie:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.104 icmp_seq=1 Destination Host Unreachable
From 192.168.0.104 icmp_seq=2 Destination Host Unreachable
From 192.168.0.104 icmp_seq=3 Destination Host Unreachable
From 192.168.0.104 icmp_seq=4 Destination Host Unreachable
```

I have static IPs and the lappy is set up accordingly. The router is not set up as a DHCP server.

I have done all updates, added ubuntu-restricted-extras, added Medibuntu repo to software sources and a sweet machine so far. Ubuntu installed without a hitch. I haven't been offered any drivers for ATI vid nor the wireless card.

I am using 8.04.3

I have tried this:

[http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/](http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/)

Nothing doing. Any help ... ?

---

### Post by Leppie on 2010-01-06
why are you using an old system on a new laptop?
try downloading jaunty (9.04) or karmic (9.10).
my intel 3945 just worked oob in karmic ;)

---

### Post by Bucky Ball on 2010-01-06
Because I only use LTS releases. What driver are you using? It does seem to be working kind of anyhow. The card is on, that is for sure. Just not connecting with my network. Ethernet cable is fine.

I need my machines to be stable.

(Release, not system. Why am I using an old release on a new system. 8.04 is the current long term support, enterprise release, not old but current, and advisable for servers and production machines.)

---

### Post by Leppie on 2010-01-06
i'm using the kernel module provided with Ubuntu.
in Debian Lenny, i always have to upgrade the module as it apparently has a bug (the card is recognized and leds light up, but won't connect).

---

### Post by Bucky Ball on 2010-01-06
> **Leppie said:**
> (the card is recognized and leds light up, but won't connect).


That is pretty much what is happening. Everything looks fine then when I ping it pings once then stops. Odd. ?

---

### Post by Leppie on 2010-01-06
as i said, i had to upgrade the drivers (kernel module), but not sure the upgrade is available in ubuntu. the debian package is iwl-firmware (it's not available in my cache)

---

### Post by darco on 2010-01-06
Works perfectly on my 3yr old Toshiba laptop using Karmic. Take the plunge Bucky and upgrade. What have you got to lose? Its a new laptop , if it doesnt work for you just go back to LTS. What app is so vital that you wont upgrade?
KK is very stable. 


darco

---

### Post by Bucky Ball on 2010-01-06
It's like this, the wireless card is actually showing me plenty of signal (75%), so it's working. Identifying my own network and the neighbour's! It appears everything is working fine but do a search for something in Mozilla and nothing. Weird. 

So I've gotten this far: Looks like the card works 'out of the box' with no drivers required but for some reason not connecting to my network (even though it happily sees, pretends to and gets great signal), regardless of the fact Ubuntu accepts WEP security etc and seems to be smiling at me.

No app that vital, but the stability is.

```
wlan0     IEEE 802.11abg  ESSID:"Slynn"  
          Mode:Managed  Frequency:5.2 GHz**  Access Point: Not-Associated   **
          Bit Rate:0 kb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=79/100  Signal level:-55 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Access point: not associated? Could have something to do with it.

---

### Post by darco on 2010-01-06
most likley a dns issue...

---

### Post by Bucky Ball on 2010-01-06
Nope. DNS fine and matches with the other three machines. That is where I got them. I'll check again though just to make sure.

---

### Post by darco on 2010-01-06
Ill fire up my lappy if theres anything you need me to check.....


darco

---

### Post by Bucky Ball on 2010-01-06
Okay, thanks for ideas people.

This card does seem to work out of the box with 8.04. I haven't loaded any drivers and am online wirelessly typing this. 

Noticed just before going to bed last night that when I issued 'iwconfig' along with 'wlan0' I was also getting 'wlan0:avahi'. I realised as I dozed the machine was trying to connect with that. It doesn't exist.

Switch on this morning and that alias has gone and connected wirelessly immediately! Hooray!

I also realised that the card had been working fine all along ('out of the box') as it was picking up wireless networks all along but just not getting online. It was the disappearring wireless alias that had been my issue.

Here's hoping it doesn't reappear at a later stage.

So 8.04.3 rocks, as usual, and problem solved itself. Thanks again for suggestions. :)

---

