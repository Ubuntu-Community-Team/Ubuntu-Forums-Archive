---
title: "disk error"
date: 2011-08-21
forum: General Help
---

### Post by pjalegria on 2011-08-21
Hi

I have Lubuntu installed with my home partition on 8gb SD card, yesterday at boot i have disk errors on my home partition, i have boot with a live cd and start a disk verification with gparted.He is doing verification for 12h and still is doing it, is that normal???

---

### Post by An Sanct on 2011-08-21
SD cards are slow, but 12h is alot...

The card maybe defect - the write count may be over the normal, so bad sectors could appear.

Can you check how gparted is set up to handle defects (retry count) and can you tell us if you also have swap on the SD card (gparted likes to uses native present swap)

---

### Post by jfed on 2011-08-21
I had a similar problem, my card was physically damaged.

---

