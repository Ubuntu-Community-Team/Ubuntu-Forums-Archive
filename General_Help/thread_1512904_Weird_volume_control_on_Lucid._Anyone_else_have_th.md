---
title: "Weird volume control on Lucid. Anyone else have this problem?"
date: 2010-06-18
forum: General Help
---

### Post by Macfunky on 2010-06-18
As opposed to Jaunty, which i previously use, i find the volume control on Lucid a bit weird. If i want to change the volume it's not very helpful. The very start (left of the volume control) turns it down very quickly and the end (far left of the control) turns it up very quickly. The other 80 percent in the middle does very little. Its annoying as usually i end up using the volume control on my speakers as i don't have much control. Most of the fader does nothing and either side changes the volume so much that it's not useful. Anyone else have this problem? I had no problem with Jaunty. It had a consistent volume control throughout the fader. Lucid doesn't, at least not on my installation. Anyone know what could be up? Could i have some setting set incorrectly?

---

### Post by phildini on 2010-06-18
It almost sounds like your volume control is increasing logarithmically, which is actually how the decibel scale increases. 

Have you tried checking the audio settings in the menu? What does it say the audio device is?

---

### Post by Macfunky on 2010-06-18
It says that it's using "Internal Audio 1 output/1 input Analog Stereo Duplex". This is the default soundcard i'm assuming. I don't think this is any different than in my previous installation of Jaunty. I'm wondering why this would cause this problem. It's very annoying. Any ideas?

---

### Post by medg85 on 2010-06-19
I am having the same problem. I have just updated from Karmic using the Update Manager. If I go to alsamixer in the terminal you can see it jump to 100% on "Front" when you turn volume up to ~ 10% on the volume slider! This page has helped me fix the problem, although I am still unsure why it happened in the first place!

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies)

Good luck!

Matt.

---

### Post by Macfunky on 2010-06-20
> **medg85 said:**
> I am having the same problem. I have just updated from Karmic using the Update Manager. If I go to alsamixer in the terminal you can see it jump to 100% on "Front" when you turn volume up to ~ 10% on the volume slider! This page has helped me fix the problem, although I am still unsure why it happened in the first place!

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies)

Good luck!

Matt.

Thanks a million for the link. The first workaround didn't work. It actually disabled my volume control altogether :P But the second workaround worked a treat. Thanks again. That was bugging my head. Nice to have control back of the volume again :D

---

