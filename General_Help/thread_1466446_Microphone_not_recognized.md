---
title: "Microphone not recognized"
date: 2010-04-30
forum: General Help
---

### Post by Rylius on 2010-04-30
This is bugging me now since I upgraded to 9.10.
Back then it broke my sound completely, I switched to OSS4 then.
OSS unfortunately doesn't recognize my microphone, which is kinda annyoing to a gamer like me :p
I removed ALSA too, Pulse is disabled.

So just finished upgrading to 10.04 full of hope to get this fixed...
During install it asked me if I would like to overwrite the pulse-configs, thought couldnt harm and did it.
Realized it broke my sound again, disabled the pulse demon again und I'm running only OSS at the moment. Output works really fine, Firefox, Quake3, Mumble - no problem.
But my microphone is not listed anywhere, and if I look into the Mumble configuration it looks like it's using my headphones as input.
My clanmates said they could hear the music I was playing :D
(To get Quake 3/Urban Terror working I needed to remove libsdl1.2debian-pulse and install libsdl1.2debian-oss)

So I finally decided to research a bit more, but did not find any similar problems, so I came here.
Does anyone have an idea how to adjust the devices in OSS?
I'm not that experienced in this deep stuff here :/
Soundcard is some HDA Intel, duno where to look exactly since /etc/asound is gone :p

If everything fails I'm going to completely reinstall 10.04.
If this won't fix it, I'll leave 2 nice years of Ubuntu behind and switch to another distro. :/
Although I wouldn't want to do any of the last two options :/

So, hopy anyone can help me here.
I don't have any problems switching back to either Pulse or ALSA, as long as my mic will work again. :/

---

