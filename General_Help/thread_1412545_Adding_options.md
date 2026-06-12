---
title: "Adding options"
date: 2010-02-21
forum: General Help
---

### Post by cool-blue on 2010-02-21
Greetings, i'm new to Ubuntu and i'm just trying to get the sound working on my laptop

I found a solution online

'Sound:
add
options snd-hda-intel model=dell-m6
to /etc/modprobe.d/alsa-base.conf.'

Although i'm not sure how to do this, can someone please explain?

Thanks in advance,

cool-blue

---

Solution found at: 'http://www.rschulz.eu/2009/11/dell-studio-1557-core-i7-with-kubuntu.html'

---

### Post by r2s2 on 2010-03-01
Try:

echo "options snd-hda-intel model=dell-m6" | 
sudo tee -a /etc/modprobe.d/alsa-base.conf

Alternative choose your favorite text editor.

Glad you find my page ([www.rschulz.eu](www.rschulz.eu)) helpful.

---

