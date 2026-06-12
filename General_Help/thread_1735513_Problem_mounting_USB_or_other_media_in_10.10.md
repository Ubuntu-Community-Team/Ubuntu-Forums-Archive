---
title: "Problem mounting USB or other media in 10.10"
date: 2011-04-21
forum: General Help
---

### Post by em3raldxiii on 2011-04-21
This is a rather bizarre issue that I have not seen much info about on the Internet.  

I recently wiped my install after backing everything up, and installed a brand new Ubuntu 10.10 32 bit.  I manually partitioned my drive to have a separate partition for root, /home, /swap, and a couple of other partitions specific to my needs.

After a fully normal and complete standard install, I installed a few odds and ends (opera, k3b, a few Nautilus scripts, and a few games), and updated all out-of-date packages.

Upon rebooting, I discovered that when I plugged in ANY USB thumb drive, it gave me an error (which I have seen repeated a few times on various forums).  Specifically, it said it could not "Moint" the drive because the folder did not exist.

After briefly looking at my root directory, I discovered there was no /media folder!  This is crazy, especially for a fully released & patched Ubuntu!!

So, I created a /media directory and that's it.  Problem 100% solved for me.

Open a terminal (Applications > accessories > terminal)

```
cd /
sudo mkdir media

```

I hope this helps someone else with the same issue!

---

