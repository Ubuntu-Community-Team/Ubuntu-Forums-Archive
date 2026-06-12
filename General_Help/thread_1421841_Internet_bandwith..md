---
title: "Internet bandwith."
date: 2010-03-04
forum: General Help
---

### Post by nos09 on 2010-03-04
Last night i put a torrent to download. i noticed a thing while downloading. i noticed that my transmission shows the Down speed of 133.5
around it and my system monitor is showing 160 around down speed.

which one is right ?
and if system monitor is then how can i know that which application is eating my bandwidth. ? 

* there was no gtk (visual) application running other then songbird and transmission torrent client. ( as far as i know ):o

---

### Post by lloyd_b on 2010-03-04
> **nos09 said:**
> Last night i put a torrent to download. i noticed a thing while downloading. i noticed that my transmission shows the Down speed of 133.5
around it and my system monitor is showing 160 around down speed.

which one is right ?
and if system monitor is then how can i know that which application is eating my bandwidth. ? 

* there was no gtk (visual) application running other then songbird and transmission torrent client. ( as far as i know ):o

First, you're probably uploading at the same time that you're downloading.  These uploads require a certain amount of your download bandwith - for ever packet that you send, the machine on the other side must send an ACK (acknowledge) packet to let your machine know that the packet was received OK.

Second, transmission is probably showing you the data download rate, not taking into account any "framing" required by the bittorrent protocol.

The combination of these two is probably the difference.

Lloyd B.

---

### Post by nos09 on 2010-03-04
> **lloyd_b said:**
> First, you're probably uploading at the same time that you're downloading.  These uploads require a certain amount of your download bandwith - for ever packet that you send, the machine on the other side must send an ACK (acknowledge) packet to let your machine know that the packet was received OK.

Second, transmission is probably showing you the data download rate, not taking into account any "framing" required by the bittorrent protocol.

The combination of these two is probably the difference.

Lloyd B.

Is there any way to know that is there any hidden possible application that is running behind and using my bandwidth ( if it does ) without my knowledge ???

---

### Post by lavinog on 2010-03-05
> **nos09 said:**
> Is there any way to know that is there any hidden possible application that is running behind and using my bandwidth ( if it does ) without my knowledge ???

wireshark
netstat

---

