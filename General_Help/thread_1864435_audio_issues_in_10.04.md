---
title: "audio issues in 10.04"
date: 2011-10-18
forum: General Help
---

### Post by Xeneth on 2011-10-18
I started having odd audio issues.  When playing back video, no mater what player, the audio progressively gets delayed.  This is not files related because I have tried playing multiple video files. 

When I say "progressivly delay" means that the longer it plays, the farther behind it gets.  The odd thing is that if I pause the video, the sound continues until it reaches the point I paused, then it is synced but starts delaying again.

A second issue which may or not be related, but randomly, my sound cuts out, and instead gets replaced with what sounds line metallic scraping.  It's a coding error with audio, and I can pause and play with no change.  When I go up to "System > Preferences > Sound" and change the profile under hardware, it starts working.  

I am no expert with linux so please be patient.  Any help please?

---

### Post by Xeneth on 2011-10-19
NvM, I found the command to redo sound setting to default on ubuntu help pages.  In truth I wish I knew what did happen, but it is working now.

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

