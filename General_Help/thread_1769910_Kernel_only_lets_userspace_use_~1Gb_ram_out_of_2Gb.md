---
title: "Kernel only lets userspace use ~1Gb ram out of 2Gb, rest is *reserved* for fs cache"
date: 2011-05-28
forum: General Help
---

### Post by Zorael on 2011-05-28
I've been having some great issues lately on my laptop where the system ends up thrashing, practically locking up due to overwhelming I/O work. Specifically, when applications reach 1Gb +/- buffers/cache memory use (as reported by **free -m**), the kernel starts to swap *despite* having swappiness set to 0. The machine is running Kubuntu natty.

```
zorael@lethe:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2001       1948         52          0          9        882
-/+ buffers/cache:       **[COLOR="red"]1056[/COLOR]**        945
Swap:         2102        **[COLOR="Red"]103[/COLOR]**       1998
zorael@lethe:~$ cat /proc/sys/vm/swappiness 
**[COLOR="Green"]0[/COLOR]**
```

As displayed it *can* reach above 1000Mb, but I've never seen it past 1150Mb, much less the full 2Gb. Meanwhile a swap of 500Mb+ is not uncommon.

When the congestion starts I'm basically forced to call for a manual OOM execution (Alt+SysRq+F), as the machine is completely unresponsive at that point. You can barely get the cursor to move. This usually kills the browser and work is lost.

This happens with the repository 2.6.38-8 kernel, but noteworthy is that the starts-to-swap limit is lowered to **_512_**Mb in the 2.6.39 kernel from the kernel mainline ppa. For what it's worth, my sysctl.conf is identical to the one from the repos (procps package) and I don't have any suspicious files in /etc/sysctl.d/.

Here is the dmesg output when doing the manual OOM execution. I can't make sense of it myself.

```
[ 2290.995942] Mem-Info:
[ 2290.995947] DMA per-cpu:
[ 2290.995952] CPU    0: hi:    0, btch:   1 usd:   0
[ 2290.995957] CPU    1: hi:    0, btch:   1 usd:   0
[ 2290.995961] Normal per-cpu:
[ 2290.995967] CPU    0: hi:  186, btch:  31 usd:  57
[ 2290.995972] CPU    1: hi:  186, btch:  31 usd: 144
[ 2290.995976] HighMem per-cpu:
[ 2290.995981] CPU    0: hi:  186, btch:  31 usd:  41
[ 2290.995987] CPU    1: hi:  186, btch:  31 usd: 142
[ 2290.995998] active_anon:466463 inactive_anon:8404 isolated_anon:0
[ 2290.996001]  active_file:376 inactive_file:921 isolated_file:0
[ 2290.996004]  unevictable:0 dirty:1 writeback:7 unstable:0
[ 2290.996006]  free:13227 slab_reclaimable:2875 slab_unreclaimable:7817
[ 2290.996009]  mapped:6402 shmem:225116 pagetables:3070 bounce:0
[ 2290.996079] DMA free:8084kB min:64kB low:80kB high:96kB active_anon:7508kB inactive_anon:12kB active_file:44kB inactive_file:16kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15800kB mlocked:0kB dirty:0kB writeback:0kB mapped:68kB shmem:56kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:228kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:13 all_unreclaimable? no
[ 2290.996098] lowmem_reserve[]: 0 865 2005 2005
[ 2290.996124] Normal free:43148kB min:3728kB low:4660kB high:5592kB active_anon:735920kB inactive_anon:3732kB active_file:12kB inactive_file:436kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:4kB writeback:28kB mapped:3804kB shmem:422204kB slab_reclaimable:11500kB slab_unreclaimable:31268kB kernel_stack:2680kB pagetables:3656kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 2290.996143] lowmem_reserve[]: 0 0 9125 9125
[ 2290.996167] HighMem free:1676kB min:512kB low:1740kB high:2968kB active_anon:1122424kB inactive_anon:29872kB active_file:1448kB inactive_file:3232kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1168096kB mlocked:0kB dirty:0kB writeback:0kB mapped:21736kB shmem:478204kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:8396kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 2290.996186] lowmem_reserve[]: 0 0 0 0
[ 2290.996197] DMA: 31*4kB 41*8kB 27*16kB 15*32kB 17*64kB 16*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 8084kB
[ 2290.996227] Normal: 4323*4kB 1120*8kB 346*16kB 119*32kB 38*64kB 8*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 43148kB
[ 2290.996256] HighMem: 119*4kB 134*8kB 8*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1676kB
[ 2290.996285] 226467 total pagecache pages
[ 2290.996291] 0 pages in swap cache
[ 2290.996297] Swap cache stats: add 0, delete 0, find 0/0
[ 2290.996302] Free swap  = 0kB
[ 2290.996307] Total swap = 0kB
[ 2291.009020] 521634 pages RAM
[ 2291.009026] 294324 pages HighMem
[ 2291.009030] 9350 pages reserved
[ 2291.009034] 35079 pages shared
[ 2291.009037] 486525 pages non-shared
[ 2291.009042] [ pid ]   uid  tgid total_vm      rss cpu oom_adj
***<long process list wall of text>***
[ 2291.010201] Out of memory: Kill process 3374 (chromium-browse) score 57 or sacrifice child
[ 2291.010211] Killed process 3374 (chromium-browse) total-vm:274432kB, anon-rss:115204kB, file-rss:2860kB[ 2291.009042] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
```

