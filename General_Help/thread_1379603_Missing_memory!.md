---
title: "Missing memory!"
date: 2010-01-12
forum: General Help
---

### Post by OliW on 2010-01-12
**Before you say "OH IT'S THE CACHE", please, *please* read what I'm about to write before you do.**

I have 6 gigs of ram. Conky, System Monitor, htop and free all say I'm using 41% of my ram before cache/buffer.... But applications running are not using that much.

Here's free's output:

```
oli@bert:/tmp$ free -m
             total       used       free     shared    buffers     cached
Mem:          5975       4368       1606          0        164       1749
-/+ buffers/cache:       2455       3520
Swap:         1498        220       1278
```

You can do the maths (used-buffer-cached)/total*100 and you'll end up close to 41%.

This command adds up the memory percentage usage for all running processes:
```
ps aux | awk '{sum +=$4}; END {print sum}'
```

It reports 23.5%, some 17.5% below the figure provided by everything else.


**Where is that 17.5%?** It's not in cache, because my figures already account for cache. What else is RAM used for? How can I monitor it?

I should note that these values are after 8 days of uptime. Missing memory grows with time. After two weeks I start to run out of free memory completely even if I kill everything. It's really bad leakage.


On another, not wholly unrelated note, I have 3x 2048MB sticks of ram  (6144MB total) but they're showing (in free) as 5975MB! I've lost 2.8% of hard RAM before I even boot up. Any ideas? This is a desktop with a dedicated video card so I don't think it's being used as shared vram.

---

### Post by warfacegod on 2010-01-12
Concerning the last part, what does your BIOS say your RAM is?

---

### Post by john newbuntu on 2010-01-12
The free, conky, sysmon, htop etc clearly appear to show the right sizes.  However, I get the feeling that adding a column from ps is not the right way of knowing the memory used by processes.  These values (percentages) get rounded to a single decimal and could be way off when added.

The more proper way to do it would be to get the resident size or the virtual size of all processes running and then determine the fraction of the total memory available, which is exactly what the above tools do.

The memory growth that you are experiencing appears to be a memory leak.  You may have to monitor a few suspect process periodically (perhaps via a script) to spot the culprit. There may also be tools available to do this.

---

### Post by warfacegod on 2010-01-12
I believe some of the new ATi drivers are giving some folk similar grief.

---

### Post by OliW on 2010-01-13
> **john newbuntu said:**
> The more proper way to do it would be to get the resident size or the virtual size of all processes running and then determine the fraction of the total memory available, which is exactly what the above tools do.

```
ps aux | awk '{sum +=$6}; END {print sum}'
Resident total = 1894500
Virt total = 19235664 (19gigs - crazy)
Current used (according to free) = 3683252
```

While the percentages aren't that accurate, we're only dealing with 100-odd processes, each with a maximum +-0.05% variance from its real value. At most that's just 5% total and it's far more likely there's as much rounding down as there is up.


> **john newbuntu said:**
> The memory growth that you are experiencing appears to be a memory leak.  You may have to monitor a few suspect process periodically (perhaps via a script) to spot the culprit. There may also be tools available to do this.

My experience of memory leaks is the processes own RAM usage goes up (which *is* easily noticeable), not it mystically deporting RAM to the middle of nowhere where nobody can see or use it until reboot.


@warfacegod - I'll reboot now to find out and I'm using nvidia drivers.

---

### Post by mcduck on 2010-01-13
> **OliW said:**
> 

On another, not wholly unrelated note, I have 3x 2048MB sticks of ram  (6144MB total) but they're showing (in free) as 5975MB! I've lost 2.8% of hard RAM before I even boot up. Any ideas? This is a desktop with a dedicated video card so I don't think it's being used as shared vram.
When the system boots, the kernel is loaded into RAM. Since the part of your memory can't obviously be used for anything else it's not calculated into the total memory.

---

### Post by OliW on 2010-01-13
> **mcduck said:**
> When the system boots, the kernel is loaded into RAM. Since the part of your memory can't obviously be used for anything else it's not calculated into the total memory.

BIOS shows 6144 (what it should be). Free shows 5975. A deficit of 169megs.

Seems like a lot of memory for the kernel to nab.

---

### Post by john newbuntu on 2010-01-13
Have you monitored any parameters of /proc/meminfo and see if you find a value increasing such as Cached, Inact-dirty and Inact-clean.  I must admit I am not familiar with all of them, but perhaps the kernel for some reason is keeping the clean data structures around.
Does running a sync command from time to time help?

---

### Post by OliW on 2010-01-13
> **john newbuntu said:**
> Have you monitored any parameters of /proc/meminfo and see if you find a value increasing such as Cached, Inact-dirty and Inact-clean.  I must admit I am not familiar with all of them, but perhaps the kernel for some reason is keeping the clean data structures around.
Does running a sync command from time to time help?

No I hadn't and I admit I have no idea what I'm looking at:

```
oli@bert:/tmp$ cat /proc/meminfo
MemTotal:        6118616 kB
MemFree:         1501416 kB
Buffers:          279508 kB
Cached:          1301536 kB
SwapCached:        32916 kB
Active:          1864752 kB
Inactive:        1338676 kB
Active(anon):    1383308 kB
Inactive(anon):   253436 kB
Active(file):     481444 kB
Inactive(file):  1085240 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:       1534168 kB
SwapFree:        1309680 kB
Dirty:               340 kB
Writeback:             0 kB
AnonPages:       1601972 kB
Mapped:           140284 kB
Slab:             158100 kB
SReclaimable:     107648 kB
SUnreclaim:        50452 kB
PageTables:        34004 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     4593476 kB
Committed_AS:    2903488 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      329148 kB
VmallocChunk:   34359400955 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     4941312 kB
DirectMap2M:     1341440 kB
```

Memtotal appears to be more than other figures (5.975gigs of 6). Very odd.

---

### Post by mcduck on 2010-01-13
Actually both "free -m" and /proc/meminfo give you exactly the same amount of total RAM.

6118616kB = 5975MB = 5,83GB.

Nothing strange here, really. The kernel can easily take much more RAM than you'd think, considering that the the kernel files on your hard drive are in compressed format, but must of course be uncompressed to RAM when running the OS. And the kernel itself isn't really that small either in desktop distributions like Ubuntu which try to support most of the hardware out-of-the-box instead of you compiling your own kernel to exactly fit the hardware you use. Also note that many of the system directories don't realy exist in your hard drive but only in RAM.

---

### Post by OliW on 2010-01-13
> **mcduck said:**
> Nothing strange here, really. Sure. Makes sense. Thank you.

Now... What about this growing difference between free and application usage? The figures in the first post all used what free was showing as total ram (ie after the kernel stealing some) so still stand.

---

### Post by trifthen on 2010-01-13
Hey, before getting to far into this, check to make sure it isn't [Bug 501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715) first. I too [noticed memory issues](http://ubuntuforums.org/showthread.php?t=1379275) that weren't reported by top or ps. Turns out ureadahead was borked somehow and kept holding 500+MB of my memory.

Rebooting twice in a row without logging in fixed it for me, but who knows if it'll return if I reboot again. You might want to check what removing ureadahead does for you.

The problem you're going to run into while using this forum is that many here assume you're a raw beginner, even when you clearly are not, judging on your use of an embedded awk command. Ubuntu *has a memory issue* currently, but since it only seems to be evident if you reboot after doing a package upgrade (and maybe only those that affect the kernel or ureadahead in some way), and goes away once you reboot *twice* afterwards, not enough people have noticed it.

There may be a different issue of course, but the one I encountered was elusive enough.

---

