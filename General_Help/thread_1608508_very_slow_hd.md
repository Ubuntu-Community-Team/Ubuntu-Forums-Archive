---
title: "very slow hd"
date: 2010-10-29
forum: General Help
---

### Post by marcocapolupi on 2010-10-29
Hi, first post here..

The problem is very simple:
Two computers, A and B, same ubuntu 10.04 64bit,same kernel 2.6.32-24-generic, same disks westeren digital.

After a fresh install, the computer B works fine, but after the first reboot it's extremely slow.

On computer A:
```
marco@marcopc:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   7954 MB in  2.00 seconds = 3980.23 MB/sec
 Timing buffered disk reads:  214 MB in  3.01 seconds =  71.12 MB/sec
```

On computer B:
```
server@server:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1082 MB in  2.00 seconds = 540.87 MB/sec
 Timing buffered disk reads:    8 MB in  3.21 seconds =   2.49 MB/sec
```

The disk on computer B when benchmarked on computer A works fine.

Any ideas?
Thanks,
Marco

---

### Post by Omnomnom on 2010-10-29
How much space left do you have on each? And also consider the possibility that the slow one could be faulty? Can you hear any grinding sounds as it's running?

---

### Post by prshah on 2010-10-29
> **marcocapolupi said:**
> The disk on computer B when benchmarked on computer A works fine.

Clearly looks like a computer/motherboard fault. Check the BIOS settings of the board, and ensure that SATA options are set to "Native", "Optimal", etc instead of "Legacy", "Compatible", etc. Sorry cannot be more specific since the options vary from BIOS to BIOS.

Can you find any relevant fault messages in the logs?

---

