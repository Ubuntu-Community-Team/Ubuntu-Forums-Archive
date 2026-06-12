---
title: "Getting logged out when running wine since Maverick update"
date: 2010-11-14
forum: General Help
---

### Post by emerald000 on 2010-11-14
I have been running MoyoGo ([http://www.moyogo.com/](http://www.moyogo.com/)) with wine on 9.10 without any problem. I recently updated to 10.10 with the update manager. Now, whenever I try to run it, I get back to the login screen some seconds after the splash screen of MoyoGo appears.

I am running wine 1.3.7, but I tried a couple of earlier versions with the same results. I can also run other programs under wine without any problem.

Here's the terminal output, showing what seems like a Xserver problem:

```
fixme:shell:FileIconInit (true)
fixme:mixer:ALSA_MixerInit No master control found on ThinkPad Console Audio Control, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x218f50,0x21d0a0): stub
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 87165 requests (87163 known processed) with 0 events remaining.

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 1005 requests (970 known processed) with 0 events remaining.
```

I haven't posted this on the wine forum, as it is more likely an Ubuntu problem, but feel free to move the thread if you feel it is appropriate.

And thank you in advance for your help!

---

### Post by emerald000 on 2010-11-15
Anyone?

---

### Post by emerald000 on 2011-01-12
Still happening.

---

