---
title: "Very Low sound in ubuntu 12.04"
date: 2012-05-03
forum: General Help
---

### Post by ankit.vader on 2012-05-03
I've installed ubuntu 12.04(new installation) and noticed that sound is very low. I can barely listen max volume. This was not a problem with ubuntu 11.10. 
I have checked sound settings and they are fine.
All i did after installation was, to install codecs for running mp3, avi, mkv, flv etc.
I've lenovo y500.

---

### Post by ankit.vader on 2012-05-04
bump

---

### Post by merlinus on 2012-05-04
FWIW, I had this problem with 11.10, and no matter what I tried, could not fix it.  Now that I installed 12.04, the sound volume works fine.  Your only recourse may be to reinstall.

---

### Post by guestolo on 2012-05-04
In terminal, if you type in **alsamixer**
Are master, pcm, etc... volumes set properly?

---

### Post by ankit.vader on 2012-05-05
> In terminal, if you type in alsamixer
Are master, pcm, etc... volumes set properly?

thanks, apparently some other sound card was selected, when i selected correct sound card problem was solved.

---

### Post by drunksaint on 2012-08-26
> **ankit.vader said:**
> thanks, apparently some other sound card was selected, when i selected correct sound card problem was solved.

even i have a y500 and have the same volume problem. i looked in alsamixer and found just one sound card. is there something i'm missing?

---

### Post by drunksaint on 2012-08-31
bump

---

### Post by justoboy on 2012-12-08
can someone help me? i upgraded to 12.10 from 11.10 and now my sound is very low. [ATTACH]228403[/ATTACH]

---

