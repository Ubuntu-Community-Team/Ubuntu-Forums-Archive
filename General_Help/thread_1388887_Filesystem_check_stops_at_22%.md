---
title: "Filesystem check stops at 22%"
date: 2010-01-23
forum: General Help
---

### Post by MichaelPalin on 2010-01-23
My Ubuntu is running a filesystem check every time it boots, but, for some reason I would like to know, it never goes past 22%, it stays there forever. It says something like this:

```
Filesystem check in progress:
/(dev/disk/b-uuid/f10e9666-...)
```

What follows are just numbers and letters. It refreshes continuously, but the sentence shown is always the same, the same numbers and letter. I have wait for a couple of minutes and it stays at 22%.

There is no external drive or pendrive connected and the HDD, has a Windows partition in it.

Any idea? Thanks in advance

---

### Post by dcstar on 2010-01-24
> **MichaelPalin said:**
> My Ubuntu is running a filesystem check every time it boots, but, for some reason I would like to know, it never goes past 22%, it stays there forever. It says something like this:

```
Filesystem check in progress:
/(dev/disk/b-uuid/f10e9666-...)
```

What follows are just numbers and letters. It refreshes continuously, but the sentence shown is always the same, the same numbers and letter. I have wait for a couple of minutes and it stays at 22%.

There is no external drive or pendrive connected and the HDD, has a Windows partition in it.

Any idea? Thanks in advance

Boot off a live CD and run a fsck on the partition.

---

### Post by MichaelPalin on 2010-01-24
Can you elaborate a little bit on your answer? Why can't I fsck from Ubuntu? What should I expect when doing a fsck from a CD?

By the way, isn't the file system at the start up a fsck by itself?

---

### Post by bakegoodz on 2010-01-24
Could be a bad sector on the hard drive. Try the drives manufacturers diagnostic CD on the drive. First try doing a quick test, if it says there is problem with the drive, immediately backup important files and get a replacement drive. If not, do a full media scan it may find bad sectors, the utility will remap these with reserve sectors. This all is done inside the hard drive's systems, the file system knows nothing about remapped sectors.



[http://support.wdc.com/product/download.asp?groupid=502&sid=30&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=30&lang=en)

[http://download.seagate.com/seatools/registration.nsf/desktop?openform](http://download.seagate.com/seatools/registration.nsf/desktop?openform)

---

### Post by MichaelPalin on 2010-01-25
Thanks a lot.

---

