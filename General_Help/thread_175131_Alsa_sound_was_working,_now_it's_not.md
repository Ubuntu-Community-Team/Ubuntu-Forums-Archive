---
title: "Alsa sound was working, now it's not"
date: 2006-05-12
forum: General Help
---

### Post by bforbes on 2006-05-12
I had ALSA sound working in Kubuntu 5.10, kernel 2.6.12-10 after a lot of effort. Everything was fine. I walked away from my computer, came back 30 seconds later, and sound had just STOPPED WORKING. Nothing coming out of the SPDIF or analog ports on the motherboard. Alsamixer works fine, and all applications that use sound seem to think everything's fine.

I literally didn't touch the computer between when it was working and when it stopped, and nothing was running. I've checked that everything works from Windows XP, so it's probably not a hardware problem.

I've reinstalled the kernel a number of times, since that was what fixed everything for me previously, but it hasn't helped. One interesting thing is that when I change the IEC958 volume to full in alsamixer, the stereo connected to SPDIF shows "UNLOCK" on the screen, so some sort of connection must have been made to the stereo.

Is there anything I can do to determine where the audio output from applications is going?

---

