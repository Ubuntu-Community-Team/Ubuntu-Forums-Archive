---
title: "/dev/dsp: No such file or directory"
date: 2012-04-14
forum: General Help
---

### Post by AkiraBergman on 2012-04-14
I get the following message from Snd (a sound analysis program) on Ubuntu 11-10 terminal, when I try to play a sound. Snd is included in the Synaptic.

can't play : open read /dev/dsp: No such file or directory
  [audio.c[576] linux_audio_open_with_error]

I have no other sound problems. Perhaps I am missing a program.

---

### Post by AkiraBergman on 2012-04-15
After building from the sources with --with-alsa option, the sound worked. I could not get snd to find Motif (although it is in Synaptic), but it switched to GTK+, and GUI also works.

Perhaps the Synaptic version was built with --with-OSS option.

---

