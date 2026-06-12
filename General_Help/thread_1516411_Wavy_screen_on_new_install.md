---
title: "Wavy screen on new install"
date: 2010-06-23
forum: General Help
---

### Post by Geekkake on 2010-06-23
Just installed Ubuntu via Wubi (I know, I know, I'm just trying it out) on a W7 machine. ASUS OEM, AOC monitor. Intel HD integrated graphics, currently connected via VGA. Very new to Linux in general.

Running at 1920x1080 and 60 Hz (only available refresh rate option when booted in both Windows and Ubuntu), the screen seems to "vibrate". When I lower the res, it appears that there's a mess of wavy lines around everything.

...that's odd. I just went to go take screenshots of it, and the effect doesn't appear in the screenshot. I tried disabling KMS (though I'm not even really certain if that's applicable) with the command "echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf" and get "permission denied".

Output for attempting to configure Xorg with "sudo Xorg -configure:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


As an aside, the effect does not occur when booting back into Windows.

Any thoughts on how I can resolve this issue? I'm starting to get quite the headache.

---

