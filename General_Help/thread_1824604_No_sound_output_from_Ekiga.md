---
title: "No sound output from Ekiga"
date: 2011-08-14
forum: General Help
---

### Post by marsgorski on 2011-08-14
Hi,

I am using ekiga 3.2.7 on Natty and I am able to make pc-to-phone calls but I am not getting any sound on my speakers. The person on the other line is able to hear me, but I cannot hear him. Does anyone know what the problem might be?

Thanks!

---

### Post by asomad on 2011-08-14
You should start by narrowing down your problem... Your description is pretty vague... Start by verifying that your sound works at all.... Go from there.

---

### Post by marsgorski on 2011-08-14
Sorry. My sound works well, just not on Ekiga. I think it might have to do with the way Ekiga es configured. As my audio output device on Ekiga I have tried both "Default(PTLIB/ALSA)" and "HDA Intel(PTLIB/ALSA)" and neither works. Other options are "HDA Intel(1)(PTLIB/ALSA)" and "Silent(Ekiga/Ekiga)"

Any suggestions?

---

### Post by marsgorski on 2011-08-16
Anyone with any ideas?

---

### Post by Johey on 2011-10-14
I have the same problem. I can play music and call using Skype. Ekiga, however, stay silent.

In the volume settings for the ongoing call, I can see that the microphone indicator registers my voice, but the sound output indicator shows no sign of life. The video is working fine as well.

I've tried with pasuspender to disable pulseaudio. From a terminal, I typed

```
pasuspender -- ekiga
```

Using that, I didn't even manage to fire up a call. I cannot make any conclusions of that. Pulseaudio might or might not be a reason to this problem. 

I'll try out some more. In case of success, I'll promise to post a note here. I'll be happy for any suggestion though.

---

