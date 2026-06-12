---
title: "Flash hard crashes machine, 10.04"
date: 2010-09-08
forum: General Help
---

### Post by newfuturevintage on 2010-09-08
Hi-
First post here.

I've built an Ubuntu Lucid Lynx box out of some spare parts and am really enjoying it, save for Flash seems to hard crash the system (full shut down, no video, nothing, just black).  Either in Chromium or Firefox.  This is a new install to a freshly formatted HDD, and I've swapped out mobos/ processors/ power supplies/ memory sticks.

The system appears completely stable if I do not have Flash installed.

In the order done:
I tried installing Flash from the ubuntu software center initially.  After getting a few crashes, I reinstalled the OS freshly.  
I tried reinstalling from the software center.  Still crashing.  Removed via software center, system stable.
I tried using Carlee's Adobe Tools ([http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)), which did not successfully install Flash, in spite of reporting having done so.
and 
Lovinglinux's Flash-Aid, which did successfully install Flash, but I'm back to the same system instability.

All permutations tried have the same issue: I can view Flash files for an indeterminate amount of time: sometimes a couple hours, sometimes a few minutes, but the system eventually hard crashes.  Seems to happen faster if Yahoo mail is open, and/or if youtube is involved, but they need not be involved for the crash to occur.

Any suggestions would be welcome!

---

### Post by lovinglinux on 2010-09-08
> **newfuturevintage said:**
> All permutations tried have the same issue: I can view Flash files for an indeterminate amount of time: sometimes a couple hours, sometimes a few minutes, but the system eventually hard crashes.  Seems to happen faster if Yahoo mail is open, and/or if youtube is involved, but they need not be involved for the crash to occur.

It could be a CPU temperature issue. Flash uses too much CPU, so after a while, if your CPU is not properly ventilated, it could cause video performance degradation and even crashes.

---

### Post by newfuturevintage on 2010-09-09
> **lovinglinux said:**
> It could be a CPU temperature issue. Flash uses too much CPU, so after a while, if your CPU is not properly ventilated, it could cause video performance degradation and even crashes.

That's certainly a possibility, and it is a total system crash, not just a single application dying.

I did blast the CPU heatsink with air, and confirm CPU, case, and power supply fans all are operational.  In this same hardware config, I had no issues under XP with anything to do with overheating.

do you have a recommendation for a CPU temp monitor? Would love to see if there's a correlation.

Thanks!

---

### Post by kerry_s on 2010-09-09
i was just getting crashes to, it was pulse causing it.
what i did was uninstall "gstreamer0.10-pulseaudio"
then
i went in to "gstreamer-properties"(multimedia system selector, if you have it tuned on in the menu) an changed them to alsa.

no more crashes.

i also removed & reinstalled flash just to be sure.

---

### Post by newfuturevintage on 2010-09-09
> **kerry_s said:**
> i was just getting crashes to, it was pulse causing it.
what i did was uninstall "gstreamer0.10-pulseaudio"
then
i went in to "gstreamer-properties"(multimedia system selector, if you have it tuned on in the menu) an changed them to alsa.

no more crashes.

i also removed & reinstalled flash just to be sure.


I think this may well be the issue.  I removed gstreamer0.10-pulseaudio. and switched to alsa.  Which immediately crashed the system.  Upon rebooting, I reinstalled gstreamer0.10-puleaudio so I could mark it for a complete removal, removed it, and then changed to alsa as per your screenshot.  
I then reinstalled flash, and attempted to crash the machine by launching a lot of applications and a lot of tabs in firefox, making sure to keep youtube videos playing.  It was appearing stable for a couple hours.

I eventually did crash the machine, however.  

As the machine spat out its last dying gasp, there was a brief bit of text on screen, and the word pulseaudio was in it.  Unfortunately it wasn't up long enough to read before the crash was complete.

any further ideas I can try?

Thanks!

---

### Post by newfuturevintage on 2010-09-09
a bit of digging in the log viewer under kern.log yields from the time of the crash:

