---
title: "Wine + &quot;any program&quot; = no sound in one of them"
date: 2010-04-28
forum: General Help
---

### Post by Velvet Karuda Leopard on 2010-04-28
I have searched the Wine HQ website and got no answer.  Wine works fine and my other sound applications, rhythmbox, vlc, etc work just fine, but any time I play Wine with any of them only the app started first has the sound.

I am not fluent with the sound in Linux.  I am using Ubuntu 9.10.  I didn't have this problem in 9.04.

It isn't a huge problem, just a major inconvenience.

Any help would be appreciated.

---

### Post by thumper13 on 2010-04-29
I'm not an expert, I'm just telling you what I've done in the past to make it work...

If you go to the terminal and type in "winecfg" (without the "'s) it should bring up a configuration screen.

Pick the Audio tab at the top.

Listed there is a list of options to have the audio play back as (codecs I believe.) Some options are ALSA, OSS, PulseAudio, etc.

AFAIK, OSS playback will not do multiple playback on the sound card, so uncheck that box and check off ALSA. That should allow you to use more than one "sounding program" at a time.

Like I said, I'm not a pro, but I'm just trying to help, so don't hate me if I'm wrong :)

---

