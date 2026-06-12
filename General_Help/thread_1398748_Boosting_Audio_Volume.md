---
title: "Boosting Audio Volume?"
date: 2010-02-04
forum: General Help
---

### Post by Norec on 2010-02-04
I have been having this problem for a while. For most things, even when I turn up the volume, the volume is extreemly low. I know for a fact that my computer should be much louder, as when I installed Windows 7 on it, it was compleetly satisfactory.

So, I was wondering if there was any software/tweeks that could help mee boost the max volume considerably on linux. (I am running Karmic Koala)

Thanks for you help,
Norec

---

### Post by cariboo on 2010-02-05
Install alsa-utils from the repositories, it includes alsmixer in the package. once installed, open a terminal and type alsamixer at the prompt, make sure all the controls are turned up.

---

### Post by Leppie on 2010-02-05
if you install pulseaudio, you can set the max to something like 400% i believe (trust me, if you want to blow your speakers out of your laptop you can do it with pulseaudio).
```
sudo apt-get install pulseaudio
```

---

### Post by Norec on 2010-02-05
> **Leppie said:**
> if you install pulseaudio, you can set the max to something like 400% i believe (trust me, if you want to blow your speakers out of your laptop you can do it with pulseaudio).
```
sudo apt-get install pulseaudio
```

Ok so I installed PulseAudio, but I cant figure out how to set the max volume. Any chance you could tell me how?

---

