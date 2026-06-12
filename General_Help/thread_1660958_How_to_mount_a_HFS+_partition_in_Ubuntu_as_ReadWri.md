---
title: "How to mount a HFS+ partition in Ubuntu as Read/Write?"
date: 2011-01-06
forum: General Help
---

### Post by anzevi on 2011-01-06
I saw a lot of people asking this question on the net and most (if not all) answers points out to disabling journaling on that partition, which is not always a good idea.

So here is 1-2-3 style how to mount HFS+ partition in Ubuntu, so that you are able to write on it:

1) sudo apt-get install hfsplus hfsprogs hfsutils

2) mount -o force -t hfsplus /dev/XXX /mnt/

3) Enjoy :)

---

### Post by mykeylynx on 2011-05-02
it works but i cant write to folders already created with osx

---

### Post by coffeecat on 2011-05-02
> **mykeylynx said:**
> doesnt work no write access 

No, it wouldn't. My guess is that the OP mounted a non-journalled hfs+ partition without realising that it was non-journalled. :) You cannot write to a journalled hfs+ filesystem from Linux - not with the present state of development of the drivers.

Installing hfsplus hfsprogs and hfsutils doesn't help either.

---

### Post by mykeylynx on 2011-05-02
ok dont know what im doing wrong but after disconnect of external and restart. i cant write? Looking in the log it reads.   

hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

ok after repairing permitions on osx mounting and forcing using:


it works again

---

