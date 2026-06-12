---
title: "Can't get internal mic to work anymore"
date: 2009-12-14
forum: General Help
---

### Post by jbrown96 on 2009-12-14
I use Kubuntu, which uses Alsa. I was trying to make some screencasts a few weeks ago, and I was able to get my laptop mic working. It took me close to two hours to figure out all the channel settings. 
The problem is that I can't figure out the voodoo that I did last time. I've messed with what seems to be every possible combination of channels volues, but it still won't work. 
Does anyone have any ideas of settings?
Audio hardware
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I've attached two screenshots that show my alsa channels.

Thanks for the replies.

---

### Post by jbrown96 on 2009-12-14
Finally got it working! couldn't fix the problem using alsamixer, but I was able to get it working with kmix. It was some weird setting with the "capture" channel that I couldn't set in alsamixer.

---