Obviously it's allocating the whole 2Gb, but it seems to firmly *reserve* roughly half of that for filesystem cache, instead of releasing it when applications need more work memory.

Any ideas? :<

---

### Post by cbowman57 on 2011-05-28
Set swappiness=1, I think it ignores 0, at least that's been my experience.

I used to use 0 but ran into similar experience, not sure if something changed in the kernel lately or what it is but I only have 2Gb RAM and my machine doesn't swap unless I REALLY load it up.

Let me know if that changes things for you.

---

### Post by Zorael on 2011-05-28
> **cbowman57 said:**
> I used to use 0 but ran into similar experience, not sure if something changed in the kernel lately or what it is but I only have 2Gb RAM and my machine doesn't swap unless I REALLY load it up.
I get something similar on my desktop machine with its 8Gb RAM. Even with heavy Chromium usage it never reaches that high, so swap remains a pleasant 0Mb. :>

On another note, the behavior on my laptop seems to remain even with swappiness 1.
```
*<system congested again, so manual OOM execution spam here>*
**[...]**
[ 7708.706444] Out of memory: Kill process 3382 (chromium-browse) score 27 or sacrifice child
[ 7708.706454] Killed process 3382 (chromium-browse) total-vm:242980kB, anon-rss:114440kB, file-rss:2384kB

zorael@lethe:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2001       1949         51          0          9       1086
-/+ buffers/cache:        853       1147
Swap:         2102        **[COLOR="Red"]104[/COLOR]**       1997
```
I don't have any tmpfs mounts, so that's not it...

---

### Post by cbowman57 on 2011-05-28
Very odd, I'm out of ideas, sorry. :)

---

### Post by Zorael on 2011-06-04
Bump.
```
zorael@lethe:~$ **free -m**
             total       used       free     shared    buffers     cached
Mem:          2003       1912         90          0          4       1347
-/+ buffers/cache:        [COLOR="Red"]**560**[/COLOR]       1442
Swap:         2102       [COLOR="Red"]**1105**[/COLOR]        996

zorael@lethe:~$ **uptime**
 20:36:03 up 3 days, 23:06,  6 users,  load average: 0.41, 1.04, 1.36

zorael@lethe:~$ **cat /proc/sys/vm/swappiness**
[COLOR="Green"]**0**[/COLOR]
```
1.1 Gb swapped while only 560 Mb (of 2 Gb) is in real use. Moan. :<

This being linux I really shouldn't need to reinstall, but I'm very close to doing it anyway out of despair. I probably caused this myself somehow, but I don't know what it was I did.

---

### Post by NightwishFan on 2011-06-04
I can only think of a memory leak. Can you review what processes are using such huge amounts of RAM? (From the oom killer perhaps chromium?)

Edit: The disk cache would not use much swap and would be freed if applications need the ram. So it is not the cache causing the issue I am fairly sure.

---

