---
title: "Breezy --&gt; Dapper, tvtime sound issue"
date: 2006-06-05
forum: General Help
---

### Post by JurB on 2006-06-05
Hi,

Today i upgraded a pc from Breezy to Dapper (fresh install) and reinstalled tvtime. In breezy it worked fine, but now i only get static for sound... I checked the config file and "/dev/mixer" is the source , "line" the channel, wich seems to be right. I tried Xawtv and get the same problem. Anyone got a clue?

tnx, JurB

---

### Post by traveller.ct on 2006-06-08
I have the exact same problem. I upgraded from Breezy to Dapper (amd64) by apt-getting and all out of a sudden I only get static for audio from tvtime.

No idea what's going on. Would love to see this solved.

---

### Post by JurB on 2006-06-10
Glad to see i'm not alone!
No progress to report... watching tv in windows for now :(

---

### Post by traveller.ct on 2006-06-12
Filed a bug (#49528) at launchpad.net

---

### Post by JurB on 2006-07-29
It's a kernel bug, you can fix it by doing
```

$ sudo modprobe -r bt878 bttv
$ sudo modprobe snd_bt87x
$ sudo modprobe bt878
```

---

### Post by traveller.ct on 2006-08-01
I suggest you submit this piece of information on lauchpad (bug #49528) so they have the information to fix it (hopefully by 6.10!).

---

