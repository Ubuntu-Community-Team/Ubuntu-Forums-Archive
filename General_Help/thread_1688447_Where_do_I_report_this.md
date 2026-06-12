---
title: "Where do I report this?"
date: 2011-02-15
forum: General Help
---

### Post by VcDeveloper on 2011-02-15
I have several of these in my user.log and it tell me to report it.  So what forum or website do I report this?

```
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-util.c: Disabling timer-based scheduling because running inside a VM.
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-util.c: Disabling timer-based scheduling because running inside a VM.
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-source.c: ALSA woke us up to read new data from the device, but there was actually nothing to read!
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-source.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Feb 10 17:23:10 anointed-webd7 pulseaudio[1468]: alsa-source.c: We were woken up with POLLIN set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

```

---

### Post by Mad dog on 2011-02-15
[https://bugtrack.alsa-project.org/alsa-bug/login_page.php](https://bugtrack.alsa-project.org/alsa-bug/login_page.php)

---

### Post by VcDeveloper on 2011-02-16
Thanks!

---

