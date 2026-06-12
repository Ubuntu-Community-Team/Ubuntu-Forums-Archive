---
title: "Upgrade to 10.04 and strange problem with skype sound"
date: 2010-09-14
forum: General Help
---

### Post by PaulWhipp on 2010-09-14
I've upgraded from 9.10 to 10.04 and everything works fine but...

I use skype (2.1.0.81) a lot and I can make calls and receive them as normal with normal mic/sound levels.

When I get a notification the sound is so faint its almost inaudible. Clicking "Test sound" in notifications has the same effect - almost inaudible sounds (I thought they were not working at all until I turned the volume right up).

I tried completely removing and reinstalling skype through synaptic to no avail.

All the Sound devices in skype are set to "PulseAudio Server (local)" - there are no other options coming up.

"Make a test call" works fine and the skype sounds are all at the expected level.

Real calls are fine too, so long as I notice them and respond.

"Make a test sound" is silent.

Likewise, testing the event in Notifications plays the sound really quietly. Allocating different sounds makes no difference - the level is still really low so I can't work around the problem that way.

Anyone know how I can correct the ringer volume without blowing out my eardrums on an actual call?

---

### Post by PaulWhipp on 2010-09-14
Answering my own problem with some further investigation:

I installed the pulseaudio-mixer-applet to take a look and see if I could adjust some level appropriately and, sure enough, there is a 'system sounds' mono channel that for some reason was set at 20%.

Adjusting this to 100% fixed the skype issue and I can now hear my calls again.

---

