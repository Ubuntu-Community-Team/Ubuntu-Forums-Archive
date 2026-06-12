---
title: "stop fsck from running after 29th boot?"
date: 2011-03-04
forum: General Help
---

### Post by cain071546 on 2011-03-04
ok so i know how to stop it from just running at boot

but how do i disable it from running EVER like i never want to see it again unless im booting in recovery?


because this install of 9.10
after being fully updated on a older Toshiba satellite A75-S2292
freezes on the fsck after the 29boot at 2% 
even my backup kernel wouldn't get passed it
only way around it was booting in recovery
and the guy im setting it up for isnt very smart/older dude 
and i dont want him gettin confused when it wont boot one day

ill have his girlfriend boot it in recovery every few weeks to run the fsck

---

### Post by lithopsian on 2011-03-04
tune2fs.  Option -c sets the count interval.  You can specify 0.  Disabling completely is very dangerous.  Journalling filesystems will get corrupted and running fsck within a reasonable time interval is necessary to prevent the corruption becoming permanent.

---

### Post by dabl on 2011-03-04
```
sudo tune2fs -c 0
```

and it will never again run fsck automatically.

```
man tune2fs
``` to learn more options.  Like you can use the -i option to set a time interval, such as once every week or something like that.

---

