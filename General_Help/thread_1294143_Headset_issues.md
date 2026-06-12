---
title: "Headset issues"
date: 2009-10-17
forum: General Help
---

### Post by Saruleus on 2009-10-17
Hey everyone, I'm a new Ubuntu user, a friend recommended it to me, and so far I love it. The only problem that has occured to me as of now is that my headset does not work, everything else works fine such as graphics drivers, but my headset doesn't. I have an ABS, Model AZ-1 headset, I tried running the setup.exe via Wine but that didn't work, any suggestions ?

---

### Post by kostkon on 2009-10-17
You need to install the *PulseAudio Device Chooser* utility (using Synaptic).

---

### Post by stinkeye on 2009-10-18
> **Saruleus said:**
> Hey everyone, I'm a new Ubuntu user, a friend recommended it to me, and so far I love it. The only problem that has occured to me as of now is that my headset does not work, everything else works fine such as graphics drivers, but my headset doesn't. I have an ABS, Model AZ-1 headset, I tried running the setup.exe via Wine but that didn't work, any suggestions ?
Im fairly new on linux so I can't give you a definitve answer but for me on jaunty,
open system > preferences > volume control
(You can also access volume control from the volume control applet that you can add to the panel.)
and see if your device is listed
if so check its not muted
If its ok then open system > preferences > sound
[ATTACH]132269[/ATTACH]
and try different settings.

---

### Post by |Mitch| on 2009-10-18
Type in terminal:

sudo apt-get install padevchooser

that will get you pulse audio device chooser

Run it from Applications/Sound and from there you can configure the sound to your headphones.

---

### Post by Saruleus on 2009-10-18
Okay, I think I got the headset detected.. using both options but I'm not sure how to configure it so the sound goes to my headset. I think the sound is there, but the sound isn't working right, as instead of hearing what the normal sound would be, I hear something like white noise. Can anyone please help ? If you have an instant messenger where I can contact you, you could PM it to me or leave it here. Thanks in advance.

---

### Post by Saruleus on 2009-10-18
Still looking for some help please !

---

### Post by Saruleus on 2009-10-18
Still looking, please I'm desperate ! I need sound to play some games and listen to music ! :(

---

### Post by Saruleus on 2009-10-18
Still looking !

---

### Post by bootdoc on 2009-10-18
first start an audio stream then open Pulseaudio device chooser as stated above.  this puts an icon on the panel.  left click on the icon and choose volume control.  click on the playback tab. there is a down arrow in the uppper right corner next to the audio stream.  Click on it and mouse over [move stream].  if your headset is recognized it will show up here and click on it to move the audio to your headset.

---

