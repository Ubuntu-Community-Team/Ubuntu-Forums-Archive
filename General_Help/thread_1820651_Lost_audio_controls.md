---
title: "Lost audio controls"
date: 2011-08-07
forum: General Help
---

### Post by ThatIdiot on 2011-08-07
Audio in wine wasn't working and a post on the Wine forums said to run 'killall pulseaudio' I did that, but now I can't control my volume, and I can't open up the sound preferences. I tried re-installing pulseaudio and then rebooting, but nothing changed. :confused:

Trying to open up Sound preferences: "Waiting for sound system to respond"
Trying to open up volume control under Sound & Video:  "Connection failed: Connection refused"

I also have this, if it helps at all: [http://www.alsa-project.org/db/?f=f976a73c89fd7af025952b76ce19c7a1b894d38f](http://www.alsa-project.org/db/?f=f976a73c89fd7af025952b76ce19c7a1b894d38f)

---

### Post by lmarmisa on 2011-08-07
Try this command:

```

rm -r ~/.pulse*

```

Then reboot your system.

---

### Post by ThatIdiot on 2011-08-08
Didn't work. :(
btw, I hear that login sound twice (the drums). they're like, overlapping each other. not sure if that'll give a bit more info on my problem.

---

### Post by lmarmisa on 2011-08-08
Try to create a new user account (named test, for example) and check if the audio works fine there.

---

### Post by ThatIdiot on 2011-08-08
Audio doesn't work on a new account either. :(

---

