---
title: "[precise] plymouth won't stop"
date: 2012-05-11
forum: General Help
---

### Post by Mozai on 2012-05-11
Since upgrading to 12.04, plymouth's oscillating "progress bar" doesn't stop after Xserver is started.  This causes some animated noise near the top of the screen.  When I switch to the text console from the console hosting X (ie. with Ctrl-Alt-F1) the progress bar is whole, and still oscillating.

If I use `[FONT="Courier New"]sudo -- pkill -HUP -f plymouth[/FONT]` the oscillation stops, but the image of the "progress bar" remains.  The image vanishes upon switching to another console.

I believe plymouth should not show this animated "progress bar" once the computer finishes booting and is ready to accept user authentication.  I believe plymouth should not cause graphical noise in the X session.

Could someone help me diagnose and fix plymouth's misbehaviour?

---

### Post by Mozai on 2012-05-12
Alternately, could someone tell me how to discard plymouth completely?  Doing 'sudo aptitude remove plymouth' throws a frightening number of warning messages.  I would really rather see the boot messages from the init/startup scripts showing me status and error messages.  With plymouth, if something goes wrong, all I see is the "progress bar" stop, but I have no idea what happened because the pretty splash picture is all I see.

I already tried setting 
[FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT="nosplash noplymouth"[/FONT]
in /etc/default/grub and rebuilding the grub config with 
[FONT="Courier New"]grub-mkconfig >/boot/grub/grub.cfg[/FONT]
but I'm still getting plymouth's splash screen obscuring any status messages, and the progress-bar noise invading my X sessions.

---

