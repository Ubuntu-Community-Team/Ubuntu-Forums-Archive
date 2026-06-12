---
title: "Problems following fsck"
date: 2006-05-05
forum: General Help
---

### Post by neutro on 2006-05-05
I recently booted my laptop only to find that the root filesystem had problems. I had to log as root and perform a fsck manually, which is a rare occurence when using ext3. I don't know at all why this happened, but fsck corrected dozens upon dozens of errors.

I was surprised that I was able to restart and boot just fine. I probably should have taken a look around before applying the updates that were available then, so that I would know if it's the updates or the fsck event that caused the problems I'm about to describe.

First, I got no sound. In fact, the volume control stays on mute because "no volume control elements and/or device can be found". Indeed, /dev doesn't even list a dsp, or audio, or snd.

Second, it seems that my USB ports are not working either; connecting a USB key or a mouse produces nothing. The LED on my key is not blinking when connected, so it's not being accessed. lsmod lists usbcore, ehci_hcd and uhci_hcd but, as far as I can see, nothing related to sound.

So I guess some files got hosed before/during the fsck event. Do you know which package I shoud try to apt-get install --reinstall to try to fix this? I already tried with alsa-base without any success. Any hint is welcome, since I would by far prefer not to have to re-install everything...

I guess in the worst case, I'll point my reps to Dapper and let the system update itself to see how it goes.

Thanks in advance for any hint!

---

