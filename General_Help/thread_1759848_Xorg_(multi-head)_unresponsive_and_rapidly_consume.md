---
title: "Xorg (multi-head) unresponsive and rapidly consumes all memory after unlock"
date: 2011-05-16
forum: General Help
---

### Post by Fastdruid on 2011-05-16
I've a problem where after attempting to unlock my 10.10[1] gnome desktop that the screen stays black and the cursor jumps rapidly between two screens and Xorg rapidly consumes *VAST* amounts of memory (and quite a bit of CPU) until the oom-killer kills it.

I can log in remotely via ssh, machine itself is slow but still responding although the GUI is non-responsive.

As can be seen below, Xorg has taken 14.8G!

top - 17:59:59 up 3 days, 7:32, 18 users, load average: 17.28, 10.08, 6.69
Tasks: 306 total, 2 running, 281 sleeping, 3 stopped, 20 zombie
Cpu0 : 2.5%us, 14.5%sy, 0.9%ni, 81.4%id, 0.7%wa, 0.0%hi, 0.0%si, 0.0%st
Cpu1 : 2.5%us, 15.7%sy, 0.9%ni, 80.4%id, 0.4%wa, 0.0%hi, 0.0%si, 0.0%st
Cpu2 : 3.4%us, 14.9%sy, 0.9%ni, 79.8%id, 0.9%wa, 0.0%hi, 0.1%si, 0.0%st
Cpu3 : 3.6%us, 15.7%sy, 0.9%ni, 79.3%id, 0.4%wa, 0.0%hi, 0.1%si, 0.0%st
Mem: 8193768k total, 8146352k used, 47416k free, 2336k buffers
Swap: 13058448k total, 13058128k used, 320k free, 17452k cached

  PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
 1800 auser 20 0 363m 8048 8048 R 110 0.1 62:13.09 compiz
 2637 auser 20 0 1755m 1.0g 1.0g S 99 13.3 2409:06 VirtualBox
 1447 root 20 0 **14.8g** 3.6g 944 D 11 46.1 202:14.59 Xorg
19178 auser 20 0 3617m 2.7g 2.7g S 6 34.2 195:26.96 VirtualBox
 2260 root 20 0 19412 1364 860 R 4 0.0 0:00.05 top
 1622 root 20 0 55424 2024 1240 D 2 0.0 0:00.87 polkitd
    1 root 20 0 23896 452 0 S 0 0.0 0:03.10 init
    2 root 20 0 0 0 0 S 0 0.0 0:00.00 kthreadd
    3 root 20 0 0 0 0 S 0 0.0 0:19.11 ksoftirqd/0
    4 root RT 0 0 0 0 S 0 0.0 0:00.96 migration/0
    5 root RT 0 0 0 0 S 0 0.0 0:00.00 watchdog/0
    6 root RT 0 0 0 0 S 0 0.0 0:00.28 migration/1
    7 root 20 0 0 0 0 S 0 0.0 0:31.73 ksoftirqd/1
    8 root RT 0 0 0 0 S 0 0.0 0:00.00 watchdog/1
    9 root RT 0 0 0 0 S 0 0.0 0:01.22 migration/2
   10 root 20 0 0 0 0 S 0 0.0 10:11.75 ksoftirqd/2
   11 root RT 0 0 0 0 S 0 0.0 0:00.00 watchdog/2

For reference in how fast memory usage grows this is the machine just after it locked.

top - 17:46:14 up 3 days, 7:18, 18 users, load average: 7.68, 4.75, 2.34
Tasks: 299 total, 4 running, 292 sleeping, 3 stopped, 0 zombie
Cpu0 : 2.3%us, 14.5%sy, 0.9%ni, 81.6%id, 0.6%wa, 0.0%hi, 0.0%si, 0.0%st
Cpu1 : 2.4%us, 15.7%sy, 0.9%ni, 80.6%id, 0.4%wa, 0.0%hi, 0.0%si, 0.0%st
Cpu2 : 3.4%us, 14.9%sy, 0.9%ni, 80.0%id, 0.7%wa, 0.0%hi, 0.1%si, 0.0%st
Cpu3 : 3.4%us, 15.7%sy, 0.9%ni, 79.5%id, 0.4%wa, 0.0%hi, 0.1%si, 0.0%st
Mem: 8193768k total, 8118668k used, 75100k free, 316k buffers
Swap: 7960852k total, 3910980k used, 4049872k free, 19380k cached

  PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
 1800 auser 20 0 363m 8588 8588 R 121 0.1 46:30.21 compiz
 1447 root 20 0 5401m 3.4g 1504 R 101 43.1 192:28.90 Xorg
 2637 auser 20 0 1755m 1.0g 1.0g S 99 13.3 2403:05 VirtualBox
   47 root 20 0 0 0 0 D 12 0.0 0:20.94 kswapd0
19178 auser 20 0 3617m 2.7g 2.7g S 5 34.2 194:08.78 VirtualBox
  295 root 20 0 0 0 0 D 1 0.0 0:06.25 usb-storage
 1685 auser 20 0 19412 1076 676 R 1 0.0 0:00.67 top
    1 root 20 0 23896 296 260 S 0 0.0 0:03.10 init
    2 root 20 0 0 0 0 S 0 0.0 0:00.00 kthreadd
    3 root 20 0 0 0 0 S 0 0.0 0:18.85 ksoftirqd/0
    4 root RT 0 0 0 0 S 0 0.0 0:00.81 migration/0
    5 root RT 0 0 0 0 S 0 0.0 0:00.00 watchdog/0
    6 root RT 0 0 0 0 S 0 0.0 0:00.28 migration/1
    7 root 20 0 0 0 0 S 0 0.0 0:31.50 ksoftirqd/1
    8 root RT 0 0 0 0 S 0 0.0 0:00.00 watchdog/1
    9 root RT 0 0 0 0 S 0 0.0 0:01.20 migration/2
   10 root 20 0 0 0 0 S 0 0.0 10:10.17 ksoftirqd/2

Any suggestions as to how I can diagnose further or fix? None of the logs have anything useful in.

Druid

[1] Unity doesn't work with multi-head on my very similar home PC and this is my work PC so I can't risk the upgrade.

---