### Post by Zorael on 2011-06-04
> **NightwishFan said:**
> I can only think of a memory leak. Can you review what processes are using such huge amounts of RAM? (From the oom killer perhaps chromium?)
```
Tasks: 146 total,   1 running, 138 sleeping,   0 stopped,   7 zombie
Cpu(s): 41.7%us,  5.5%sy,  0.0%ni, 49.9%id,  2.5%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   2051084k total,  1988536k used,    62548k free,     3104k buffers
Swap:  2152672k total,  1196556k used,   956116k free,  1369400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU [COLOR="Green"]**%MEM**[/COLOR]    TIME+  COMMAND                                              
12044 zorael    20   0  795m  86m  13m S    5  [COLOR="Green"]**4.3**[/COLOR]  25:26.13 firefox-trunk-b                                      
 3163 zorael    20   0  987m  81m 1700 S    1  [COLOR="Green"]**4.1**[/COLOR]  62:33.47 chromium-browse                                      
12085 zorael    10 -10  344m  73m 7768 S   75  [COLOR="Green"]**3.7**[/COLOR] 102:59.70 plugin-containe                                      
 8580 zorael    20   0  319m  55m 3512 S    1  [COLOR="Green"]**2.8**[/COLOR]   6:48.43 skype                                                
23532 root      20   0  227m  29m 3856 S    2  [COLOR="Green"]**1.5**[/COLOR] 153:54.15 Xorg                                                 
10619 zorael    20   0  271m  26m 4972 S    0  [COLOR="Green"]**1.3**[/COLOR]   1:42.75 plasma-desktop                                       

[...]

```
At no point does anything seem to soar in memory use; I just eventually hit the imaginary ceiling where my applications simply... aren't allowed any more. It's confusing.

> **NightwishFan said:**
> Edit: The disk cache would not use much swap and would be freed if applications need the ram. So it is not the cache causing the issue I am fairly sure.
No; having the disk cache in the disk swap would be pretty dumb. :3

What *seems* to be happening is that the kernel stops releasing the memory the disk cache uses, forcing applications into swap.
```
$ free
             total       used       free     shared    buffers     cached
Mem:          2003       1945         57          0          8       **1333**
-/+ buffers/cache:        602       1400
Swap:         2102       1179        923
```
Doesn't the *cached* field list disk cache use? If I pipe 3 to **/proc/sys/vm/drop_caches**, it only drops minutely.
```
zorael@lethe:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1945         57          0          0       [COLOR="Red"]**1334**[/COLOR]
-/+ buffers/cache:        610       1392
Swap:         2102       1184        917

zorael@lethe:~$ echo 3 | sudo tee /proc/sys/vm/drop_caches 
3

zorael@lethe:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1913         89          0          0       [COLOR="Red"]**1307**[/COLOR]
-/+ buffers/cache:        605       1397
Swap:         2102       1184        917
```

---

### Post by NightwishFan on 2011-06-04
That is a bit baffling.. Try:
```
sudo swapoff -a && sudo swapon -a
```

---

### Post by Zorael on 2011-06-04
> **NightwishFan said:**
> That is a bit baffling.. Try:
```
sudo swapoff -a && sudo swapon -a
```
If I do, the machine starts to thrash; resource contention makes it choke completely on the I/O. It continues indefinitely until I manage to kill the swapoff process via manual OOM execution. :<

```
[...]

[328897.140912] Out of memory: Kill process 12737 (swapoff) score 1000 or sacrifice child
[328897.140921] Killed process 12737 (swapoff) total-vm:4032kB, anon-rss:84kB, file-rss:72kB
```

It's as if it's trying to empty the swap by reading it into RAM, but the RAM is already "full" so it gets swapped again instead.

---

### Post by NightwishFan on 2011-06-04
This seems very odd. Perhaps create a new user, reboot, and see if this happens for the new user. If not, than it is some configuration issue in user space.

---

### Post by Zorael on 2011-06-04
This has persisted over several boots and across both the repo kernel and the 2.6.39 from the ppa, but I haven't yet tried a new user, no. I'll report back when I have more data.

Many thanks for the help.

---

### Post by Zorael on 2011-06-04
New user did not seem to help.
```
$ free
             total       used       free     shared    buffers     cached
Mem:          2003       1664        338          0          8       1016
-/+ buffers/cache:        **[COLOR="Red"]639[/COLOR]**       1363
Swap:         2102        **[COLOR="red"]226[/COLOR]**       1875
```
```
[ 9538.826147] Out of memory: Kill process 6622 (vlc) score 70 or sacrifice child
[ 9538.826158] Killed process 6622 (vlc) total-vm:466312kB, anon-rss:251264kB, file-rss:45652kB
```

---

### Post by NightwishFan on 2011-06-04
Well I personally see no reason for it to need so much RAM. In your shoes I would lean toward testing a live CD or reinstalling.

---

### Post by Zorael on 2011-06-07
After reinstalling;
```
$ free
             total       used       free     shared    buffers     cached
Mem:          **[COLOR="Green"]2003       1946[/COLOR]**         56          0          7        **[COLOR="DarkOrange"]912[/COLOR]**
-/+ buffers/cache:       **[COLOR="Red"]1027[/COLOR]**        **[COLOR="Red"]975[/COLOR]** (!!)
Swap:         2102       **[COLOR="Red"]1040[/COLOR]**       1061
```

Sob. :<

---

