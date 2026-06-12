---
title: "Missing Hard Drive Space"
date: 2011-02-09
forum: General Help
---

### Post by BNZBKK on 2011-02-09
On a fresh install my 320GB computer shows a 317GB 'File System' a 'Swap Capacity of 3.1GB and 'Free Space' 273.8GB !

The 317GB doesn't want to partition

How do I get access to the remaining 43GB ..less whatever elbow room Linux needs to utilise which is not 43 GB !

---

### Post by migs73 on 2011-02-09
Good news!!

You 320GB HDD really only has 317GiB of space (that's gibibytes not the gigabytes manufacturers use).

This mean your only missing 40GiB not 43! ;)

When you say the drive won't partition, when are you trying to do so and how are you installing ie. manually partitioning (the 'advanced' installer option) or letting the installer do all the work and trying to do so after?

---

### Post by BNZBKK on 2011-02-09
Thanks for your response.

I'm letting the installer do the work as I can't reformat the 317GB manually partitioning it and 'after' (auto) install it still won't reformat.

---

### Post by P4man on 2011-02-09
You didnt lose anything. Harddrive capacity is usually incorrectly given as if 1GB were 1 billion bytes. But its not. In reality it is 2exp30 bytes, or 1073741824 bytes. Thats why you 'lose' almost 10% drive capacity. Ubuntu is only using ~3GB. More here:

[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by BNZBKK on 2011-02-09
Aha, so it's OK then 

Thank you for the enlightenment on false advertising

---

### Post by srs5694 on 2011-02-09
Don't be too harsh on the disk manufacturers. The whole issue of the meaning of "gigabytes" (or "GBs"), and of similar units, has been controversial and confusing for decades. In recent years, new standards have emerged (namely [IEEE-1541](http://en.wikipedia.org/wiki/IEEE_1541)) that clearly define the relevant meanings. To summarize the new system, use of "KB", "MB", "GB", etc. (that is, SI prefixes) should be used only in reference to power-of-ten units -- so 1 MB is 1,000,000 bytes, for instance. New units (KiB, MiB, GiB, and so on, pronounced "kibibytes", "mebibytes", "gibibytes", and so on) refer to power-of-2 units -- so 1 MiB is 1,048,576 bytes.

Many here on this forum dislike the new standards, but IMHO the new units are a good thing in the long run. Used properly and consistently, they improve precision and clarity in discussions about disk sizes, memory sizes, etc.. The main problem is getting people to understand them and use them properly.

---

