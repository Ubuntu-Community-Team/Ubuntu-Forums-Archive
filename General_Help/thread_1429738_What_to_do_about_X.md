---
title: "What to do about X"
date: 2010-03-14
forum: General Help
---

### Post by Tamalin on 2010-03-14
Every time I start the movie player (totem) on my ubuntu laptop, X crashes.  When this happens, neither my mouse nor my keyboard will respond, and I have no way to shut down my computer besides holding down the power button for a couple seconds for a manual shutdown.  Somehow, I get the impression, this isn't the best way to shut down my laptop.  When my computer freezes like this, what can I do to shutdown my laptop without just manually powering it down?  Or better yet, is there a fix for the X bug?  I can't shut down my computer over the network, all the other computers run Windows Vista (they are not mine), at least I can't do it without a lot of fiddling with Vista/Ubuntu and hundreds of tries.  Any ideas?

---

### Post by mr_rg on 2010-03-14
If everything is frozen, not much you can do other than the power button.
Your keybord might not be locked so try Ctrl-Alt-f1 (or f2, f3..) to get a console.
If this works login and type: sudo shutdown -h now

Better to fix the problem with the player.

If rebooted after a crash check what it says in the logs:

Xorg.0.log.old  Should show the previous boot (Xorg.0.log the present boot)

Also look at the end of:
/var/log/dmesg.0

If you find weird error messages plug them into google.

Other things to check, what graphics card do you have?
Are you using "direct rendering" ? Check with:

glxinfo

At the top it says direct rendering yes or no.
Most graphics card support this so if it says no..
You should install the right graphics drivers, to enable
it..this might solve the problem.

Also try other movieplayers like xine and vlc.

Other things to try could be the player logs and to start the player with a tracer
ltrace and strace.. to see what happens.

---

### Post by adam814 on 2010-03-14
Hold ALT+PrintScreen and type this sequence: R S E I N U B

This will (among other things) sync the disks and reboot.

That's assuming you can't CTRL+F1 and get to a terminal of course, if you can do that you can just restart X or shut down from there.

---

### Post by Tamalin on 2010-03-14
OK, yes I am using direct rendering.  My graphics card is apparently is "Intel 915" apparently, but I don't see any driver installed for it.  This problem seems to be related to Xine.  I can't remember exactly what I did with it when I installed it, but I seem to remember it being a plugin for totem or something of the like.  Maybe I should remove it?  I don't use the video player very often.

PS: Hold ALT+PrintScreen and type this sequence: R S E I N U B: I will try this if I have the problem again.

---

