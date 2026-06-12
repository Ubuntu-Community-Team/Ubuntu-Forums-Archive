---
title: "Refuse upgrades, install only - please help"
date: 2010-08-17
forum: General Help
---

### Post by forcecore on 2010-08-17
I try to use VLC 1.1.2 and some other soft from 10.10 repos but how to refuse upgrades that Synaptic wants to do, i want to install only.

---

### Post by snowpine on 2010-08-17
10.10 is alpha-state, currently under heavy development with 100s of mb's of upgrades; if you don't apply the upgrades, you won't get bug fixes and you won't get the final product in October. I question the wisdom of this, so why don't you back up a step and tell us why you desire to skip all the upgrades?

As far as I know, Synaptic should allow you to install an app without doing a full system upgrade. Maybe you can try installing from the command line and copy & pasting the output here?

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by forcecore on 2010-08-17
i want vlc for 10.04 not maverick system... my Lucid is 10.04.1

---

### Post by snowpine on 2010-08-17
> **forcecore said:**
> i want vlc for 10.04 not maverick system... my Lucid is 10.04.1

Whoa whoa whoa... you omitted this important detail from your original post!

The 10.10 repos are for 10.10 only!!!

My advice is STOP what you are doing, REMOVE the 10.10 repos from your software sources, and HOPE it's not too late to recover your system!

Then, read one of the many existing threads on these forums about "how to safely install the latest VLC in 10.04."

Sorry to be harsh but there is nothing I can do to support you if you continue down this dangerous path. :(

---

### Post by forcecore on 2010-08-17
Problem is noone has good vlc 1.1.2 repos anymore with new ffmpeg for vp8, Windows has always up to date full featured vlc but now c-korn abandoned his ppa and i am out of luck.

---

### Post by snowpine on 2010-08-17
> **forcecore said:**
> Problem is noone has good vlc 1.1.2 repos anymore with new ffmpeg for vp8, Windows has always up to date full featured vlc but now c-korn abandoned his ppa and i am out of luck.

If you can't find a good discussion on the topic here on UbuntuForums, you can always try [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/) for more information. Good luck! :)

---

### Post by andrew.46 on 2010-08-18
Well, I maintain a quite complex guide for building the development version of vlc but in response to the problems people are having getting a good copy of 1.1.2 I have added a small section describing how to build your own release version 1.1.2:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

This builds with an uncrippled FFmpeg 0.6 and has WebM playback amongst many other features. But certainly it is not like adding a PPA...

Andrew

---

