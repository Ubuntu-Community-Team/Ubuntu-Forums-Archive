---
title: "Disable caching in RAM"
date: 2012-03-28
forum: General Help
---

### Post by mosquetero on 2012-03-28
Hi everyone!

I want to make some storage performance measurements using Ubuntu and for that I would like to disable the caching in the RAm so that everything that is written in the storage goes directly to the storage and not to the RAM. Can someone explain me how to do it or give me some hints? 

Thanks

---

### Post by dcstar on 2012-03-28
> **mosquetero said:**
> Hi everyone!

I want to make some storage performance measurements using Ubuntu and for that I would like to disable the caching in the RAm so that everything that is written in the storage goes directly to the storage and not to the RAM. Can someone explain me how to do it or give me some hints? 

Thanks

There is no "write" caching so to speak (except for USB devices), it just means that recently written disk data is left in the cache until replaced by read data.

The **hdparm -Tt** command pair gives a cached (memory) read as well as a direct disk read so you can see the difference.

---

### Post by mosquetero on 2012-03-28
Ok. I just want to make some storage performance tests using IOmeter and I really want to avoid the cache to be used since it will get disturb the results. Do you know how can I do it?

Thank you

---

