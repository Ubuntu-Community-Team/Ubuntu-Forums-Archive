---
title: "Server 12.04 64bit crashed - does not recover"
date: 2012-06-13
forum: General Help
---

### Post by stormbind on 2012-06-13
I have been running 12.04 Server in Oracle VirtualBox.

The VM crashed overnight, when I relaunch the VM:

1. Ubuntu is very slow to ready the swap (continues to wait)
2. Ubuntu is unable to boot with full network configuration
3. Ubuntu hangs after printing * Starting AppArmor profiles [OK]

When I try recovery mode:

Check file-system: Ubuntu *hangs* after printing /dev/sda1 230/124496 files (1.3% non-contiguous), 43643/248832 blocks

The VM contains my source code repository. How do I recover Ubuntu?

---

### Post by stormbind on 2012-06-13
Anyone? :(

---

### Post by stormbind on 2012-06-13
Using "Recover", some selections and ^C I can get to a bash prompt.

From bash everything looks OK. My repository server is running. I can checkout/submit code.

It seems to me that on normal boot-up, Ubuntu Server is trying to mount partitions that do not exist.

---

