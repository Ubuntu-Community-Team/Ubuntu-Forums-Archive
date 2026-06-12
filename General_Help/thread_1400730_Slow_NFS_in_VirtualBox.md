---
title: "Slow NFS in VirtualBox"
date: 2010-02-07
forum: General Help
---

### Post by Lutefisk on 2010-02-07
Am having problems with getting acceptable NFS performance between Ubuntu host and guest system on the same physical server, and wondering if anyone knows what might be the issue?

Host is Ubuntu 8.04 running VirtualBox 3.1.2. Guest is Ubunu 9.10 running on one core with ~350MB RAM and set up with bridged networking on eth0. The network between host and guest is secured with IPSec set up in /etc/ipsec-tools.conf (partly general paranoia and partly in case I ever want to move the guest to a separate physical machine). Server- and client-side NFS was set up according to the Ubuntu SettingUpNFSHowTo.

Total NFS read/write speed is around 3 MB/s. HW disk performance on the host should not be an issue; it is still order-of-magnitude higher than NFS read/write speeds.

I have browsed various web sites for optimizing NFS performance and tried various /etc/exports and mount options, including e.g. experimenting with rsize/wsize, async, UDP vs. TCP, hard, intr, and so on, and the best I could get (which it seems going to UDP was the main differentiator) was around 4 MB/s which is still way slower than the performance I would expect.

The strange thing is the bandwidth seems to be CPU-constrained; I always see very high CPU% on either rpciod/0, pdflush, or nfsiod (depending on which of the various setups I have tried). In the typical setup when mounting without any particular mount options it is rpciod/0 which seems to be the culprit.

I'm sort of stuck at the moment, any help would be greatly appreciated! :)

---

### Post by Lutefisk on 2010-02-22
For anyone coming across this issue; it seems my particular configuration with IPSec is the main problem. I tried the same setup with KVM and got similar results with ~1.5 Mbps between the guest and host and close to 100% CPU consumed by rpciod/0 on the guest. After disabling IPSec on the KVM guest and host the speed increased to ~9.5 Mbps and rpciod/0 CPU usage dropped to ~10%.

I was a bit surprised to see IPSec becoming a bottleneck at these speeds based on experience with SSL download/upload speeds at comparable ~10 Mbps transfer rate with no noticable CPU usage for the transfer. Also I found it a bit surprising that the high IPSec related CPU usage would show up in the rpciod/0 process.

---

