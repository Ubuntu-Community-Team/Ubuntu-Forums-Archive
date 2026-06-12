---
title: "USB transfers stop/start in 10.04"
date: 2010-05-30
forum: General Help
---

### Post by ubnewbie2 on 2010-05-30
When copying files to USB drives, the file progress bar moves it 'bursts', sometimes doing nothing for long periods, then moving forward quickly and stopping again.

It's almost like it is showing the transfer to the cache, not the transfer to the actual drive.

---

### Post by plutoniumpenguin on 2010-05-30
I noticed that as well.  In my case, say when I'm transferring a single 2GB file to the USB drive, the progress bar will reach very close to the end in about maybe half a minute, but then it will just stay there for maybe 2 - 3 minutes.  During this period of stagnation, the LED on the USB drive is on and the drive itself (a little pen-drive) feels warm to the touch, which lends support to your theory.

---

### Post by ubnewbie2 on 2010-05-30
Yes, one of the longest waits was right at the end of a copy of the 10.04 iso that I tried to write to a USB key.

---

### Post by andytof47 on 2010-05-30
yeah shiny and new chocka block full of your favorite bugs it's awesome.

From what I have read it has to do with the kernel and SATA / USB 

I played with my BIOS settings and turned of my wireless ATH5k (although madwifi also sucks now) 

three choices - 1)get an upstream kernel and pray  they have developed it enough to iron out the bugs ( i am yet to try this)

2) tweak BIOS and also check ur power management option I disabled mine, cause on resume it was glitchy as all heck.

3) Or use a boot CD like 8.04 (yes the that's right the speed increase is discgraceful, considering we are using the "latest and greatest or just switch to OpenSuSe:) )

It's a well known bug that I experienced on my desktop with 9.10 (same hardware)

---

### Post by ubnewbie2 on 2010-05-30
> **andytof47 said:**
> 
 1)get an upstream kernel and pray  they have developed it enough to iron out the bugs ( i am yet to try this)


So it's a problem in the kernel?  

Not that that makes it any easier for me to fix :(   I'll just have to wait for the fix to trickle through then I guess - not good to hear it's been there since 9.10 (which I skipped).

---

### Post by andytof47 on 2010-05-31
from the sounds of it yes, and there are plenty of bug reports filed about this.

anyhow apart from the obvious disappointment and the Microsoft attitude (it's not working yet but lets get it out there anyway) I found this and it's pretty comprehensive. To Canonicals credit at least they have the link in their kernel howto docs

here's the link.

[http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/)

lets hope they don't release another Vista like operating system, although I hear rumors that they plan an early release for their next LTS OH NO!!!! Lord help us all

hope the link helps

---

