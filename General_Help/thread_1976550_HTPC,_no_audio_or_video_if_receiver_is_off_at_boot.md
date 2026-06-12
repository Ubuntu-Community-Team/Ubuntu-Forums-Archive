---
title: "HTPC, no audio or video if receiver is off at boot"
date: 2012-05-08
forum: General Help
---

### Post by Mega_Mike on 2012-05-08
I have Ubuntu setup as a HTPC over HDMI into a receiver.  If the receiver is off when I boot the HTPC, there is no audio or video.  If the reciever is on at boot, then everything is good.

Is there any fix for this besides leaving the receiver on all the time?

---

### Post by papibe on 2012-05-08
Hi Mega_Mike.

I would try to force your computer to believe it is connected to the monitor (or HDTV). To accomplish that you need to get your resolutions and timings of your monitor (EDID), save it on a file, and then configure your card to read it.

Take a look at post #4 of this [thread]("http://ubuntuforums.org/showthread.php?t=1936293&highlight=customEDID") for the specific instructions.

I hope that helps, and tell us if you need more help with that.
Regards.

---

