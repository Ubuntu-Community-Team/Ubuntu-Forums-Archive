---
title: "locking firewire port"
date: 2006-06-27
forum: General Help
---

### Post by Dilligaf on 2006-06-27
hi, I'm running mythtv with firewire support which works great except for one problem, the pot assigned to the firewire to my cable box changes ports. When I run plugreport the port changes from 0  to 1 to 2 if I reboot or turn the cable box off and on.I looked at udev and was lost, I'm kind of a newbie but a quick learner. How can I force a persistent port for my firewire cable box??
Is this possible?

Host Adapter 0
==============

Node 0 GUID 0x00159afffe18ef9a
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=0, data_rate=2, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x9aef18fefe18ef9a
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 2 GUID 0x00e01800002365af
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR



Thanks Greatly for any help or guidance

Mike

Edit: It changes nodes, not ports

---

### Post by ddennedy on 2006-08-08
Just saw this while browsing around. As the 1394 libs maintainer, the answer is that you can not prevent the changing of the node id due to the nature of firewire bus management. The correct way to track a device is by its GUID. You can get the nodeid for a GUID in /sys/bus/ieee1394 or with librom1394. However, it would not be good to make libiec61883 require librom1394 just for an example and perhaps processing /sys would add noise to an example program. The solution, then, is a new utility that combines features, but that has not yet been written. It is on my TODO list to add mpeg2-ts support to dvgrab (HDV uses mpeg2-ts), which would fill this gap.

---

