---
title: "Dlink DWL-G510 Ubuntu 9.04"
date: 2009-10-08
forum: General Help
---

### Post by slinkeey on 2009-10-08
Hello,

I am having some trouble getting my Wireless Card to work in my PC.  
It is an older card, but if I can get it to work, I will still be happy.  It has served me well in the past.

Anyways,  It does not show up under network connections.

lshw -C network
yields

```

*-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=29 mingnt=10

```
Actually it yieds a few more entries, but this appears to be the culprit.

Could anyone help or point me in the right direction.  I have googled and tried stuff others posted.. Mostly stuff from 2006 though.

I also tried activating the madfi driver..

Thank You,
Jeff

*01 Sorry, I forgot to put this in the Netowrking and Wireless Forums....

---

### Post by PrePenguin on 2009-10-08
I am assuming the "unclaimed" part is the issue which I would assume would have to be assigned to a network.

---

### Post by slinkeey on 2009-10-08
I tried assigning it to a network just like this notebook that i am using to type.

I set up the wireless connection info exactly the same.

Thanks,
Jeff

---

### Post by PrePenguin on 2009-10-08
is it wep keyed to a router? And is that router showing up in your wireless connections?

---

### Post by slinkeey on 2009-10-08
Yes it is wep keyed.

On this machine my router shows up and so do other routers around me under Wireless Network.

The non working machine is a different story..  No wireless networks show up.

---

### Post by PrePenguin on 2009-10-08
Atheros Communications Inc. I am running the same wireless with absolutely no problems except its not named Dlink under my network connections it is labeled Auto eth0 and set to connect automatically.. I am thinking theres a possibly a driver issue here or a setting in the panel is wrong or mis-configured.

---

### Post by slinkeey on 2009-10-08
Mine is not named Dlink..

I did a fresh 9.04 install and no networks showed up unlike my other machines.

eth0 is my wired on that machine.

---

### Post by PrePenguin on 2009-10-08
> **slinkeey said:**
> Mine is not named Dlink..

I did a fresh 9.04 install and no networks showed up unlike my other machines.

eth0 is my wired on that machine.

On the fresh install did you do a full kernel install or the minimal? Maybe try the driver update CD and see if it then detects a proper driver? Just a few idea's to try before digging to deep. Also when i use my lan connection along with my wireless enabled at the same time on 1 machine they seem to conflict maybe try disabling the lan connection.

---

### Post by slinkeey on 2009-10-08
> **PrePenguin said:**
> maybe try disabling the lan connection.

Disabling in linux did not do the trick but......
Disabling the on board lan in the bios did the trick..

Thank You

Why didn't I think of that..I usually start disabling and running minimal to trouble shoot but sometimes i am stubborn.

Jeff

---

### Post by PrePenguin on 2009-10-08
Hey we all been there and done it at some point.. Glad your issue is resolved and enjoy ubuntu..Sincerely,Tre

---

### Post by slinkeey on 2009-10-08
I have been enjoying it for years..
I am setting up an old machine of mine for my brother.

He liked using my machine because it doesn't get slower by the day like his windows machine.  He manages to pick up garbage from the net..

---

