---
title: "PulseAudio &amp; Skype -- Selecting devices"
date: 2010-06-29
forum: General Help
---

### Post by kidko on 2010-06-29
I recently upgraded from Xubuntu 9.04 to 10.04[1]. In .04 my sound system worked great, and without PulseAudio as far as I know. I used a USB headset to handle Skype calls, both input (the mic) and output (the headphones). Rhythmbox and the like still went to my speakers.

However, once I upgraded, the only option under Skype's audio settings is "PulseAudio Server (local)." I no longer know how to, if I can at all, redirect my conversations to the headset. It works fine as a microphone, but all of the calls come through the speakers now.

As I said, I've never interacted with PulseAudio before, so there might be an easy solution to this. Or there might not be one; I don't know. Does anybody have an idea as to how can I choose where my sounds goes? Thanks in advance!

________________
[1] The upgrade also had 9.10 in the middle, but it was just a stepping stone. I never used it except to upgrade to 10.04, so I couldn't tell you if my configuration was screwed up at that point.

---

### Post by DJonsson2008 on 2010-06-29
Are you using the lastest version of Skype?

I recall having much better luck with pulse audio
after updating to Skype Beta 2.1

---

### Post by kidko on 2010-06-29
I've been running Skype 2.1 beta 2, which (according to the site) is the latest version.

Is there a PulseAudio configuration utility or something of that nature that handles devices?

---

### Post by kostkon on 2010-06-29
Yes, install the PulseAudio Volume Control utility. Start Skype, then open the volume control and set the input and output device for it.

---

### Post by sandyd on 2010-06-29
install pavucontrol, and then you can adjust it through pavucontrol when skype is running

---

### Post by kidko on 2010-06-30
That did the trick. From there I could choose my devices. Thank you!

---

