---
title: "Disk Space on ROOT filling up"
date: 2010-12-27
forum: General Help
---

### Post by synergie on 2010-12-27
Hi there,

I've done a search to help resolve my problem and done as it said, emptied the tmp and trash directories on root. But I still seem to be running out of space? Something is really wrong as I allocated at least 30 gigabytes of space to ubuntu but now only have 250mb left.

Can anyone help me out? Please let me know what information I should share with you.

Thanks

I'm using ubuntu 10.10 64 bit

---

### Post by synergie on 2010-12-27
Here are my file systems (attached)

---

### Post by synergie on 2010-12-27
I am guessing because this is a 64bit system with only 2 gigabytes of ram, my swap space is filling up rather quickly.

---

### Post by mcduck on 2010-12-27
Your sap space isn't any of those partitions, it's  on it's own partition. And 2GB is plenty of RAM.

Anyway, your root partition is just 4,8GB, which really isn't much. There's nothing special going on, you simply should have reserved a bit more space for root... (It doesn't help if you available space on *other* partitions, things that need to go to root partition go to root partition and can't use space from your larger home partition).

If you haven't done it already, run "sudo apt-get clean" to remove apt's cached packages. And after that I'd recommend looking for a way to grow your root a bit larger...

---

### Post by synergie on 2010-12-27
> **mcduck said:**
> 

And after that I'd recommend looking for a way to grow your root a bit larger...


Any thoughts/recommendations on how to do this?

Thanks

---

