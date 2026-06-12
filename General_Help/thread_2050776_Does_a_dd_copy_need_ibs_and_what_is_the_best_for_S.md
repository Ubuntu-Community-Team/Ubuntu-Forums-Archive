---
title: "Does a dd copy need ibs and what is the best for SD cards?"
date: 2012-08-31
forum: General Help
---

### Post by fixitdude on 2012-08-31
I am using dd to copy a 4GB SDHD card and I have seen examples using ibs= and bs= of 512 to 4096.

It's going really slow at ibs=512 but I am not sure if I will miss end bytes in the card if I set 4096 and it doesn't come up a even number of 4096 blocks.

So the question is, which one should you use bs or ibs, does it matter and how can you speed the reading and writing speed up on these things? It takes about a hour to just read it and another hour to write one back.

Example read:
dd if=/dev/sdd of=/home/user/4GB-SD-card.img ibs=512

Write:
dd if=some-image.img of=/dev/sdd bs=512 && sync && sync

Is 512 the way to go to be safe?

---

