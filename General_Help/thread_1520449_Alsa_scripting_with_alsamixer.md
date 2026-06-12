---
title: "Alsa scripting with alsamixer?"
date: 2010-06-29
forum: General Help
---

### Post by Darth_tater on 2010-06-29
Hey all. I've got a question about ALSA's command line utilities.

Right now, ive got a a desktop with built in speakers and a sound card in the back.  Currently, the speakers are set as the default sound source.

The only way i can get the soundcard in back to work is to mute the external amplifier manually with alsamixer

I have to run alsamixer, then mute my external amp.

I currently have to do this by hand, and it's a pain in the ***.
What i want to do is have this done during boot up.  

So does anybody know what alsamixer command line flags there are ( i cant find any...) that would allow me to *mute* or turn off an internal amp?

-- Thanks!

---

### Post by kerry_s on 2010-06-29
**man amixer**

you should be able to that from the volume icon in pulse audio(default in ubuntu). look under hardware or output.

---

### Post by Darth_tater on 2010-06-29
I dont have a gui :)


and the command line flags for this utility dont allow me to mute.

EDIT: I finally found a mailing list entry that had what i needed:

amixer -q -c 0 sset 'External Amplifier',0 mute

---

