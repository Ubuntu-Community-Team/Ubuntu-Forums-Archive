---
title: "Won't boot - &quot;error 24&quot;"
date: 2009-11-13
forum: General Help
---

### Post by djuke04 on 2009-11-13
Here's the context:

I have 2 hard drives - 1 solid state with Ubuntu 9.04 installed, and 1 hard disk I use for media and network sharing - plus I have to fresh install Ubuntu so often that I got tired of backing up my stuff on another hard drive, so I got the SSD to make it all quick and easy.

Anyway, I started playing a tv show in movie player tonight - sons of anarchy, a real meaty season 1 finale (I digress...) - and walk away thru the intro to get some grub (er, food...) and come back to find the system frozen in the middle of the first few moments of the show, and completely unresponsive.  I give it a few minutes as I eat thru some cheese and apples, and then have to force a shutdown via the power button for ten seconds.  

When I go to restart, it says:

grub loading...
error 24

so I popped in a live Kubuntu cd - failed - froze mid-boot three times.  Switched to Ubuntu live disc and it went up alright.  I searched around here a bunch, and found some older, less pertinent threads that lead me to try some things.

I cannot mount the main drive, the ssd that is.  When I try to open that drive in the live session it says:

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error 
In some cases useful info is found in syslog -try dmesg tail or so  

(that's as best as I could copy it)

So here I sit, confused and frustrated, watching Sons of Anarchy on my windows laptop with terrible resolution and audio to boot.  

What else could I try? Where do I go from here? I'm a psuedo-noob - but not stupid - so please explain things that seem beyond basic.


THANKS IN ADVANCE FOR HELP THANKS THANKS THANKS!!!

---

### Post by djuke04 on 2009-11-13
Also I should add that it's frozen during video playback before, and I just had to skip around in the video to fix it, as long as I did it quickly after the freeze rather than leaving it frozen for a while.  
 
 It's stopping now at Grub loading stage 1.5 also if that's helpful.  Thanks!

---

### Post by djuke04 on 2009-11-15
Not that this is particularly helpful information, but if anybody is interested in this, it's lead absolutely nowhere. 

I tried a wide variety of things to restore the GRUB and the filesystem - somewhat blindly since I'm not a professional here - and in the end I thought the hard drive was broken.  I had to put it into a windows machine and format it before it would be recognized again by a live session disk utility even.  So now I'm rebuilt, with 9.10, getting excited for the next LTS to come out.  

It seems like in GRUB stage 1.5, when you get an error 24... it's all over.  Rebuild!

---

