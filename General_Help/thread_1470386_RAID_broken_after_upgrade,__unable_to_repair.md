---
title: "RAID broken after upgrade,  unable to repair"
date: 2010-05-02
forum: General Help
---

### Post by TheSilverHornet on 2010-05-02
More specifically, after upgrading, the device names seem to have shuffled around a bit, and raid broke.  I'm unable to rebuild the array, it seems to value the old device names more highly than the uuid's, and errors out.

Pastebin of the current drive situation is at [http://www.pastebin.com/2AT9fQYF](http://www.pastebin.com/2AT9fQYF) .  The drives used to be sda, sdb and sdc, but somehow the dvd drive took over sdb post-upgrade.  You can see my attempts to sort the situation here, and the results: [http://www.pastebin.com/t8wPxZHu](http://www.pastebin.com/t8wPxZHu) .

I can get to busybox on the PC, and am using a liveCD to try to repair it.  Any help you can provide is much appreciated... but please don't 'guess', I have a lot of important data on this array that I would much prefer not to lose if possible.

Many thanks. :)

---

### Post by TheSilverHornet on 2010-05-03
bump

---

### Post by TheSilverHornet on 2010-05-03
bump again, this is a critical problem, please help. :(

This is the latest situation: [http://pastebin.com/TzMnu8q1](http://pastebin.com/TzMnu8q1)

---

### Post by Justinsaccount on 2010-05-03
This is the only relevant message in your logs:

```
mdadm: no recogniseable superblock on /dev/sde1
mdadm: /dev/sde1 has wrong uuid.

```You've never posted the output of this though:

```
mdadm --examine /dev/sde1
```sdb bumped the drives up to sde, but I don't see where you ever tried assembling the array from a,c,d,e.  You should run this, and see what it says:

```
mdadm --assemble -v /dev/md0 /dev/sd{a,c,d,e}1
```

---

### Post by TheSilverHornet on 2010-05-09
It's been sorted now, something very bizarre happened & I had to recreate the array ... which has caused another issue I should make a separate post about.  Cheers anyway.

---

