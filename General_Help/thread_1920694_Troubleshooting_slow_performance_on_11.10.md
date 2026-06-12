---
title: "Troubleshooting slow performance on 11.10"
date: 2012-02-05
forum: General Help
---

### Post by ghetto2ivy on 2012-02-05
I've been an ubuntu user since Dapper, and have always tried to keep my systems in tip top shape and hardware up to date. However, I have run into an issue with my latest build that is leaving me scratching my head. 

My Machine Specs:
6 core phenom 2.8ghz
16gb ram
2 x 1.5 tb hard drives (3 mirrored partitions each)
nvidia 8500gt with 512mb ram video card
Biostar MB 
11.10 64bit

Starting with my fresh install of 11.10:

[LIST]
[*]Nautilus is unbearably slow opening some of my partitions. 
[*]Slow Copy operations to Usb thumbdrive. Reaches the buffer, then drops to kb /second copy rates.
[*]Even in gedit, the typing gets occsionally buffered, and doesn't show up immediately on screen
[*]phpunit tests that take 17 seconds on my MacBook air (1.6ghz core2duo) take 4 minutes on this machine.
[/LIST]

A folder with 1000 items takes 4-5 seconds to load. Same folder in 10.04 was instant (with intel q6600 proc, and less ram). I never saw the dreaded "loading" message.


I know the video card is older, and unity3d slows things down, but really it should be adequate.

What I've done so far to troubleshoot:
[LIST]
[*]checked /proc/cpuinfo to make sure all the cores are found.
[*]Ramtest
[*]Benchmarked my hard drives (each actually came to decent 120+mb/sec reads times with 9.3ms access times)
[*]Watched my system with top to check the cpu and ram utilization (typically 6-8gigs, no swap)
[*]Run my system with all swap off (swapoff -a)
[/LIST]

I haven't played with my fstab settings, I suspect the bottleneck is really the hard drive, but I haven't found any proo of that as the benchmarks don't indicate they should be the bottleneck.

So Community, any suggestions?

---

