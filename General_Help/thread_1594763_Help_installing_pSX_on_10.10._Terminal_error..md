---
title: "Help installing pSX on 10.10. Terminal error."
date: 2010-10-12
forum: General Help
---

### Post by ThePhysician on 2010-10-12
I've managed to extract pSX to /home/xan/Games/pSX and then pSX would do nothing when clicked on, so I tried launching it from the terminal and found out I had to install libgtkglext-x11, which I did from the package manager.

Now upon trying to run it from the terminal again I get the following error:

```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Any idea what this means?

---

### Post by jvhellraiser on 2010-10-12
Did you try install it from ubuntu software center?

if is not there try to find a deb file.

[http://www.megaupload.com/?d=2BXQ76DA](http://www.megaupload.com/?d=2BXQ76DA)

---

