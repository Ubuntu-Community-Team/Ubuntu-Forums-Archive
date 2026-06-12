---
title: "pyrit works better with core2 duo than with cuda"
date: 2009-11-18
forum: General Help
---

### Post by N3tMast3r on 2009-11-18
[FONT=Times New Roman][SIZE=3]Hi everyone,

I noticed that on my laptop pyrit works better with the corse than it does with the gpu of my videocard. How is that possible? I noticed that whan I use cuda drivers the second cpu occurency is never, ever, more than 60%. Can anyone help me to fix this problem?
Here is the report of the benchmark... first with the 2 cpus and then with cuda and 1cpu:

[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]root@ubuntu:~# pyrit -e myessid batch
Pyrit 0.2.4 (C) 2008, 2009 Lukas Lueg [http://pyrit.googlecode.com]("http://pyrit.googlecode.com/")
This code is distributed under the GNU General Public License v3

Working on ESSID 'myessid'
Error: API mismatch: the NVIDIA kernel module has version 185.18.36,
but this NVIDIA driver component has version 190.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
Processed all workunits for ESSID 'myessid'; 1146 PMKs per second.
Computed 1146.13 PMKs/s total.
#1: 'CPU-Core (SSE2)': 689.2 PMKs/s (Occ. 73.7%; RTT 0.9)
#2: 'CPU-Core (SSE2)': 684.7 PMKs/s (Occ. 93.2%; RTT 1.1)


------


root@ubuntu:~# pyrit -e myessid1 batch
Pyrit 0.2.4 (C) 2008, 2009 Lukas Lueg [http://pyrit.googlecode.com]("http://pyrit.googlecode.com/")
This code is distributed under the GNU General Public License v3

Working on ESSID 'myessid1'
Processed all workunits for ESSID 'myessid1'; 847 PMKs per second.
Computed 847.80 PMKs/s total.
#1: 'CUDA-Device #1 'GeForce 9400M G'': 687.9 PMKs/s (Occ. 91.6%; RTT 4.4)
#2: 'CPU-Core (SSE2)': 382.4 PMKs/s (Occ. 56.9%; RTT 1.4)
[/SIZE][/FONT]

---

