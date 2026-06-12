---
title: "Skype with Logitech 350 USB Headset on Karmic"
date: 2009-11-01
forum: General Help
---

### Post by gorade on 2009-11-01
Since Hardy Heron I have used Skype with a USB headset from Logitech. After upgrading from Ubuntu 9-04 to 9.10 Skype sound was muted. The version is skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb.
Before upgrading I could go to Options>Sound devices and chose which sound device to use.
After installing Karmic Koala 9.10 amd64 my only option is PulseAudio server (local).
What am I doing wrong? Is there a work around?

---

### Post by bodhi.zazen on 2009-11-05
Moved to general help.

Tips and tutorials is not a section for support threads.

---

### Post by thraxy on 2009-11-27
I see this is 3 weeks old. Did you ever get the problem fixed? I have the same issue.

---

### Post by thraxy on 2009-11-27
Interesting. I found that disabling the internal audio (audio settings - hardware) solved the problem nicely. It is a drag that it won't do that automatically though.

---

### Post by gorade on 2009-11-27
I read this one: [http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)
Then I haven't done much to it. I use the Headset microphone and the speakers for sound. 
Exactly what did you do to disable pulse audio?

---

### Post by thraxy on 2009-11-27
I didn't disable pulse. Headset is working nicely with skype though.

My headset is showing up in sound preferences as "Audio Adapter Analog Stereo". That is what I have set as Input and Output device. After that I've simply disabled the internal sound from the Hardware tab.

So now I have a perfectly working headset, but when I remove it I have no sound on the system... lol

---

### Post by gorade on 2009-11-27
I see. I have tested that mode too. Anyway it was better before the "upgrade". Then there were multiple choices in Skype.Now I chose "Simultaneous output to internal sound Analog Stereo, Premium Stereo USB Headset 350 Analog stereo, R700 Audio Device [Radeon HD 4000 Series] Digital Stereo (HDM)Stereo. 
pulseaudio is unchecked in sysv-rc-conf

---

### Post by Cotopaxi on 2010-01-07
Sorry guys: Can anyone please tell me what EXACTLY you have done to get your USB headset working with skype?

Since my upgrade to karmic Skype isn't usable anymore. My USB headset is not recognized and the headsets, which I plugin via the audio card, only receive sound, but respective microphones don't work!

Thanks for your help!

---

### Post by gorade on 2010-01-07
> **Cotopaxi said:**
> Sorry guys: Can anyone please tell me what EXACTLY you have done to get your USB headset working with skype?

Thanks for your help!

Hmm.. that was some time ago, but I'll try
open alsamix and see to that all functions are enabled.

Then System>Options>sound>Hardware: Enable Analog Stereo Outpu + Analog mono input.  Ingoing: Check Premium Stereo USB Headset 350 Analog Mono. Outgoing same. 

Look out in the upper line that the box Silent isn't checked.

I think that was what did it for me. Hope it will help.

---

### Post by Cotopaxi on 2010-01-07
Gorade you made it!

Thanks very much indeed for your help! :popcorn:

---

