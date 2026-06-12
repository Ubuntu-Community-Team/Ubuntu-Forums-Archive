---
title: "Extremly slow videoplayback while Chromium Browser running"
date: 2010-04-30
forum: General Help
---

### Post by a-user on 2010-04-30
Well, i decided to open a new thread for this VERY strange issue.

I can watch movies without problems, with the default videoplayer in ubuntu and with xbmc. but if i have a chromium web browser window open (in the background) i have about 1 frame / sec in videoplayback and no sound.

the no sound problem may be related to the fact that im using sound over hdmi. i am using the nvidia proprietary drivers for my gt220.

how can it be that a simple webbrwoser is slowing down videoplayback in other programs?

p.a. this does not happen if i'm having firefox instead of chromium open.

---

### Post by a-user on 2010-05-03
push

---

### Post by TBABill on 2010-05-03
Could it be a memory leakage issues? Lots of posts regarding recent upgrades to Chromium from the daily PPA.

---

### Post by Mazin on 2010-05-03
I would be curious to know if this problem happens with the official Chrome you get from Google instead of the Chromium build from the PPAs.

---

### Post by TBABill on 2010-05-03
The posts on the forum I have seen suggest it is the latest version that is the culprit and reverting back a couple daily releases solves the problem. I am using the one from the repositories, not the daily PPA, so I can't confirm.

---

### Post by a-user on 2010-05-04
no, this happens with any version since at least the initial shiped with ubuntu lucid release. it also happend during lucid beta 1 and 2. and it happens with the latest ppa version.

as soon as chromium is running every other video player software cannot output sound and the palyback speed reduces to arround 0.5 frames per second if it does not get stucked.

killing chromium imediatly returns video playback to normal. this is a MAJOR bug as a browser should never have influence on other programms running.

---

### Post by tommyasplund on 2010-05-14
I have this problem to running Lucid, Chrome 5 and XBMC 9.11. Sound via hdmi.

When I start playing a file in XBMC I get this message:
"Failed to initialize audio device"

Has anyone found any kind of workaround for this problem?

---

