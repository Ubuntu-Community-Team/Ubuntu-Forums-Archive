---
title: "cache information"
date: 2010-07-18
forum: General Help
---

### Post by sulekha on 2010-07-18
Hi all,

I tried to get cache information on my machine as follows

getconf -a | grep -i cache

zodiac@zodioc:~$ getconf -a | grep -i cache
LEVEL1_ICACHE_SIZE 32768
LEVEL1_ICACHE_ASSOC 8
LEVEL1_ICACHE_LINESIZE 64
LEVEL1_DCACHE_SIZE 32768
LEVEL1_DCACHE_ASSOC 8
LEVEL1_DCACHE_LINESIZE 64
LEVEL2_CACHE_SIZE 1048576
LEVEL2_CACHE_ASSOC 8
LEVEL2_CACHE_LINESIZE 64
LEVEL3_CACHE_SIZE 0
LEVEL3_CACHE_ASSOC 0
LEVEL3_CACHE_LINESIZE 0
LEVEL4_CACHE_SIZE 0
LEVEL4_CACHE_ASSOC 0
LEVEL4_CACHE_LINESIZE 0



does this listing means that LINESIZE of my L2 cache is 64 bytes and that L2 cache is divided into units comprising of 8 cache lines(each of 64 bytes in size) ?

---

### Post by dino99 on 2010-07-18
some help there:

[http://www.networknuts.net/Performance_tuning-3.pdf](http://www.networknuts.net/Performance_tuning-3.pdf)

---

