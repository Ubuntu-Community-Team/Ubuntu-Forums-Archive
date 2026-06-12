---
title: "Can't play urbanterror"
date: 2010-05-21
forum: General Help
---

### Post by 1243bobboobo on 2010-05-21
I  am not able to play  urbanterror after the games main menu.  

Spec:

UBUNTU 10.04

cpu - Core 2 duo (2.26GHz)
ram - 2Gb
gpu - INTEL  i915



error syslog.log:






May 19 18:44:09 jeru-laptop kernel: [ 1627.608030] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:09 jeru-laptop kernel: [ 1627.608036] render error detected, EIR: 0x00000000
May 19 18:44:09 jeru-laptop kernel: [ 1627.608051] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357646 at 357613)
May 19 18:44:10 jeru-laptop kernel: [ 1628.304030] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:10 jeru-laptop kernel: [ 1628.304034] render error detected, EIR: 0x00000000
May 19 18:44:12 jeru-laptop kernel: [ 1630.481030] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:12 jeru-laptop kernel: [ 1630.481036] render error detected, EIR: 0x00000000
May 19 18:44:12 jeru-laptop kernel: [ 1630.481048] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357652 at 357613)
May 19 18:44:12 jeru-laptop acpid: client 2028[0:0] has disconnected
May 19 18:44:12 jeru-laptop acpid: client connected from 2085[0:0]
May 19 18:44:12 jeru-laptop acpid: 1 client rule loaded
May 19 18:44:14 jeru-laptop kernel: [ 1632.041031] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:14 jeru-laptop kernel: [ 1632.041037] render error detected, EIR: 0x00000000
May 19 18:44:14 jeru-laptop kernel: [ 1632.041072] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357654 at 357613)
May 19 18:44:14 jeru-laptop kernel: [ 1632.732029] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:14 jeru-laptop kernel: [ 1632.732034] render error detected, EIR: 0x00000000
May 19 18:44:14 jeru-laptop kernel: [ 1632.732048] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357655 at 357613)
May 19 18:44:17 jeru-laptop kernel: [ 1634.952029] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:17 jeru-laptop kernel: [ 1634.952034] render error detected, EIR: 0x00000000
May 19 18:44:17 jeru-laptop kernel: [ 1634.952045] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357660 at 357613)
May 19 18:44:17 jeru-laptop kernel: [ 1635.281452] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 19 18:44:17 jeru-laptop kernel: [ 1635.281456] render error detected, EIR: 0x00000000
May 19 18:44:17 jeru-laptop kernel: [ 1635.281465] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 357664 at 357613)
May 19 18:44:17 jeru-laptop kernel: Kernel logging (proc) stopped.
May 19 18:45:06 jeru-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.



If any one can help, I greatly appreciate it.:)

---

### Post by tommcd on 2010-05-21
> **1243bobboobo said:**
> I  am not able to play  urbanterror after the games main menu.  
Spec:
UBUNTU 10.04
cpu - Core 2 duo (2.26GHz)
ram - 2Gb
gpu - INTEL  i915

What do you mean by "not able to play"?? Do you mean the game runs very slow? Or do you mean that the game won't even start?

Your graphics card may not be up to the task of playing a 3D game like Urban Terror. At the very least, you should disable all desktop effects (system > preferences > appearance > visual effects tab) and see if the game performance improves.
There is a performance cost to using compiz while playing 3D games, especially with a low end intel video card:
[http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1](http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1)
And specifically for Urban Terror and intel graphics:
[http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=3](http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=3)
Note the very low fps for Urban Terror on intel graphics.

And by the way, welcome to the Ubuntu forums!

---

### Post by 1243bobboobo on 2010-05-21
I have already tried turning off the compiz fusion, before posting to the forum.
I think it is the driver, but I need a more advance command to debug.  Thank you for your reponse.

---

### Post by 1243bobboobo on 2010-05-21
xorg   crash

---

