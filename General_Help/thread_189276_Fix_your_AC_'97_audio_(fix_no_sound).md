---
title: "Fix your AC '97 audio (fix no sound)"
date: 2006-06-05
forum: General Help
---

### Post by ericesque on 2006-06-05
I've seen a lot of posts about people losing their audio on upgrade or having no sound after installing.  Here's what worked for me:

Open **volume control** (sound icon on panel). In **volume control** select

[I]file>change device
[/I]
 make sure that you have the **'IXP (Alsa Mixer)'** selected.

Then go to *edit>preferences*

check the **'External Amplifier'** option then click close.

While still in the **volume control** there should be a new tab called **'switches'**--select it.

Uncheck **'External Amplifier'**

close the window and check for sound.
[B]
PLEASE REMEMBER that Ubuntu does not support a variety of sound codecs.  So attempting to play MP3s or other unsupported formats for your sound check will not get you anywhere.
[/B]

hope this helps.

---

