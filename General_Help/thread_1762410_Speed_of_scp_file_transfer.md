---
title: "Speed of scp file transfer"
date: 2011-05-19
forum: General Help
---

### Post by cherva on 2011-05-19
I have two machines running open vpn connected trough a 8 port Gigabit switch (Tp-link TL-SG1008D). The problem is when I try to transfer a file the transfer starts at 13 mb/s and drops to 300kb/s. When I replaced the ram on the two machines and restarted the transfer the speed was 13mb/s constant. How does changing the ram makes such differences (at the first transfer they had 512mb at the second transfer the machines had only 128mb) ? Os Ubuntu Server 10.04.2 LTS

PS Tried with 256 ram and the problem persists...
Machines: two hp d530

---

### Post by prshah on 2011-05-19
> **cherva said:**
> How does changing the ram makes such differences (at the first transfer they had 512mb at the second transfer the machines had only 128mb)

scp transfers data via ssh protocol. This means that the data is being transferred encrypted, and both PCs have to have the grunt to manage this (one to encrypt, the other to decrypt). Possibly 128MB is not enough and leads to disk swapping (swap space usage).

---

### Post by cherva on 2011-05-19
Yes, but the transfer speed is 13mb/s with 128mb ram and the problem is when I put 256 or 512 mb ram. Then it starts at 13 mb/s and slows down to 300 kb/s.

---

