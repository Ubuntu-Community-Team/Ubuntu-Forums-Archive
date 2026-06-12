---
title: "Audio skipping in Java application"
date: 2011-01-18
forum: General Help
---

### Post by kaldor on 2011-01-18
I just installed Ubuntu 10.10 last evening and all has been going well. Lucid didn't work out for me, so I used other distros. 10.10 fixed all issues except one thing.

This is a need for me; e-courses I take require that I use Elluminate Live, a Java-based conference software. It runs flawlessly on every distro except Ubuntu. I had to use another PC running a different distro in order to get to a class. I really don't want to do that all the time.

I thought it may be OpenJDK, but I found that Sun Java was installed and in use (I installed the extras while installing). I tried OpenJDK (worth a shot eh?) and the exact issue persists.

All other programs have perfect audio.

---

### Post by kaldor on 2011-01-18
I found a solution for this (I am in class right now, maybe this will help others someday!)

In Elluminate, go to Tools > Preference > Speaker Settings. Turn down the Sample Rate.

This worked for me.

---

### Post by dmaxel on 2011-01-21
Thank you so much!!! I've been having problems with this in Ubuntu (and I think Fedora too, but Arch was flawless.) It seems setting it from 44100 to 48000 seems to fix it too. At least for me it does. Finally, a fix!! :D

---

