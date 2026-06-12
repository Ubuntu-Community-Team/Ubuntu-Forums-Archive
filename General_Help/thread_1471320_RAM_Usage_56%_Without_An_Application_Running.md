---
title: "RAM Usage 56% Without An Application Running"
date: 2010-05-03
forum: General Help
---

### Post by ProNux on 2010-05-03
As the thread states, I wonder why my RAM usage is about 56% without any application running.  It turns to 58% while opening Firefox (with only one Tab/Page opened) and typing this post.  Is there something wrong?

My hardware is described on my signature...

---

### Post by whoop on 2010-05-03
With the gnome desktop on ubuntu this can happen. It's quite bloated, lots of processes doing nothing useful at all.

---

### Post by Erik765 on 2010-05-03
If you open up system monitor and sort by RAM usage, what process(es) are actually using the RAM?

How much RAM do you have in your system total?

---

### Post by P4man on 2010-05-03
56% of 2 GB? That doesnt sound right at all. I think you are misreading some values using "free -m" in the cli. Post the results or open system monitor from system > administration > system monitor > resources.

Im pretty sure you are including cache memory in the used %.

---

### Post by WorMzy on 2010-05-03
Open System monitor (System -> Administration -> System Monitor) and click the Processes tab, now click View -> All Processes, then click on the Memory column twice. Does anything there looks suspicious? Here's mine for comparison:
[[IMG]http://www.ubuntu-pics.de/thumb/56054/system_monitor_095_9g2Qpt.png[/IMG]]("http://www.ubuntu-pics.de/bild/56054/system_monitor_095_9g2Qpt.png")

EDIT: My memory usage comes to 1GB, so perhaps this 56% is normal..

---

### Post by Mazin on 2010-05-03
> **whoop said:**
> With the gnome desktop on ubuntu this can happen. It's quite bloated, lots of processes doing nothing useful at all.
This is not an accurate description at all. 

 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155335&stc=1&d=1272911281[/IMG]
Notice that, on my computer, 15% is used by programs and 15% is used by cache.  Your computer SHOULD be using as much memory for cache as it can.

Open up System Monitor, go to Processes, and sort by Memory and let us know which processes are taking up too much memory.  I'm guessing that standard Gnome processes will not be at the top of your list.

---

### Post by whoop on 2010-05-03
> **Mazin said:**
> This is not an accurate description at all. 

 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155335&stc=1&d=1272911281[/IMG]
Notice that, on my computer, 15% is used by programs and 15% is used by cache.  Your computer SHOULD be using as much memory for cache as it can.

Open up System Monitor, go to Processes, and sort by Memory and let us know which processes are taking up too much memory.  I'm guessing that standard Gnome processes will not be at the top of your list.

Well I've noticed other distributions with gnome using much less memory than ubuntu.

---

### Post by ProNux on 2010-05-04
> **Erik765 said:**
> If you open up system monitor and sort by RAM usage, what process(es) are actually using the RAM?

How much RAM do you have in your system total?

Sorry for the late reply as it is already 1:00 AM last night, and same again now.

My total RAM is 2gb, swap partition also 2 GB

I was surprised now after my first boot today, my RAM usage is now only 36%, with only 1 tab of Firefox running.

I have opened many video streams last night and after closing them, my RAM was still up to 58% usage (never noticed though what was the actual RAM usage while I streamed the videos).

Is it possible that the free-up of RAM is slow after closing the applications?

Is there a command to manually free-up the RAM?

---

### Post by ProNux on 2010-05-04
> **P4man said:**
> 56% of 2 GB? That doesnt sound right at all. I think you are misreading some values using "free -m" in the cli. Post the results or open system monitor from system > administration > system monitor > resources.

Im pretty sure you are including cache memory in the used %.

Here is the "CURRENT" screenshot of my RAM usage Tofay.  I was surprised that my first boot now it only shows about 38% usage.  Last night I streamed many videos but after I closed them, the RAM usage was about 58%.

---

### Post by snowpine on 2010-05-04
> **ProNux said:**
> Sorry for the late reply as it is already 1:00 AM last night, and same again now.

My total RAM is 2gb, swap partition also 2 GB

I was surprised now after my first boot today, my RAM usage is now only 36%, with only 1 tab of Firefox running.

I have opened many video streams last night and after closing them, my RAM was still up to 58% usage (never noticed though what was the actual RAM usage while I streamed the videos).

Is it possible that the free-up of RAM is slow after closing the applications?

Is there a command to manually free-up the RAM?

The data stays cached in ram until something else needs it. Nothing to worry about. As you mention, rebooting makes the ram usage go back down.

---

### Post by ProNux on 2010-05-04
> **WorMzy said:**
> Open System monitor (System -> Administration -> System Monitor) and click the Processes tab, now click View -> All Processes, then click on the Memory column twice. Does anything there looks suspicious? Here's mine for comparison:
[[IMG]http://www.ubuntu-pics.de/thumb/56054/system_monitor_095_9g2Qpt.png[/IMG]]("http://www.ubuntu-pics.de/bild/56054/system_monitor_095_9g2Qpt.png")

EDIT: My memory usage comes to 1GB, so perhaps this 56% is normal..

Here's mine.  Unfortunately, (or fortunately)  my RAM usage today is a little lower than last night.  See my post above. The "Xorg" application/service takes the largest.  Is this normal?

---

### Post by DeMus on 2010-05-04
Why did you buy a computer with 2GB ram if you think it is strange when the system uses it? You should be happy it does so. Programs which you have used and closed down will remain in memory until some other program needs it. Then it will be released. That explains the higher ram usage. Not all is used but should you re-open a program it is very fast to open since it is in ram already.
Don't worry about it, the more ram your system is using the faster it will be because it needs to take less data from disk which is a whole lot slower.

---

### Post by ProNux on 2010-05-04
> **Mazin said:**
> This is not an accurate description at all. 

 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155335&stc=1&d=1272911281[/IMG]
Notice that, on my computer, 15% is used by programs and 15% is used by cache.  Your computer SHOULD be using as much memory for cache as it can.

Open up System Monitor, go to Processes, and sort by Memory and let us know which processes are taking up too much memory.  I'm guessing that standard Gnome processes will not be at the top of your list.

My RAM now is 45% but cache (Swap partition) is only 16%, big difference.

---

### Post by mk1w86 on 2010-05-04
Are you using 32 or 64bit Ubuntu?

The 64bit version (this applies to any OS as far as I know) generally uses more RAM but this is nothing to worry about, the percentages will seem quite high because you only have 2GB. ;)

---

### Post by jocko on 2010-05-04
> **ProNux said:**
> My RAM now is 45% but cache (Swap partition) is only 16%, big difference.
Cache has nothing to do with the swap partition. Cache is data that is kept in ram until it's either needed again or until something else needs the ram space.

---

### Post by ProNux on 2010-05-04
I am using 64-bit Lucid.

Thanks to all of you.  Great information...

---

### Post by mariorez on 2010-05-06
Hei ProNux... Did you see this Wiki about Memory Leak?
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)
> Recently in Lucid, a major memory leak was found in the X.org server  which causes the computer to get slower and slower over time

---

### Post by figosound on 2010-05-06
Hi, I'm experiencing about the same problem, see [http://ubuntuforums.org/showthread.php?t=1473131](http://ubuntuforums.org/showthread.php?t=1473131)
I have a system with 2G of ram, 256 MB used by sideport (shared); I have already checked the Infamous Memory Leak, but it affects only Intel and Free video drivers, but since I have tried free, non free, no compiz this is not the case. Any help?

---

### Post by ProNux on 2010-05-29
> **mariorez said:**
> Hei ProNux... Did you see this Wiki about Memory Leak?
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

Thanks bro, I haven't heard of this info.  I will read about this...

---

