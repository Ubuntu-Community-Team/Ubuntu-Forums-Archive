---
title: "Alsa Configuration Save error"
date: 2010-12-01
forum: General Help
---

### Post by dbzkid on 2010-12-01
I am getting an error with alsactl, I am using the nightly snapshots of the alsa driver (my gtx 470 doesn't like the stable alsa drivers for hdmi output. I am also using the Nvidia drivers not the ones provided by the ubuntu repositories). I am just wondering what do I need to do to fix this error

```
kevin@kevin-desktop:~$ alsactl
alsactl: /usr/lib/libasound.so.2: version `ALSA_1.0.12' not found (required by alsactl)
alsactl: /usr/lib/libasound.so.2: version `ALSA_1.0.8' not found (required by alsactl)
alsactl: /usr/lib/libasound.so.2: version `ALSA_1.0.9' not found (required by alsactl)

```

Otherwise I will have to keep unmuting s/pdif in alsa mixer at every boot.

Thanks

---

### Post by dino99 on 2010-12-01
these alsa are outdated, but which ubuntu release are you running ?

you can use synaptic repo tab to update these packages with:

[https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by dbzkid on 2010-12-01
I am running Ubuntu 10.10 and i will try those Repos :D
This is the Repos that I am using:
```
ppa:ubuntu-audio-dev/ppa
```

---

