---
title: "Computer is not able to boot"
date: 2010-05-03
forum: General Help
---

### Post by corniel on 2010-05-03
Hi,

My computer is not able to boot anymore. Not from hard disk, and also not from a cd.
I did a normal shut down. After that I replaced a cd drive with an other hard disk to rescue some data. But the cd-drives were not recognized anymore. Then I attached the hdd to the other IDE cable. Then the cd-drives were recognized again. But the computer is not booting anymore. 

When I try to boot from hdd, there are a lot of udevd errors, last ones:

[QUOTE=computer](...)
udevd[109]: worker [407] unexpectedly returned with status 0x0006
udevd[109]: worker [407] failed while handling '/devices/virtual/vc/vcs1'
udevd[109]: worker [274] unexpectedly returned with status 0x0006
udevd[109]: worker [274] failed while handling '/devices/virtual/block/ram14'

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device)
- Missing modules (cat /proc/modules: Is /dev)
ALERT! /dev/disk/by-uuid/2d571d37-c137-4a24-9e47-28de2ad41d79 does not exist. Dropping to a shell![/QUOTE]

The problem is not my memory, i did a memtest. That worked fine from cd. The ubuntu menu also shows up. But when i select 'boot without installing', the computer hangs. Knoppix 6.2 gives also some errors, something about a segmentation fault.

Does someone know a solution?

Greetings,
Corniël

---

### Post by corniel on 2010-05-04
Can it be that my motherboard is broken?

---

### Post by timjohn7 on 2010-12-14
I have exactly the same problem except that I did not make any hardware changes to my machine.

My errors are all udevd[##]: worker [##] faied while handling '/devices/pci0000:00/0000:00:0e.0 and then a variety of devices (usb, scsi-device etc)

I fear motherboard too, but hopefully someone can help us!

---

### Post by corniel on 2010-12-14
In my case, my motherboard or processor was broken. I replaced both, en now it workes again.

---

