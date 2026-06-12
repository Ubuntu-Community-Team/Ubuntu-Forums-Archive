---
title: "VoIP Mic is Garbled, Sound Recorder is OK"
date: 2010-08-27
forum: General Help
---

### Post by cambot on 2010-08-27
Wonder if someone has experience with this.

Ubuntu 10.04. The Mic input works for the sound recorder application. I can record and play back no problem. However, when I go to use a VoIP application -Skype/Google Voice/anything, the voice is garbled or almost non-existant, I can hear the other party with no problem. They can't hear me. The mic works fine in Win7/XP, however. 

As stated, recording with sound recorder works absolutely fine. It's only when using a VoIP call that the mic is garbled and unusable. 

Help! I really want to use Google's Phone.

---

### Post by quixote on 2010-08-29
Voip uses different ports and protocols for ringing, voice in and voice out.  You must have all the right ports open or you would get only silence for that aspect of it.  But maybe you have the wrong protocol (?? just guessing, I have no idea) --it should be UDP and allow both incoming and outgoing on all the ports voip needs -- or maybe the wrong codecs in the the voip software setup.

What I'm pretty sure this is not, is a mic problem.  The issue is in the voip somewhere.

---

### Post by cambot on 2010-08-30
Yes however I think this problem is specific more to PulseAudio than anything else.

For example, a Windows XP machine on the same network is fine- the garbled thing doesn't happen. So as a test, I installed XP into a Virtualbox VM on Ubuntu, and set the audio to use the ALSA driver. And...it works like a champ. The problem also happens with Skype. However, if I'm recording, the problem doesn't appear. The mic is crystal clear on playback. Even the Skype test call sounds fine- the service can hear the mic OK. However once it gets passed to an actual call, the mic sounds garbled and inaudible.

Still thinking it's a PulseAudio problem as I've read tons of stuff that it still doesn't play well with Skype and Google's Phone.

---

### Post by quixote on 2010-08-30
Ah, yes.  Pulseaudio.  Words can't express how I feel about that POS.  Yeah, that could indeed be it.  There are ways to remove pulseaudio and force it to use alsa, but that's not my forte.  Last time I tried it, I managed to lose sound entirely.  Maybe somebody who actually knows how to effectively uninstall pulseaudio will hop on.

---

