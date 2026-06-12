---
title: "Spotify under wine not working"
date: 2010-10-17
forum: General Help
---

### Post by danbaark on 2010-10-17
I'm using Ubuntu 10.10 and trying to run Spotify through Wine 1.2 but can't get it to play anything (worked fine on 10.04). I've followed the instructions on the Spotify site but setting the wine audio driver to OSS as recommended cause the audio test to fail. ALSA driver the audio test is fine but in both cases Spotify doesn't play anything (not just no sound but the song doesn't progress).

Any ideas? Thanks a lot for the help!

---

### Post by drr104 on 2010-10-17
Had the same problem after upgrading to 10.10, fixed it by changing the DirectSound hardware acceleration option in winecfg to "Emulation" (using ALSA not OSS).

Hope that helps.

---

### Post by danbaark on 2010-10-17
Weirdly that didn't work for me at first but after a computer restart it's all fine using those settings. Cheers

---

### Post by matt_symes on 2010-10-17
Hi

On their web page you are advised to use emulation.

Has anybody tried their Linux version?

I also run under wine

Kind regards.

---

