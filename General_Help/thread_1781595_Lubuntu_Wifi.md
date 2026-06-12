---
title: "Lubuntu Wifi"
date: 2011-06-13
forum: General Help
---

### Post by Nevakonaza on 2011-06-13
Hey guys,

I just installed Lubuntu on my Asus X58L Series laptop,It runs very nice...everything workes out the box exept the Wifi is a bit dodgy.

It works but its super slow and im not sure why,When i look at the signal bar its showing 3 out of 4 bars so its not a signal problem as the laptops downstairs...router is upstars.

The wifi worked great under Windows Vista so im notsure why its soo slow under lubuntu...i have installed all the latest updates for Lubuntu.

Any help appreciated. :D

---

### Post by SteveDee on 2011-06-14
> **Nevakonaza said:**
> ...It works but its super slow...

Click on the network icon. This should show you the Network connection name (e.g. wlan1, eth2 or whatever)

Now open a terminal (select LXTerminal from Accessories menu).

So if your connection name is eth2, at the prompt type:-
```

iwlist eth2 bitrate

```

This should give you an output like this:-
```

eth2      4 available bit-rates :
	  1 Mb/s
	  2 Mb/s
	  5.5 Mb/s
	  11 Mb/s
          Current Bit Rate=11 Mb/s

```
...and should show whether your current rate is low or not. If it is, you might like to try a different channel: [http://ubuntuforums.org/showthread.php?t=1768125](http://ubuntuforums.org/showthread.php?t=1768125)

---

