---
title: "Transmission ignores upload limits."
date: 2010-03-20
forum: General Help
---

### Post by Anhedonia on 2010-03-20
Hey guys,

Today I noticed, that despite a 1kb/s limit upload being set i was seeding at an unlimited bandwidth, it had been running for 3 hours wasting about 300mb.

I had never seen this before, however 10gb mysteriously disappeared from my 25 quota last month as i dont mind seeding things at 1kb to help people get the missing bits. My 25gb costs me $100 with the larger package being $160 so i dont have much choice but to be stingy.

I've read several Ubuntu bugs claiming this to be fixed? from as long as 1 year ago.

Can anyone recommend a trustworthy torrent client?

An

---

### Post by _h_ on 2010-03-20
You might have done something wrong, like enter a wrong number or forgot to enable the cap, since my Transmission I have set to 500kb/s down and 5kb/s up and it's never violated those numbers...ever.

---

### Post by roccivic on 2010-03-20
applications -> accessories -> terminal

```
rm -r ~/.transmission/*
```

This will wipe transmissions preferences clean and should fix your problem.
Warning: It will also take out all the cache, stored torrents, etc.

---

### Post by wojox on 2010-03-20
Deluge, it's in the repo's.

---

