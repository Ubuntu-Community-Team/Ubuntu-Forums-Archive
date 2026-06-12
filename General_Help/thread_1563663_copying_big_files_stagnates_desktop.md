---
title: "copying big files stagnates desktop"
date: 2010-08-29
forum: General Help
---

### Post by ilna on 2010-08-29
Hi!

I use (up to date with proposed) Kubuntu lucid, but think the problem is independent on concrete desktop environment.

During copying big files (say, iso images) DE becames almost not responsive: commonly instant actions take seconds and seconds.

Are there some configuration tricks to (at least partly) cure the issue?

---

### Post by Vaphell on 2010-08-29
that would mean that your cpu load shoots through the roof
run top or htop to verify that
that shouldn't happen though, seems like there is some problem with dma

---

### Post by ilna on 2010-08-29
> **Vaphell said:**
> that would mean that your cpu load shoots through the roof
run top or htop to verify that
that shouldn't happen though, seems like there is some problem with dma
To be free from any DE surprises I have tried 'cp' under fluxbox. 'top' shows 'cp' eating 7-12% of a core. So, all time is spent under IO-waiting.

I have ordinary SATA HDD (1Tb WDC WD10EADS-00M2B0). 'hdparm' shows nothing sad:

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   7108 MB in  2.00 seconds = 3558.12 MB/sec
 Timing buffered disk reads:  290 MB in  3.00 seconds =  96.51 MB/sec

What do you mean saying about DMA problems? Where to dig in?

---

