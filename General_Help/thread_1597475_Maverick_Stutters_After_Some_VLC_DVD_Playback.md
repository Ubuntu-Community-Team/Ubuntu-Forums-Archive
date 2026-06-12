---
title: "Maverick Stutters After Some VLC DVD Playback"
date: 2010-10-15
forum: General Help
---

### Post by powerofpi on 2010-10-15
Please move this to the appropriate subforum; although VLC playback triggers it, I suspect it's actually a kernel problem. After moving from 10.04 x64 to 10.10 x64, I've been noticing the following problem:

When watching a DVD .iso using VLC Media Player, the system will  become "jerky" and "stutter" after a random amount of smooth playback. At that point, the only way to make the system smooth and responsive again is a hard restart (normal shutdown hangs and refuses to complete).

Any ideas where I can start looking to find where the bug lies? My laptop is an Acer Aspire 6930 with 10.10 x64 and the current NVidia display driver.

---

### Post by powerofpi on 2010-10-15
Note that I can close VLC after the issue occurs and verify that the process is no longer running, but the system still is glitchy from that point forward. No running process is eating up tons of cpu time either.

---

### Post by lancest on 2010-10-17
10.10 64 bit
Also noticed system freeze up problem when playing .avi with VLC.
Desktop pc

---

### Post by normit08 on 2010-10-17
i did this and it fixed my jerky video and audio.

> Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
Code:

```
load-module module-udev-detect
```

It should look like this:
Code:

```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


---

### Post by sendblink23 on 2010-10-17
> **lancest said:**
> 10.10 64 bit
Also noticed system freeze up problem when playing .avi with VLC.
Desktop pc

Works 100% fine over here, tested with my ATI cards & as well tested with my Nvidia card... all seems fine with many movies on file formats of avi & mkv

only issue with VLC is with ATI(screen flashes black before playing any video) but it works fine afterwards

As for the OP... well its been a while since I've played a DVD movie.. so no clue I can't test it(dont own any right dvd movies now)

---

### Post by TheCommissar on 2010-10-25
This may be an incredibly n00by question, but I can't edit the default.pa file. How do I make it not read-only?

---

### Post by KingofKnights on 2010-11-14
type:  sudo nano /etc/pulse/default.pa  in the terminal window, make changes, and then exit using ctrl+X

---

### Post by James78 on 2010-11-14
If that actually makes my audio not stuttery/skippy, I'll be happy. We'll see...

---

