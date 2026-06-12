---
title: "Brooktree Corporation Bt878 TVCard Problem"
date: 2012-07-06
forum: General Help
---

### Post by Wagon21 on 2012-07-06
Can anyone help me out with my TVCard?

I have a Brooktree Corporation Bt878 TVCard and I looked in another thread about how to go about setting it up but when I run tvtime-scanner I get..

No existing PAL station list "Custom".
videoinput: Can't get tuner info: Inappropriate ioctl for device
videoinput: Can't get tuner info: Inappropriate ioctl for device

    No tuner found on input 2.  If you have a tuner, please
    select a different input using --input=<num>

ls /dev/video* shows

/dev/video0  /dev/video1

So I am kind of confused.. Where do I go from here to change the --input on the tvtime tunner? I've tried using --input=0 && --input=1 to no avail and am now left wondering what I am doing wrong. (besides breathing)

----Edit---

Scrap that - I desided after much grumbling under my breath to remove the Card, I have a KWorld VS-DVBt 355U (USB) Digital TV Dongle, a WinTV Hauppauge b535 and this Pinnacle Systems Brooktree bt878 - in hindsight three digital TV Cards that just refuse to work.

I contemplated cheating and using ndiswrapper with this video capture driver [http://btwincap.sourceforge.net/download.html](http://btwincap.sourceforge.net/download.html) until my setup then informed me that it couldnt load ndiswrapper modules into the kernel so that got RM'd too. Seems like going upstream to kernel 3.2.0 is not a good idea if you plan on watching television! (although maybe still possible in virtualbox with Windows XP!) however upon reflection I have reached the conclusion that the next time I buy a TV card it had bloody well better say 100% compatible with Linux on the Box... Damned device driver vendors and their cheaply made in China proprietary hardware! grr!

:lolflag:

---

