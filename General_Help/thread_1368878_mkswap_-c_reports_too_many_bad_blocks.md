---
title: "mkswap -c reports too many bad blocks"
date: 2009-12-31
forum: General Help
---

### Post by Selmi on 2009-12-31
i had problem with my computer, when too many applications were running and swap was used quite a lot then sometimes, especially when i tried to copy large files (1GB and more) i got complete computer freeze (ok, computer itself worked because i could connect to it from other machine, but keyboard, mouse etc. didn't responded at all). when i did restart no problems were detected. also i noticed that often when i did correct shutdownn it failed and i was stuck on screen with messages, last message was about switching off swap space (i don't remember it correctly)

so i started to think thereissomething wrong with swap partititon

and now fun starts
badblocks -f -s -v /dev/sda8 runs about for 3 minutes and reports no problem
mkswap -c /dev/sda8 runs for about 6 hours and ends with message about too many bad blocks!
if i changed swap partition to ext2 and made fsck -c /dev/sda8 it also reported no problem

what now? disk seems to be ok and swap has problems anyway?
what does itall mean?

i have ubuntu 9.10 64bit with all updates but upstart which is still in version provided by karmic koala itself (becauseofproblems afterupgrade)

computer has 2GB of RAM + 4GB of swap space. freezing problems started when swap usage was about 16%

---

### Post by spiderbatdad on 2009-12-31
Many users report better results forcing the system to swap less aggressively. Edit /etc/sysctl.conf
```
# use less swap
vm.swappiness=10
# use less cache
vm.vfs_cache_pressure=50

```

---

### Post by Selmi on 2010-01-05
i didn't had crash since proposed change, thanks

but still, 'mkswap -c' reports bad blocks and 'badblocks' doesn't, and its a bit scarty.... any idea what could cause it?

---

