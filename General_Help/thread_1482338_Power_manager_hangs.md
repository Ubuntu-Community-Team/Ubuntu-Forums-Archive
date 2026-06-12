---
title: "Power manager hangs"
date: 2010-05-13
forum: General Help
---

### Post by muzikill on 2010-05-13
When the pc is powered up it takes ages for the login screen to come up and after that it hangs then comes up with a power manager is not responding fault, when i get into the desktop it takes ages for the top bar to appear and i noticed that the wireless usb dongle takes ages to connect.....

could the problem be with everyone a usb hang at boot?

i have recently installed a usb printer.

Weirdly a reboot fixes the issue, it seems to be at times the very first boot up where the problem arises.

---

### Post by mike555 on 2010-05-13
How much RAM memory do you have? is your swap file working and big enough?

---

### Post by muzikill on 2010-05-13
2gig memory
[B]
cat /proc/meminfo[/B]
results


MemTotal:        2061384 kB
MemFree:          539796 kB
Buffers:           58584 kB
Cached:          1068492 kB
SwapCached:            0 kB
Active:           592604 kB
Inactive:         806944 kB
Active(anon):     182652 kB
Inactive(anon):    93876 kB
Active(file):     409952 kB
Inactive(file):   713068 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187528 kB
HighFree:           1736 kB
LowTotal:         873856 kB
LowFree:          538060 kB
SwapTotal:        563192 kB
SwapFree:         563192 kB
Dirty:               140 kB
Writeback:             0 kB
AnonPages:        272388 kB
Mapped:            90300 kB
Shmem:              4056 kB
Slab:              93780 kB
SReclaimable:      83948 kB
SUnreclaim:         9832 kB
KernelStack:        2112 kB
PageTables:         6288 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1593884 kB
Committed_AS:     931412 kB
VmallocTotal:     122880 kB
VmallocUsed:       30904 kB
VmallocChunk:      80380 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      126968 kB
DirectMap4M:      782336 kB

---

### Post by mike555 on 2010-05-13
ok, if your talking about starting from sleep you should have a swap file at least as big as your ram ... if your talking about starting from a shut down it might be a graphics problem where grub needs to be moded to more quickly find your graphics card .... search for remedies , there are lots in the forum .


 haven't hear of any troubles with printers slowing startup.

---

