---
title: "Cloning a disk -- misbehaviour in gparted and dd?"
date: 2012-09-13
forum: General Help
---

### Post by lupoph on 2012-09-13
First of all, let it be said: I don't really have a problem anymore. Everything works. I am just confused about some errors produced by the use of gpartedd and dd and want to know their origin for merely educational purposes and future reference ;)

I was using an Ubuntu 12.04 live cd for cloning my drives from a 256 GB SSD to a 512 GB SSD, containing a Windows 7 installation (UEFI boot). 

**1. dd corrupts MBR?**

I just did
```
sudo dd if=/dev/sda bs=32M | sudo dd of=/dev/sdb bs=32M
```

Yes, I know "dd if= of=" would have done the same, but at first the piped version was faster and anyway, it did the job ;) When I controlled the output drive in gparted, all partitions where as they are meant to be. 

Anyway, when I installed the cloned drive I only got a "operating system not found" message. Using the Windows Recovery DVD allowed me to restore the MBR, but I would have expected dd to copy the MBR just like everything else.

I'm curious though what dd failed to copy. Is there some kind of meta-data inaccessible to dd? Is the MBR invalid, if the disk size doesn't match? After all the MBR should have been copied over when cloning the device. 

**2. gparted: "Partitions may not overlap"**

I then wanted to adjust my three non-hidden partitions to the new disk size using gparted. The first step was to move /dev/sda7 ("E:") to the end of the disk and grow it from 43 to 50 GB. The transitions should have been somethink like this:

```

1. |Hidden|C:-|D:--------|E:---|#EMPTY#####################|
  to
2. |Hidden|C:-|D:--------|#EMPTY###################|E:---|#|
  to
3. |Hidden|C:-|D:--------|#EMPTY###################|E:-----| 

```

Curiously the step from 2 to 3 failed, saying "Partitions may not overlap". 

I then booted into windows, seeing that the drives worked fine at least. Using windows-internal tools I then was able to make the transition from
```

   |Hidden|C:-|D:--------|#EMPTY###################|E:---|#|
  to
   |Hidden|C:-|D:---------------------------------||E:----||

```

The "||" is meant to indicate an empty spaces of 1MiB left by the Windows volume manager (which for all I know can shrink and extend partitions, but cannot MOVE partitions). 

Any idea about the reason? Is there some rule about the partitions tables that gparted is not aware of, but its backend(s) are? Also note that no such space exists between C: and D: or between the hidden system partitions.

---

