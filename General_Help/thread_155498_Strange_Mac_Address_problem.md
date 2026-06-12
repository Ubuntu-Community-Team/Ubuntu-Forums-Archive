---
title: "Strange Mac Address problem"
date: 2006-04-05
forum: General Help
---

### Post by PowerLlama on 2006-04-05
It seems every time I restart my computer, my Mac Address for my computer changes. This is incredibly irritating as I have to use my mac address for a key. Only the last 6 entries change, while the rest stays the same.

Any help?

---

### Post by shof2k on 2006-04-05
Open a terminal and type "ifconfig".  If you could paste the output here for 3 changes of mac-address then perhaps someone can help you.

I always thought mac's were burnt onto the nic being used.  What network card are you using. Is this changing at all?

---

### Post by PowerLlama on 2006-04-05
Here's for two reboots

```
eth0      Link encap:Ethernet  HWaddr 00:00:6C:D3:AB:11
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000


eth0      Link encap:Ethernet  HWaddr 00:00:6C:81:BF:C0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000
```

I thought mac addresses were on the card itself as well. It's the built-in ethernet on my mobo.

---

### Post by Jason_25 on 2006-04-05
Some motherboards with built-in ethernet have an option to enter the mac address in the bios.  The mac should be on a sticker on top of the lan connector.  You'll probably need to open your case to see it.  Maybe that will help.

---

