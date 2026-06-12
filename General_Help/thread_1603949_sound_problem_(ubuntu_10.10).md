---
title: "sound problem (ubuntu 10.10)"
date: 2010-10-23
forum: General Help
---

### Post by kurci2 on 2010-10-23
hi!
i have a strange problem.
i own toshiba satellite a660 laptop. A fresh install of ubuntu 10.10 works great, but i have a sound problem. Sound only works with headphones. No sound is played through speakers.
What should i do??
Install any third-party driver?
I'm a bit desperate...

thanks for any help!!

---

### Post by Deecie on 2010-10-23
I had the same problem, and solved it by running "alsamixer" from a terminal. It turned out that the speakers were muted by default; hopefully your problem is equally trivial, as even that took me a while to figure out.

---

### Post by kurci2 on 2010-10-23
hmm...
i uploaded a printscreen of alsamixer
i thing everything is ok, but still no sound

---

### Post by kurci2 on 2010-10-23
i have an extra problem.
i tried to install Realtek High Definition Audio Codecs, but i get an 109 error saying that alsa was not found...

---

### Post by Volens on 2010-10-23
Try checking /etc/modprobe.d for a file called alsa-base.conf. You may need to add another line for your audio card. Try checking the alsa website matrix (just google "alsa matrix"). I think it has the lines you might need to add. Its usually something along the lines of ```
options snd-hda-intel model=mobile
```

I don't know if this will work, but I had a mic issue recently and it had to do with the configuration of my sound card on my laptop. It seems laptop cards can sometimes be picky.

I would look for you, but I don't know what audio card you have.

---

