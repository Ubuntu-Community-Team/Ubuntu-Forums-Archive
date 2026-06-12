---
title: "My microphone misbehaves."
date: 2010-11-29
forum: General Help
---

### Post by theShaggy on 2010-11-29
I'm confused by how microphones are handled in Ubuntu.

At some point in the recent past, it would work fine when trying to chat in Steam.  It came through without a problem.  And then, suddenly, it stopped.

Now, I've removed PulseAudio and have put it back in, taken it out, run with Alsa, OSS4, and everything, but nothing seems to solve the problem.

With enough tweaking, I can get my microphone to FINALLY be recognized by Skype, but only on very, very rare occasions is it recognized by anything else including Steam (Left4Dead and TeamFortress 2), TeamSpeak, or WoW.

Worse is that when it works for Skype (after the aforementioned excessive tweaking that I still haven't figured out), as soon as I try going to WoW, or Lord of the Rings Online or anything that requires a mic, I lose microphone anywhere else.

I'm very confused and frustrated by this.  Can anyone help me figure out what to do?

Running Maverick 64-bit with Alsa sound.  I've had more luck with Phonon in Kubuntu across the board than I have with anything in Gnome.

Thanks!

---

### Post by theShaggy on 2010-12-06
Anyone?

---

### Post by theShaggy on 2010-12-11
I have tracked down the problem at least to the following situations:

1. When using Flash, particularly YouTube, in any of the browsers (Chrome, Firefox).

2. When loading World of Warcraft, which seems to co-opt the microphone and leave it unused.

If I use sudo alsa force-reload then I have no problems getting it to run any more.

Anybody have advice?

---

### Post by theShaggy on 2010-12-16
Seriously, nobody?

Nobody else even has the same problem as me?

---

