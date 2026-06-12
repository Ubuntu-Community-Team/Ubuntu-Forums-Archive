---
title: "Manual Partitioning help."
date: 2011-04-25
forum: General Help
---

### Post by karthick87 on 2011-04-25
These are the hardware configurations, can any one say me the manual partitioning details for those configuration for a speedy system..
[B][COLOR=Black]
Hardware Configurations:[/COLOR][/B]

Harddisk : 250 GB
RAM : 1 GB

Please say me the following details,

SWAP : ?
BOOT : ?
ROOT : ?

---

### Post by Rubi1200 on 2011-04-25
Hi Karthick,

first of all, why do you need/want a separate /boot partition and do you want a /home partition?

This is how I might do it (others can also add their ideas):

SWAP = 2GB

ROOT = 15-20GB

HOME = the rest of the drive

edit: if you really need a /boot partition it should probably be about 100MB if I am not mistaken, but certainly 500MB would be more than enough.

---

### Post by karthick87 on 2011-04-25
Thanks a lot Rubi1200. What's the use of swap?

---

### Post by Rubi1200 on 2011-04-25
> **karthick87 said:**
> Thanks a lot Rubi1200. What's the use of swap?
Best explanation is here:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

