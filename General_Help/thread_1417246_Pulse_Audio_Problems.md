---
title: "Pulse Audio Problems"
date: 2010-02-27
forum: General Help
---

### Post by Vince N on 2010-02-27
Hey All,

Having some issues with Pulseaudio today.  I'm not a big fan of Pulse and I found it to be absolute garbage in earlier versions of Ubuntu however in 9.10 its pretty much been pretty transparent for me.

However I'm starting to run into another issue with it and can't seem to find away around it.  Some programs for whatever reason cannot play sound in synchronization with video where the sound will be of by 1 to 2 seconds.  This seems to mostly affect Emulators like Gens/GS and SNES9x though I've also experienced the issue in applications such as Skype.

Is there some way to allow certain applications to bypass pulse?  Is there a way I can shut-down pulse before running a certain program and bring it back online after its done?

Is there an (EASY) way to disable pulse on the system completely without removing it, as doing so pretty much destroys the system?

Or even better.  Is there some way to configure pulse audio to play nicer with these applications?

---

### Post by dino99 on 2010-02-27
pulse can be removed without damage. Remove/purge pulse* packages and ./pulse, and ./gstreamer.
If you don't want to uninstall it, just kill the process in monitor system or htop.

But you can also help to debug reporting on launchpad:

into console: ubuntu-bug audio and let comments as in your post above.

---

### Post by Vince N on 2010-02-27
Killing Pulse doesn't help.  It just re spawns the next time sound is called.

I don't want to uninstall it, last time I tried it removed a ton of stuff including Ubuntu Desktop.

I want certain applications to fall back to Alsa ONLY and not use pulse or the Alsa Wrapper for Pulse.  Is this possible?

---

