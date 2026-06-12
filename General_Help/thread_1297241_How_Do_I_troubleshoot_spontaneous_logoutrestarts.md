---
title: "How Do I troubleshoot spontaneous logout/restarts?"
date: 2009-10-21
forum: General Help
---

### Post by kendoori on 2009-10-21
Am running 9.04 with 2.6.30-02063009 kernel. Also have GM965 chipset. In the last week after leaving my machine idle for a few hours, I will come back to my desk and the machine will be at the login screen. 

I'm likely to completely rebuild machine when 9.10 is released, but would love to understand what's happening that's causing this annoying behavior.

I'm pretty sure that this always happens when I have a VirtualBox session running as host for XP.

Not sure what logs to look in to isolate when this is happening. Any help is appreciated.

---

### Post by compiledkernel on 2009-10-21
Ive got a diag doc you should read through. I have to believe that something gets dumped to the logs at the time you perform the shutdown. 

[http://gwos.org/udsf/doku.php/hardware:diagnosis](http://gwos.org/udsf/doku.php/hardware:diagnosis)

Id say check syslog, then messages at the time you commit the action.

---

### Post by kendoori on 2009-10-21
Thanks for the suggestion. I don't think hardware is at issue here... but will explore that if I exhaust other avenues. As suggested, I looked in the syslog and discovered this: gdm_slave_xioerror_handler: Fatal X error

I then searched the forums and discovered this thread, which seems to describe my issue to the "T" [http://ubuntuforums.org/showthread.php?t=1152024&highlight=Fatal+X+error](http://ubuntuforums.org/showthread.php?t=1152024&highlight=Fatal+X+error)

This has got to do with Intel GM965 chipset, and the fact that I'm running compiz. What motivated me to update the kernel is I was randomly experiencing X issues where the display would crash and spit back this error: **Display Server has been shutdown 6 times in 90 seconds, **which I detailed here: [http://ubuntuforums.org/showthread.php?t=1285338](http://ubuntuforums.org/showthread.php?t=1285338) 

The new kernel has seemed to make the error go away, but introduced this new condition. I may update the kernel to 2.6.31 and see if that makes this go away, as I've done a trial run of the Karmic beta installed to a USB key and have not had a problem yet (need to do more testing).

---

