---
title: "Frustrating sound problem: working mic doesn't work!"
date: 2010-08-03
forum: General Help
---

### Post by fizikz on 2010-08-03
I was just using the mic and watched it stop working suddenly. I was in the middle of a skype test call when the graphical mixer level died down to zero in the middle of the call. When the test call was played back, the first part sounded fine then the sound got lower until it became inaudible. Since then I can't get any sound from my mic in skype. Also, the audio input level graphically shown in Sound Preferences shows no fluctuations in sound as it used to before. The input device is enabled. I tried using Sound Recorder to record some sound clips and that worked fine. So the mic is working but Sound Preferences and Skype seem to have the mic level really low. I'm not sure what else to think considering it was working perfectly a few minutes ago. I've tried restarting, but that didn't fix it either.

---

### Post by wesleybailey on 2010-08-03
In your skype options(Sound Devices) is the "Allow Skype to automatically adjust my mixer levels" box checked?

I tried using skype with that enable, but my mic was to sensitive and it caused problems. Try unchecking that box.

---

### Post by fizikz on 2010-08-03
Yes, I've tried again with that boxed unchecked and it isn't working. But for the record, it previously worked with it checked.

---

### Post by fizikz on 2010-08-05
I found what was wrong. In Pulseaudio Volume Control (pavucontrol) under the Input Devices tab, both sliders for L and R channels were at 100%. I put the R to 0% and now the mic works properly. I have no idea how things changed, but at least that problem is fixed. 

I still don't know why any ringing sounds don't work in Skype, but that's a separate problem, so I'll mark this problem as solved.

---

### Post by fizikz on 2010-08-05
Got my last Skype problem solved too. Turns out if you want to hear the incoming call ring and other such notifications, you need to have system sounds enabled (Sound Preferences -> Sound Effects tab, Alert volume). Now that I un-muted that, everything is working just fine.

---

