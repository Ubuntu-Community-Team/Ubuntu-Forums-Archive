---
title: "System upgrading crash -&gt;sound problem afterwards"
date: 2009-07-07
forum: General Help
---

### Post by alejiss on 2009-07-07
I was making a routine upgrade but the downloading windows crashes, then my system was blocked so I restared the system and when it come back the sound doesnt work it makes some weird sound evrytime there is a sound.

I went to the  Comprehensive Sound Problem Solutions Guide and reinstall the packages:

typed the following code in the terminal:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

sudo apt-get install gdm ubuntu-desktop

restart my system but the problem remains, I know it should be related with the last upgrading when it crash.

what can i do to fix my sound problem and to see if there is other problem with the routine upgrade that failed.

---