> Sep  9 11:56:04 sara-desktop kernel: [  305.060019] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  9 11:56:04 sara-desktop kernel: [  305.060032] render error detected, EIR: 0x00000000
Sep  9 11:56:04 sara-desktop kernel: [  305.061076] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 28955 at 28952)
Sep  9 11:56:06 sara-desktop kernel: [  306.976017] [drm:i915_gem_idle] *ERROR* hardware wedged
Sep  9 11:56:08 sara-desktop kernel: [  308.819342] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
this is repeated a few times until I rebooted the machine

---

### Post by kerry_s on 2010-09-09
do you got compiz turned on? if so switch to none.
compiz don't play nice with intel. use the metacity composite if you need for docks.

i just did a fresh install 30min, looks like just removing the gstreamer pulseaudio is enough on mine.

---

### Post by newfuturevintage on 2010-09-10
> **kerry_s said:**
> do you got compiz turned on? if so switch to none.
compiz don't play nice with intel. use the metacity composite if you need for docks.

i just did a fresh install 30min, looks like just removing the gstreamer pulseaudio is enough on mine.


Compiz was not enabled.  Metacity I have not enabled.

I ended up doing a fresh install (messed up grub chasing down the intel i915 issue, and couldn't get it back to working order).  

Next question: is it the opinion of the hive mind that this issue is a gstreamer.pulseaudio issue, or an intel i915 issue?  I'm beginning to suspect that flash might not be the root issue, but rather just the straw that breaks the camel's back.

---

### Post by lovinglinux on 2010-09-10
> **newfuturevintage said:**
> Compiz was not enabled.  Metacity I have not enabled.

I ended up doing a fresh install (messed up grub chasing down the intel i915 issue, and couldn't get it back to working order).  

Next question: is it the opinion of the hive mind that this issue is a gstreamer.pulseaudio issue, or an intel i915 issue?  I'm beginning to suspect that flash might not be the root issue, but rather just the straw that breaks the camel's back.

If you remove pulseaudio and don't install any other sound server, then flash uses a lot less CPU. Obviously that in this case, there is no sound. I have noticed that when trying to replace pulseaudio, but unfortunately, I wasn't able to configure another sound server properly.

---

### Post by newfuturevintage on 2010-09-10
Thanks.

I'm beginning to suspect this issue is the i915 issue more than anything else.  I've applied the fix suggested here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511)
and have my fingers crossed.

---

### Post by newfuturevintage on 2010-09-10
seems more stable.

Firefox is now catching Flash crashes, which didn't happen before.  Was able to run for 3 or 4 hours of moderate use prior to crashing.  This time the pulseaudio was again mentioned in the dying gasp, so I've uninstalled gstreamer0.10-pulseaudio again, and will continue testing.

---

### Post by newfuturevintage on 2010-09-14
So I've done quite a bit more research on this, and it appears it indeed may be an issue with the intel integrated video chip my system is using, which is an intel 82845G.  Compiz-check reported it as blacklisted hardware for Compiz, and I unearthed a lot of threads detailing very similar problems to what I am experiencing.
The crux of that seems to be moving to the VESA driver in lieu of the intel default.
So I've done that, and will continue testing.
Thanks for all the help.  Will update the thread with the results in a couple days.

---

### Post by newfuturevintage on 2010-09-16
Using the VESA driver seems to fix the issue, at least so far, no crashes.  I used the machine fairly heavily yesterday for 5 or 6 hours, file copying, playing mp3s, watching flash videos.  Left it last night playing mp3s overnight, and it was stable when I got to it 18 hours later.  

The only remaining issue I've got is since moving to VESA from the intel driver, I get a warning on bootup that:

(EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) no devices detected.

Strangely to my n00b self, the above leads me to believe VESA has not loaded.
however, compiz-check reports:
> 
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLXI think I'm at a place where I'm good with the system, less the  error.  I'd like to know how to make that go away.  Any thoughts?

---

### Post by newfuturevintage on 2010-09-16
helps to use the search function, doesn't it?  :rolleyes:

solved via:
[http://ubuntuforums.org/showthread.php?t=149706](http://ubuntuforums.org/showthread.php?t=149706)

going to keep this open a breath longer to make sure we're good, then I'll mark it solved.

thanks for the help all!

---

### Post by newfuturevintage on 2010-09-21
Sticking a fork in this one.  Moving over to VESA from the intel drivers has made this system stable.  

Thanks for the help.

---

