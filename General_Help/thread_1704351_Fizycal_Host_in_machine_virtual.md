---
title: "Fizycal Host in machine virtual"
date: 2011-03-10
forum: General Help
---

### Post by saltcushy on 2011-03-10
Hi gus
I installed two systems in Disc Winxp,ubuntu10.10 but I don't wanna install again WinXP I want physical WinXP adds to VitualMachine or other on Ubuntu.
Vmware workstation can boot physical Host but is't free as well in p2p lack for DEB and soure binare+patch linux, hard are compitatios.
Any help me find way?

---

### Post by saltcushy on 2011-04-30
# dd if=/dev/sda1 of=winxp.mbr bs=512 count=1
# VBoxManage internalcommands createrawvmdk -filename winxp.vmdk -rawdisk /dev/sda -partitions 1,5 -mbr winxp.mbr -relative -register

solved :)

---

