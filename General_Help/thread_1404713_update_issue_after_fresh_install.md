---
title: "update issue after fresh install"
date: 2010-02-11
forum: General Help
---

### Post by gabrielcik on 2010-02-11
Hello,

Every times, after a fresh install of ubuntu karmic, i use update manager for to get all possible updates and regularly on reboot i have a filesystem check  with immediate reboot.

is it normal?

Thank you

P.s.
I tried also to divide the updates, but in this way happens even twice.

---

### Post by rcayea on 2010-02-11
I wouldn't say it's normal, but I have seen where my hard drive being bad will force a file system check all the time. Maybe your hd is going bad?

---

### Post by Richard1979 on 2010-02-11
> **gabrielcik said:**
> Hello,

Every times, after a fresh install of ubuntu karmic, i use update manager for to get all possible updates and regularly on reboot i have a filesystem check  with immediate reboot.

is it normal?

Thank you

P.s.
I tried also to divide the updates, but in this way happens even twice.

I've heard that fsck is forced every 30 boots or so:
[https://lists.ubuntu.com/archives/ubuntu-doc/2007-September/009300.html](https://lists.ubuntu.com/archives/ubuntu-doc/2007-September/009300.html)

---

### Post by gabrielcik on 2010-02-11
I don't think my hd is going bad since is only 1 week old (at least i hope so :D)

It is a ocz solid 2 ssd with only 1 partition.
(for to align it i left 1mb before the partition using gparted)

I believe it is something related with some of the upgrades...

I tried to do before only the important updates and everything was fine...

then when i updated the other packages and  i restarted i got the file system check...

Thank you

---

### Post by gabrielcik on 2010-02-12
Hello,

I re-installed everything using a ext4 journal partition and this time i didn't get any file system check after rebooting. (i tried also with ext4 without journaling but in this case it would do again the file system check after update)

Another thing, this time i have also run the update on battery...

So no more issue with the ext4 journal... or maybe it was some problem with installing updates on AC...

Do u think journaling can be armful for my ssd? (i heard it is dangerous for cheap ssd coming on netbooks). Mine is a OCZ solid 2...

---

