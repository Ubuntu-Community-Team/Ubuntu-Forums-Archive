---
title: "Turn DMA on without messing up automount?"
date: 2006-02-11
forum: General Help
---

### Post by earth_walker on 2006-02-11
So I've been feeling all smug and happy about how pleasureable it is to have Ubuntu on my laptop instead of windows.

That is, until last night. A friend came over and started trying to play a series of mixed media cds and dvds on it, and the automount got totally confused - instead of unmounting the cd/dvd/cdr and mounting the next one, it would just keep adding new mount points to the desktop, and refused to recognise some of them, and certainly didn't autoplay things consistently.

A little deflated (I had just been giving a pro-open source speech) I did some reading today around the forum, and I realised that it's because DMA was turned on for the drive, which seems to cause confusion in the automount feature. Sure enough, when I turned DMA off, automounting works like a charm, no matter how often I change media types or order.

Great. However, now DMA is off and dvd playback is choppy.

So hours of reading later, I find many entries telling people how to turn DMA on to get rid of DVD choppiness, and then entries telling people to turn it off to fix automounting, but no clues as to how to get DMA on AND automounting working.

Can anyone help with this? 

I have an Acer Aspire 1692 WLMI (DDR2 version) laptop. 
Ubuntu Breezy, a pretty fresh install, DMA originally activated using Automatix.
Matshitauj-845D DVD-RW/CD-RW dual layer drive

---

### Post by PaulMellors on 2006-02-11
auto mount works for me even with dma on, i assume youve turned on DMA by editing the /etc/hdparm.conf file?

if not edit it and then add to the bottom of the file

/dev/hdc {
              dma = on
              }

change the hdc to match your cdrom drive reboot and see what happens!

---

### Post by bluevoodoo1 on 2006-02-11
[QUOTE=earth_walker]So I've been feeling all smug and happy about how pleasureable it is to have Ubuntu on my laptop instead of windows.

That is, until last night. A friend came over and started trying to play a series of mixed media cds and dvds on it, and the automount got totally confused - instead of unmounting the cd/dvd/cdr and mounting the next one, it would just keep adding new mount points to the desktop, and refused to recognise some of them, and certainly didn't autoplay things consistently.

A little deflated (I had just been giving a pro-open source speech) I did some reading today around the forum, and I realised that it's because DMA was turned on for the drive, which seems to cause confusion in the automount feature. Sure enough, when I turned DMA off, automounting works like a charm, no matter how often I change media types or order.

Great. However, now DMA is off and dvd playback is choppy.

So hours of reading later, I find many entries telling people how to turn DMA on to get rid of DVD choppiness, and then entries telling people to turn it off to fix automounting, but no clues as to how to get DMA on AND automounting working.

Can anyone help with this? 

I have an Acer Aspire 1692 WLMI (DDR2 version) laptop. 
Ubuntu Breezy, a pretty fresh install, DMA originally activated using Automatix.
Matshitauj-845D DVD-RW/CD-RW dual layer drive[/QUOTE]

I'm been having the exact same problem... 
[http://ubuntuforums.org/showthread.php?t=117772](http://ubuntuforums.org/showthread.php?t=117772)

I have an ASUS DVD-RW/CD-RW and the same things happen, except DMA won't stay on after I open/close the drive. 

For me, I assume it's hardware related, so I've given up on it for now.

---

### Post by dcstar on 2006-02-11
[QUOTE=earth_walker]So I've been feeling all smug and happy about how pleasureable it is to have Ubuntu on my laptop instead of windows.
......
Great. However, now DMA is off and dvd playback is choppy.

So hours of reading later, I find many entries telling people how to turn DMA on to get rid of DVD choppiness, and then entries telling people to turn it off to fix automounting, but no clues as to how to get DMA on AND automounting working.
......[/QUOTE]
There are various DMA modes you can specifically set, it is possible that the default (maximum) DMA mode is just too quick for Ubuntu.

You may want to experiment with manually setting the various DMA modes to see if you can (hopefully) find one that solves both you problems, then hard-code it in your hdparm.conf file.

---

### Post by bluevoodoo1 on 2006-02-11
[QUOTE=dcstar]... it is possible that the default (maximum) DMA mode is just too quick for Ubuntu.[/QUOTE]

Thank you for that tip.

---

### Post by earth_walker on 2006-02-12
Thanks, dcstar. I will play with dma settings when I next get a chance, and see if that helps.

---

