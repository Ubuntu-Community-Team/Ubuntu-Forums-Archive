---
title: "bitTorrent / 4 ntfs part /swap space/packet scanner"
date: 2010-07-23
forum: General Help
---

### Post by vaibhav292 on 2010-07-23
(1) i have a super-slow net connection with a limit of (200MB/3days)..so i dont want to seed my files wit bitTorrent..
.
.
(2)I have a 4 ntfs partitions which have some free space i want to utilise, in my ubuntu using ext3 patition, how could i do safely create free space w/o disturbing my other drives(one has vista on it)??
.
.
(3)I carelessly created 4GB swap space which is now going waste!! could i decrease it and use it somwhere else??
.
.
(4)Could you please tell me a tool which could scan packets coming to my firewall.

---

### Post by ubunterooster on 2010-07-23
(1)under Applications>Internet>Transmission BitTorrent client>Edit>preferences>speed>Limit upload. Limit to 1 KBPS

(2) and (3) Go to a liveCD, figure which partition has windows and (using Gparted on the liveCD) delete all the others and the swap and make them into one partition

(4)install Internetwork Routing Protocol Attack Suite ```
irpas
```

---

