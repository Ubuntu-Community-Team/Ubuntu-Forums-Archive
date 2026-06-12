---
title: "Partition Automount and Permissions"
date: 2010-01-21
forum: General Help
---

### Post by Stigmata13 on 2010-01-21
Hello.. So I recently changed my system, before I had Ubuntu 9.10 installed solely on the drive, but recently I resized so the OS partition is about 20 gigs and the Data partition is about 120 gigs, but for some reason when mounting the Data drive I don't have write permissions.
So I was wondering what I could do to have the drive automatically become mounted at start, and have write permissions for the drive.

---

### Post by quixote on 2010-01-23
Do you have an entry for the partition in /etc/fstab?  (If not, I'll give some more detailed instructions on that.)  In the options section you need the word "user".  For instance:```
UUID=some-interminable-number /data           ext3    defaults,**user**        0       2
```

Alternatively, you can mount the partition with a specific umask (also in the option section, eg umask=022), but I'm not sure that's a good idea for a big fixed data drive.

---

