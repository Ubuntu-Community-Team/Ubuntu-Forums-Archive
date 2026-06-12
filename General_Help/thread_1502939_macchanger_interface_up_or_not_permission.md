---
title: "macchanger: interface up or not permission"
date: 2010-06-06
forum: General Help
---

### Post by Telhma on 2010-06-06
hej hej, i was tying to change the mac adress of my internet device, but, mmm, it is not working. i always get a error:

```

tella@telhma-laptop:~$ sudo ifconfig eth0 down
tella@telhma-laptop:~$ sudo macchanger --mac 11:22:33:44:55:66 eth0
Current MAC: 00:17:a5:e5:5b:75 (unknown)
ERROR: Can't change MAC: interface up or not permission: Invalid argument

```

with my wireless card it is all working perfect.

but how can i do it make the mac of the wired connection change?

thanks a lot

greetings

---

### Post by wooblah on 2010-06-06
post some debug info.

dmesg ?

that seems like the right way to do it normally.

---

### Post by Telhma on 2010-06-06
you know that write a hell of a file?

Is there something i need to look for, i post here every line with eth0 in ;)

```

[    1.805462] eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:17:a5:e5:5b:75
[    1.805467] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.805470] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.805473] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
...
[   15.737195] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by dino99 on 2010-06-07
is wifi-radar installed ?

---

