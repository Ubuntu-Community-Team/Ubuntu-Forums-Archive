---
title: "Multiple copy threads sometimes get stuck on the last one."
date: 2011-11-15
forum: General Help
---

### Post by JayKay3OOO on 2011-11-15
Let me pick your brains on this as I only just remembered about it.

I copied about 60GB of music and work using A 3.4GHZ AMD quad core machine with 4GB DDR3 RAM.

The transfer was from a 72k rpm 3.5inch drive to a 54k rpm 2.5 inch drive and the transfer was done using about 6 different copy threads. Both drives are SATA drives. 

They all completed fine except the last one that hung on a few document files. During the hang time the OS worked fine, but I noticed that the 1st core (that seems to get bashed the most in Linux) got pegged at 100% meaning I had to stop the transfer and re-copy the last few files or sit there for eternity looking at it.

I've not noticed this when copying between 72 to 72k rpm drives on the same machine, but I did notice the same problem when copying from my AMD e350 fusion machine to the AMD quad core machine using a mix of 72k and 54k rpm drives. Single transfers fine, but then multiples sometime get stuck.

I guess I'm not really looking for a fix as I don't do multiple transfers that often between different speed drives.

Still... Would be nice to know if anyone else has notice this.

---

