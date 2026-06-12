---
title: "I have no sound through my headphones, tried everything"
date: 2011-05-10
forum: General Help
---

### Post by Resdayn on 2011-05-10
First of all I wish to say hello to the Ubuntu community here, as this is my first post.
I have a very annoying problem with my sound. In the very beginning, I had no sound through my headphones (headset mic was OK), but I did have sound through my speakers. My headset is connected to the front jacks, and my speakers to the rear green out. My sound chip is a VIA VT2020 on the ASUS Crosshair IV Formula mobo. I've read the troubleshooting page about snd-hda-intel chips and this is what I tried to fix it:

I checked the model list and according to the list I should add "options snd-hda-intel model=auto" to the alsa-base.conf, so I did: No result. Then I replaced "auto" with "generic". I now had sound through my headphones and through my speakers as it should: When my speakers were turned off, I could hear sound through my headphones. But: My headset microphone didn't work anymore: just static.
After browsing through several help topics looking for somebody who had the same chip, I found somebody that fixed it by using "model=6stack-digout" instead of "auto" as suggested in the snd-hda-intel model list.
After a reboot, my problem was solved! That was yesterday. 

I just booted into Kubuntu again, and I didn't hear the soothing startup sound. The alsa-base.conf was still the same as I left it yesterday, but for some reason, I could not hear sound through my headphones anymore. What I noticed, is that when I mute the headphones channel in Gnome ALSA Mixer, my speaker sound gets muted too.

I'd like to have my sound "as normal" again, which means: I can hear sound through both my speakers and my headset whenever I want to, and my headset mic works. (Like I said, this was the case yesterday)

I know there are more people who had a problem with an snd-hda-intel chip, but I'm beginning to think that my problem is becoming rather unique, as I've tried almost everything. I've been using Ubuntu/Kubuntu for about a month now and I must say that after I switched to Kubuntu, I really start to like it, but this little sound problem is just killing some of the experience if you know what I mean. :(

Maybe this post is a bit long, but I hope the community can help me out with this problem. I will provide any info needed. Thanks in advance!

~Resdayn

---

### Post by vivimos on 2012-05-17
I believe it is fixed in version 1.0.25 of the alsa kernel. You can find your current version with:

cat /proc/asound/version

Carl

---