### Post by NightwishFan on 2011-06-07
I will do some digging. I will look up some specific commands to review memory management.

Edit, check out the folder /dev/shm and see how full it is.

edit edit: Try booting your system using less available ram to see how it behaves. Just append mem=800m to grub (while booting not in the grub config file).

Also you might have answered this but is this 32 or 64 bit?

---

### Post by Zorael on 2011-06-07
First of all, my eternal thanks.

The only files in /dev/shm are pulseaudio's shared files, which total some 8 Mb. I have two tmpfs mounts excluding /dev/shm; **/var/run** and **/var/lock**, but they only total 456 kb. And sorry, yes; this is a 32-bit installation. It's an old-ish Atom netbook upgraded to 2 gb RAM.

I'll try limiting the memory.

---

### Post by NightwishFan on 2011-06-07
Also, give me the output of vmstat; you can compare it to mine to see if anything sticks out as odd.
```
vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0     16 1424152  64844 913836    0    0    95    43  314  320  5  1 93  1
```

(64-bit Debian, bunch of apps running)

---

### Post by Zorael on 2011-06-07
After ~2h45m of uptime with mem=800m;
```
$ free; echo; vmstat
             total       used       free     shared    buffers     cached
Mem:        798668     765512      33156          0       1104     178436
-/+ buffers/cache:     585972     212696
Swap:      2152672     137852    2014820

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0 137852  33156   1104 178436    1    8   197    18  617  732 10  2 82  5
```
Applications wanted 706 Mb (572+134) out of 779 Mb available RAM, yet were only allowed 572 Mb and had to resort to swap for the remaining 134 Mb. Swappiness is at 1.

Does the vmstat output help at all? The figures don't look terribly different from yours, except my system numbers (in/cs) are twice yours.

I'll paste the contents of /proc/meminfo too, just incase;
```
$ cat /proc/meminfo 
MemTotal:         798668 kB
MemFree:           15884 kB
Buffers:            1588 kB
Cached:           182032 kB
SwapCached:        28636 kB
Active:           341196 kB
Inactive:         378708 kB
Active(anon):     310248 kB
Inactive(anon):   342092 kB
Active(file):      30948 kB
Inactive(file):    36616 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         798668 kB
LowFree:           15884 kB
SwapTotal:       2152672 kB
SwapFree:        2016100 kB
Dirty:                24 kB
Writeback:             0 kB
AnonPages:        518100 kB
Mapped:            50012 kB
Shmem:            116100 kB
Slab:              23164 kB
SReclaimable:       8196 kB
SUnreclaim:        14968 kB
KernelStack:        2440 kB
PageTables:         8996 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2552004 kB
Committed_AS:    2465732 kB
VmallocTotal:     212984 kB
VmallocUsed:       15592 kB
VmallocChunk:     196376 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      819200 kB
DirectMap4M:           0 kB
```
It seems sort of relevant, at least.

---

### Post by NightwishFan on 2011-06-07
I don't get it. It is like you said where it seems like its not dropping the disk cache right. :o

Does it even do this if you boot to single user mode (recovery mode, then a shell and then free -m) If its abusing swap even then you might want to file a bug.

---

### Post by Zorael on 2011-06-07
Hmm. How do I allocate memory that way from a terminal? It's easy in a desktop environment with my browser tabbing behavior.

I can compile some C snippet if you know any malloc() voodoo; my C-fu is not quite there yet, I'm afraid.

Finishing this tangent, I tried closing down Chromium (which accounts for most of my memory needs) and disabling swap. Then I reopened it and observed behavior with no swap present.
```
$ free -m; sudo swapoff -a; free -m
             total       used       free     shared    buffers     cached
Mem:           779        351        428          0          6        178
-/+ buffers/cache:        166        613
Swap:         2102        108       1993
[sudo] password for zorael: 
             total       used       free     shared    buffers     cached
Mem:           779        436        343          0          7        187
-/+ buffers/cache:        240        539
Swap:            0          0          0
```
You'd think it'd run out of memory and invoke the OOM killer when it restored all my tabs, but it's like it's still swapping.
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           779        771          7          0          0        156
-/+ buffers/cache:        614        164
Swap:            0          0          0
```
Opening new tabs starts a fury of disk reads and writes, and iotop sanely lists Chromium as doing non-buffered I/O work. But when reading/writing so, it also lists kswapd0 at 90%+ I/O wait. I'd have thought kswapd0 would be inactive now that there is no swap?

---

### Post by NightwishFan on 2011-06-07
I think kswapd handles a bit more paging than just to swap but I could be wrong.

---

