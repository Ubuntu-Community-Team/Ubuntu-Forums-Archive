---
title: "No PulseAudio in Natty"
date: 2011-05-03
forum: General Help
---

### Post by kyfho23 on 2011-05-03
OK, after struggling for a couple days with Pulse not working in Natty, I found a solution, and it's easy:

Delete the ~/.pulse folder in your home folder. I keep a separate home partition, and apparently some of the old settings conflicted with the new setup.

---

### Post by bobcatt on 2011-06-14
Hi,

Well, this actually didn't solved the issue for me. All the sound layer was broken with Pulse Audio, but alsa was fine.
I then discovered that some users were not in the right groups so I did the following.

I added my user to groups "pulse" and "pulse-access". The user was also part of the "audio" group.

As I also run MPD (Music Player Daemon) as a system service, I did the same with user "mpd".

All was fine after that.

---

