---
title: "Hard disk access causing high CPU usage"
date: 2010-07-07
forum: General Help
---

### Post by noshade on 2010-07-07
Every time I access my hd, the system becomes unresponsive with the cpu usage reaching 100%.

Example:
I use the disk utility for a read benchmark and I have to wait for it to end to be able to do anything else. It seems that the cpu is completely dedicated to reading the hd.


DMA is enabled:
[    1.464552] ata1.00: ATA-7: Hitachi HDS721616PLAT80, P22OA8BA, max UDMA/133
[    1.480461] ata1.00: configured for UDMA/133

I have disabled swap temporarily (swapoff -a) to make sure that it isn't concurrent hd access that is draining the resources.

Any idea where the problem might be? Thanks.

---

