---
title: "Can I write to memory as though it were a file?"
date: 2009-09-10
forum: General Help
---

### Post by fizzybrain on 2009-09-10
I want to dump debugging information from some perl code to a file, but it seems silly to keep accessing the disk (maybe 1,000 times a second). On Windoze I simply created a ramdisk and wrote to a file there. Can I do a similar thing in linux, writing to RAM as though it were a file?
I'm sure that I can as linux treats *everything* as a file :-) , I just don't know how to do it!

I know my code could be changed, but I'm not really much of a programmer and time is short.

Share and Enjoy,
Fizzybrain

---

### Post by P4man on 2009-09-10
This makes a 64Mb ramdisk in /ramdisk:

```
sudo mkfs -t ext3 -q /dev/ram1 65536
sudo mkdir -p /ramdisk
sudo mount /dev/ram1 /ramdisk -o defaults,rw
```

---

### Post by fizzybrain on 2009-09-10
Excellent, thanks.
(had to change permissions to let me write to it)

Is there still a "thanks" button on these forums?

---

### Post by fizzybrain on 2009-11-17
FOLLOWUP:    It's also worth looking up "tmpfs". A fixed size of ramdisk must be specified, but it will use swap space if necessary (e.g. if "real" applications need more physical ram). And you can put it into /etc/fstab really easily.

---

### Post by imtheguru on 2009-11-17
> **fizzybrain said:**
> FOLLOWUP:    It's also worth looking up "tmpfs". A fixed size of ramdisk must be specified, but it will use swap space if necessary (e.g. if "real" applications need more physical ram). And you can put it into /etc/fstab really easily.

Just fyi, /dev/shm is a ready to use shared memory of type tmpfs.

---

