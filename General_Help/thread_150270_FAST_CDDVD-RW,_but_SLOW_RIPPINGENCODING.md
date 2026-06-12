---
title: "FAST CD/DVD-RW, but SLOW RIPPING/ENCODING"
date: 2006-03-25
forum: General Help
---

### Post by bom bom on 2006-03-25
Hello all,  I recently learned Linux from the first release of Ubuntu.  I recently upgraded after a harddrive crash and have the following issue:

I have a 48x CD/DVD RW installed, but only get 4x max speed when I rip and encode my music onto the Hard Drive.  

Systems Specs
1.5 GHZ P4 processor
256 MB RAM
Linux 2.6.12-10-386
NEC DVD RW model ND 3520A

Any help would be greatly appreciated!

Benji Burrell

---

### Post by bluevoodoo1 on 2006-03-25
I have a quick CD drive too and it only rips at 4x, my DMA is enabled too. Is your DMA enabled? Are you using sound-juicer to rip?

---

### Post by bom bom on 2006-03-25
DMA is enabled. Learned to do thatin the Ubuntu documentation.  Any other suggestions?

---

### Post by bom bom on 2006-03-25
Both in Sound Juicer and Grip, ripping and encoding is 4x max, 2.6 average.

---

### Post by bom bom on 2006-03-25
anybody there?

---

### Post by Barrakketh on 2006-03-25
I don't use Grip, but try lowering the paranoia level (or whatever it's called).  It uses the cdparanoia backend to rip with (last I checked), and the default should be to use full paranoia.  The upside to this is that your rips will be much better, especially if you have a scratched CD.  Also, if you're ripping/encoding in one pass (as opposed to ripping the tracks, then encode) it'll only rip as fast as your computer can encode.

---

### Post by bom bom on 2006-03-25
Thanks!  Adjusting the paranoia settings changes the rip and encode speeds dramatically!  I'll turn it off unless i'm ripping a scratched cd.

Could you recommend a better package for ripping and encoding?

---

### Post by Barrakketh on 2006-03-25
[QUOTE=bom bom]Thanks!  Adjusting the paranoia settings changes the rip and encode speeds dramatically!  I'll turn it off unless i'm ripping a scratched cd.

Could you recommend a better package for ripping and encoding?[/QUOTE]
Not really...I use cdparanoia from the command line along with cdrdao's "read-toc" command.  I rip my CDs as a single file and create a cue sheet for seeking through the tracks.  Sadly, the Rhythmbox developers have chosen not to support cue sheets, so I don't use it.

I'm a KDE user, and when I want to rip CDs the "normal way" I use K3B (KDE's CD burning application), which can also rip CDs.

I think Grip is the most popular application to rip CDs with, though I may be wrong >_>

---

### Post by bom bom on 2006-03-25
I have K3B also, but havent used it yet.  Thanks so much!

---

