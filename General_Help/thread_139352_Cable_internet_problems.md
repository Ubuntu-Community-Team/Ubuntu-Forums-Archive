---
title: "Cable internet problems"
date: 2006-03-03
forum: General Help
---

### Post by kate on 2006-03-03
A couple of months ago, we moved house and got cable internet. I'm trying to connect via an Ethernet cable and it works (after a lot of trying and failing) with my laptop which is running Fedora Core 3, but I can't get it to work on my desktop which is running Ubuntu 5.10 (I couldn't get it working with 5.04, or anything else, either). Can someone please help me? I'm kinda a Linux newbie, also.

Thanks, 
Kate

---

### Post by Ramses de Norre on 2006-03-03
Does your ethernet card show up in system > administration > networking?
If so, did you configure everything correctly?
What error messages do you get when trying to connect to the internet?

---

### Post by kate on 2006-03-03
At boot, it gets stuck on 'starting network interfaces' or the like, then after a while it says 'failed'. Then when I log in, it says it's active and it seems to be recieving a little bit of something from the modem, but I can't access the internet. There aren't any error messages, as such.

---

### Post by kate on 2006-03-04
:confused:  I'm still kinda lost...

---

### Post by Stormbringer on 2006-03-04
Hi kate,

Might there be the possibility that your Cable Internet is bound to a specific MAC address (=the hardware address of the ethernet card of your laptop)? If that's the case then your desktop won't get a valid dhcp-lease because its ethernet card's MAC address is different from your laptop.

Best solution in this case would be to use a router that's capable of spoofing the MAC address - this will enable internet access for both systems.

Storm.

---

