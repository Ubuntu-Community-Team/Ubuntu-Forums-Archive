---
title: "no sound on lenovo y530"
date: 2009-07-21
forum: General Help
---

### Post by pianodreamer on 2009-07-21
I am using a customized installation of ubuntu 9.04. I used an alternate disk to install a 64bit command line system, and then installed xorg and fluxbox separately.

on my previous laptop, I did the same thing, and sound worked fine after running: ```
$ sudo chmod 775 /dev/snd/*
```

this time on my new laptop, I still have no sound.

When I open the gnome-alsamixer, it is empty. If I go up to edit, then sound card properties, gnome-alsamixer crashes.

here is some information about my system:

```

$ uname -a
Linux orangecat 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Motorola Si3054
Codec: Intel G45 DEVCTG

```

I've tried searching google and the ubuntu forums, and have found people with similar problems, but so far the solutions have not worked.

---

