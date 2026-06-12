---
title: "Intermittent but persistent problem"
date: 2010-09-17
forum: General Help
---

### Post by digimark on 2010-09-17
HI Chaps,

Running Lucid. On occasion I get a boot error saying that the /tmp directory is missing or cant be mounted. On other occasions the boot works fine and nothing is wrong. Is it possible this is a hard disk error? I do seem to be getting a lot of disk consistency checks upon boot up at the moment.

Many thanks

/Mark

---

### Post by digimark on 2010-09-17
HI Chaps,

Running Lucid. On occasion I get a boot error saying that the /tmp directory is missing or cant be mounted. On other occasions the boot works fine and nothing is wrong. Is it possible this is a hard disk error? I do seem to be getting a lot of disk consistency checks upon boot up at the moment.

Many thanks

/Mark

---

### Post by coffeecat on 2010-09-17
> **digimark said:**
> HI Chaps,

Hi, Fella. :wink:

> **digimark said:**
> Running Lucid. On occasion I get a boot error saying that the /tmp directory is missing or cant be mounted. On other occasions the boot works fine and nothing is wrong. Is it possible this is a hard disk error? I do seem to be getting a lot of disk consistency checks upon boot up at the moment.

Yes, I've noticed a greater frequency of disk checks with Lucid than with earlier versions, but I haven't investigated why.

However, a missing /tmp is odd (if it really is missing). The "can't be mounted" is odder, unless you have /tmp on another partition. Do you? The /tmp folder is cleaned up when you shut down, but not deleted. I think you need to investigate whether these are symptoms of a failing drive. If you go to System > Administration > Disk Utility, you can check the SMART data (if supported in your drive) and run a self-test.

If you haven't backed up your personal files, do so now - before doing a SMART self-test. Hopefully this is not a failing HD, but you can't be too careful.

---

### Post by uRock on 2010-09-17
Threads merged. Please do not create duplicate threads.

Thanks,
uRock

---

