---
title: "apt-get update error"
date: 2011-10-20
forum: General Help
---

### Post by sledhead45 on 2011-10-20
Hi All-
I recently upgraded from 11.04 to 11.10. 11.10 seems to be running good except apt seems to be broken now. I noticed I hadn't gotten any updates for several days, so I opened up the terminal and did a ```
sudo apt-get update
```
which returned: 
```
E: The method driver /usr/lib/apt/medhods/http could not be found.
```
*notice the "medhods" which i believe should be "methods"*

I did some googleing around. I unchecked all software sources and completely cleared out my /etc/apt/sources.list.. This eliminates the error, but re-adding any repo makes the error return. 

I also tried a 
```
apt-config -o dir::bin::methods=/usr/lib/apt/methods
```
which didnt seem to do anything.

thoughts anyone? 

Thanks

---

### Post by bibble235 on 2011-10-20
[http://forum.eeeuser.com/viewtopic.php?id=18452](http://forum.eeeuser.com/viewtopic.php?id=18452)

Perhaps an error in the source list?

---

### Post by sledhead45 on 2011-10-20
An error in the source list was my first thought also which is why I deleted everything in the source.list and just added 1 entry which I know to be correct. I tried individually adding several different correct lines all of which produced that same error. Thanks for the quick reply tho :D

---

