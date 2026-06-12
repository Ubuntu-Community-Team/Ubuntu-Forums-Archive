---
title: "Strange display hiccups with 10.04 (64-bit)"
date: 2011-10-06
forum: General Help
---

### Post by Doctor Memory on 2011-10-06
My display will hang for 5-20 seconds if I don't move the mouse or type anything.  All I have to do to get it moving again is hit the shift key, but it's annoying.  It happens intermittently, but at least every five minutes.  No messages in the logs or .xsession-errors (except I'm getting a constant "(gnome-settings-daemon): WARNING: **: connection failed, reconnecting", what's up with *that*?).  I've tried running with effects turned off, but that didn't help.

System: Gigabyte GA-MA785G1-US2H motherboard
     CPU: AMD Phenom 9850
  Video: on-board Radeon HD 4200 chipset
Memory: 8G DDR2-800

I see from Xorg.0.log that I seem to be running the proprietary ATI driver.  Any suggestions for things to try or stuff to check out?  Like I said, this isn't a "hang" or a "freeze" that would suggest overflowing the list buffer or a driver failure, it's more like a GC pause or something (except I can break out of it by pressing shift).  Moving the mouse doesn't fix it, but if I do move the mouse while it's hung, the pointer position gets updated when the display comes back.

Any ideas?

---

