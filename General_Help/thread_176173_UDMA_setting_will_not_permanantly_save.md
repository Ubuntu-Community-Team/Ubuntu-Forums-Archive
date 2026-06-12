---
title: "UDMA setting will not permanantly save"
date: 2006-05-14
forum: General Help
---

### Post by mcpish on 2006-05-14
I'm trying to enable the UDMA mode on my DVD-ROM drive according to the wiki:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

It enables and seems to work, but it won't stay that way.  Whenever I switch CDs or DVDs on my DVD-ROM drive UDMA turns off according to the "sudo hdparm /dev/hdc" command, or when I reboot despite following the directions in the wiki.  Any advice?

---

### Post by bluevoodoo1 on 2006-05-14
I had an annoying problem like thatas , here's the thread if you see any ideas from it...
[http://ubuntuforums.org/showthread.php?t=117772](http://ubuntuforums.org/showthread.php?t=117772)

To sum it up, I could not have autoplay work with I added anything regarding DMA to hdparm.conf .... and DMA would not stay on if I ejected a disc--- but although it was *said* to be on, videos were still choppy.

After 3 months (!!) and 2 burners later I *finally* realized that it was the hardware rather than software. 

So if you have tried *everything* with the DMA wiki, perhaps you could try some hardware rearranging? My solution, found at the end of that thread, was actually looking up my barebone and its relationship to DMA on google. Changing it to slave, plugging in to the *other* IDE input and changing its name in the fstab fixed it.

---

