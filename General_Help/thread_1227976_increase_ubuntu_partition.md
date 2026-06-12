---
title: "increase ubuntu partition"
date: 2009-07-31
forum: General Help
---

### Post by affenzeit on 2009-07-31
I decided to test drive Ubuntu for awhile and it is growing on me a lot. So much, in fact that  I realize I didn't give myself enough room on my ubuntu partition. I'm running a dual boot with vista and vista can pretty much suck it from now on. I want to to leave vista in place just in case, but I want to  move a lot of space from my vista partition to my ubuntu partition. I've looked at GParted, but I'm not really sure what I should do, and everything I've searched has to do with the initial installation, but my system is already set up. What's the best route to go?

---

### Post by hibliss on 2009-07-31
> **affenzeit said:**
> I decided to test drive Ubuntu for awhile and it is growing on me a lot. So much, in fact that  I realize I didn't give myself enough room on my ubuntu partition. I'm running a dual boot with vista and vista can pretty much suck it from now on. I want to to leave vista in place just in case, but I want to  move a lot of space from my vista partition to my ubuntu partition. I've looked at GParted, but I'm not really sure what I should do, and everything I've searched has to do with the initial installation, but my system is already set up. What's the best route to go?

Defrag Vista a few times first, them shrink the partition as much as possible. A fragmented Windows filesystem will not allow you to shrink it. You will have to resize it from the utility in Windows, think it is "disk management".

Now after you have some free space (unformatted), you can expand the ext partition Ubuntu is on with gparted. You will have to boot from LiveCD to do so because the partition you are manipulating cannot be mounted.

---

### Post by merlinus on 2009-07-31
Good how-to here:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

