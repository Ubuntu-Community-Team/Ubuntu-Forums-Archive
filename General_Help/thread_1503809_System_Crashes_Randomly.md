---
title: "System Crashes Randomly"
date: 2010-06-07
forum: General Help
---

### Post by The_Grudge on 2010-06-07
I have an old PC in my basement that I decided to load Ubuntu onto a few months ago. I ran version 9 for a while and then recently upgraded to 10.04.
 
Unfortunately, I've been having issues with intermittent system crashes using both versions. Sometimes the computer will work fine for hours and other times it will crash 20 seconds after startup. I'll be able to provide much more information tonight when I get home but for now I wanted to plant the seed in the forum and see if anyone has any ideas.
 
The computer will be working fine and then all of a sudden the screen will go black and then start blinking, switching between a blank screen and a blank screen with a bunch of tiny white squares/lines. When I restart, things seem okay again. 
 
Like I said, when I get home tonight I'll post the model of my PC (it's an old HP Pavillion) and any other details I can find. Thanks.

---

### Post by The_Grudge on 2010-06-07
Okay, so the computer I'm using is an HP Pavillion a300n ([http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00039169](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00039169)).  I'll try and post a screenshot of my blinking screen. Any input is  appreciated.:P

---

### Post by _khAttAm_ on 2010-06-07
Seems like same old Intel 945/965 graphics problem.. Do you get freezes with Compiz disabled/removed?

---

### Post by The_Grudge on 2010-06-07
Thanks for the response _khAttAm_

I do have compiz disabled. The last time it crashed the error said something about "pulse audio" and "checking battery state", whatever that means. 

Having said that, I was able to find something that makes it crash everytime. When I go into the screensaver options and start previewing screensavers it'll crash everytime which leads me to believe it's something to do with the graphics. 

So assuming I have compiz disabled (effects turned off), is there anything else I can try?

Thanks again.

---

### Post by The_Grudge on 2010-06-08
Bump:guitar:

---

### Post by The_Grudge on 2010-06-08
Heres a snippet from my log file. Lots of errors, not sure what any of them mean or how to fix.

Jun  5 10:46:58 UbuntuBasement kernel: [11772.012018] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun  5 10:46:58 UbuntuBasement kernel: [11772.012031] render error detected, EIR: 0x00000000
Jun  5 10:46:58 UbuntuBasement kernel: [11772.012070] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 186426 at 186421)
Jun  5 10:47:00 UbuntuBasement kernel: [11774.304033] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  5 10:47:00 UbuntuBasement acpid: client 4738[0:0] has disconnected
Jun  5 10:47:00 UbuntuBasement acpid: client connected from 4799[0:0]
Jun  5 10:47:00 UbuntuBasement acpid: 1 client rule loaded
Jun  5 10:47:01 UbuntuBasement kernel: [11775.526133] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  5 10:47:02 UbuntuBasement kernel: [11775.844015] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun  5 10:47:02 UbuntuBasement kernel: [11775.844028] render error detected, EIR: 0x00000000
Jun  5 10:47:02 UbuntuBasement kernel: [11775.844064] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 186428 at 186421)
Jun  5 10:47:04 UbuntuBasement kernel: [11777.908054] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  5 10:47:04 UbuntuBasement acpid: client 4799[0:0] has disconnected
Jun  5 10:47:04 UbuntuBasement acpid: client connected from 4807[0:0]
Jun  5 10:47:04 UbuntuBasement acpid: 1 client rule loaded
Jun  5 10:47:05 UbuntuBasement kernel: [11779.123029] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  5 10:47:05 UbuntuBasement kernel: [11779.444041] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun  5 10:47:05 UbuntuBasement kernel: [11779.444054] render error detected, EIR: 0x00000000
Jun  5 10:47:05 UbuntuBasement kernel: [11779.444188] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 186430 at 186421)
Jun  5 10:47:07 UbuntuBasement kernel: [11781.500075] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  5 10:47:08 UbuntuBasement acpid: client 4807[0:0] has disconnected
Jun  5 10:47:08 UbuntuBasement acpid: client connected from 4815[0:0]
Jun  5 10:47:08 UbuntuBasement acpid: 1 client rule loaded
Jun  5 10:47:08 UbuntuBasement anacron[4396]: Job `cron.daily' terminated
Jun  5 10:47:08 UbuntuBasement anacron[4396]: Job `cron.weekly' started
Jun  5 10:47:08 UbuntuBasement anacron[4839]: Updated timestamp for job `cron.weekly' to 2010-06-05
Jun  5 10:47:09 UbuntuBasement kernel: [11782.723059] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  5 10:47:09 UbuntuBasement kernel: [11783.044040] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun  5 10:47:09 UbuntuBasement kernel: [11783.044054] render error detected, EIR: 0x00000000
Jun  5 10:47:09 UbuntuBasement kernel: [11783.044095] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 186432 at 186421)
Jun  5 10:47:11 UbuntuBasement kernel: [11785.108079] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  5 10:47:11 UbuntuBasement acpid: client 4815[0:0] has disconnected
Jun  5 10:47:11 UbuntuBasement acpid: client connected from 4847[0:0]
Jun  5 10:47:11 UbuntuBasement acpid: 1 client rule loaded
Jun  5 10:47:12 UbuntuBasement kernel: [11786.304214] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  5 10:47:12 UbuntuBasement kernel: [11786.624069] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun  5 10:47:12 UbuntuBasement kernel: [11786.624085] render error detected, EIR: 0x00000000
Jun  5 10:47:12 UbuntuBasement kernel: [11786.624139] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 186434 at 186421)
Jun  5 10:47:15 UbuntuBasement kernel: [11788.688090] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  5 10:47:15 UbuntuBasement acpid: client 4847[0:0] has disconnected

---

### Post by The_Grudge on 2010-06-09
One more "bump" then I'll give up.
 
Thanks in advance for any help

---

