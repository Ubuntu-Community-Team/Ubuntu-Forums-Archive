---
title: "Only Some Sounds"
date: 2010-01-08
forum: General Help
---

### Post by Beastlicker on 2010-01-08
It seems that only music in Amarok and system sounds work. I tried youtube vids in firefox, and nothing. I downloaded one of my favourite games: Neverball, and no sound. I tried switched to PulseAudio, but it just fell back to my speakers. Any help?

---

### Post by Zorael on 2010-01-08
First thing to check is your volumes.

As an example, my netbook has three volume channels that all affect output multiplicatively; Master, Front and PCM. If they're all at 100%, my total sound output is 100%. If they're all at 80%, the total output is 51.2% (0.8^3). And obviously, if one or more of them is at 0%, the total output is 0%. So I just max out Front and PCM, and then use Master as my volume slider.

Now, KDE only seems to take Master and Front into consideration, while Flash, Firefox and other non-KDE stuff also obeys PCM's setting. And something keeps lowering my PCM volume to 0, which mutes sound in those apps.

So, pop up kmix and make sure nothing there is muted or at 0%.

---

### Post by Beastlicker on 2010-01-08
Thanks a bunch. That worked. I never knew about the PCM and everything.

---

### Post by hyperdude111 on 2010-01-08
Which version of KDE are you using? I installed KDE 4.4 beta1 this morning and for the first few hours sound worked fine. Anyway I rebooted in to windows then back into KDE and have mixed sound issues.

The KDE startup sound works fine but the desktop then informs me it thinks one of the sound drivers can be removed as it is not needed. I dis allow this and go to audio manage preferences. On testing the options under audio I see that the analog driver  for my card (ALC1200) works at first and plays a test sound. However once I try to play a sound in chrome or songbird the sound is dead until re-boot. After the boot i try preferences again and realise that by even testing the other audio drivers available it instantly kills the system audio again until reboot.

EDIT: Seems to be fixed after checking the mixer settings and the Headphone setting was on mute even though the actual system wasn't.

---

