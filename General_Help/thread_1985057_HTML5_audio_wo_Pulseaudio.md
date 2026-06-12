---
title: "HTML5 audio w/o Pulseaudio"
date: 2012-05-22
forum: General Help
---

### Post by nomodeset on 2012-05-22
Hello,

I'm using Firefox 12.0 (Ubuntu 12.04 x86) and strangely sound output is missing while watching WebM videos on YouTube or starting any HTML5 audio demonstrations. This can be easily fixed by enabling the Pulseaudio backend. However, I am looking for a proper solution. Does Firefox ignore the .asoundrc configuration? Or do I have to remove Pulseaudio completely? My gstreamer based media players work fine without Pulseaudio, but only Firefox won't play the audio streams. And yeah, no sound issues with Flash Player, just with HTML5 audio.

Thanks :)

---

### Post by nomodeset on 2012-05-25
Can't reproduce the issue anymore.. very strange.

---

### Post by idoitprone on 2012-05-25
> **nomodeset said:**
> Can't reproduce the issue anymore.. very strange.

I just dont get the pulseaudio hate. I understand if people hate alsa, but not pulseaudio.

btw, if the problem in question do not use the native alsa api, then one program will steal the entire audio stream. This is a problem pulse audio is suppose to fix. If you do not want pulseaudio then I will suggest you to use kde with phonon or oss4

---

### Post by brainwash on 2012-05-25
I prefer ALSA over Pulseaudio. :D

Does anyone actually use OSSv4 on Ubuntu based systems?

---

### Post by idoitprone on 2012-05-26
> **brainwash said:**
> I prefer ALSA over Pulseaudio. :D

Does anyone actually use OSSv4 on Ubuntu based systems?

If you use pulseaudio, you are using alsa...In fact, alsa might be the largest contributor to broken sound..

---

### Post by brainwash on 2012-05-28
> **idoitprone said:**
> If you use pulseaudio, you are using alsa...
That's right. I intended to say, that I prefer **raw** ALSA over PA. No need for an extra daemon and forced software mixing.

Nevertheless, PA offers many great features, the integration is pretty good and it can be disabled easily. I don't want to use nomodeset's thread to discuss my actual question, maybe I'll create another dedicated to OSSv4.

---

