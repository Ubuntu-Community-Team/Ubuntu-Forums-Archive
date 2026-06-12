---
title: "no audio, help please"
date: 2011-04-21
forum: General Help
---

### Post by storm1990 on 2011-04-21
i have a hp pavilion g6 series can anyone help me figure this out i have no audio

---

### Post by anieruddha on 2011-04-21
I had problem with my vaio laptop. To solve the problem u need to download latest alsa driver source code. ([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)) and do installation.
user command (./configure && make && make install). Before installation please check your sound card is supported ([http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main))

After that just run alsamixer.

Restart computer.

---

### Post by storm1990 on 2011-04-21
> **anieruddha said:**
> I had problem with my vaio laptop. To solve the problem u need to download latest alsa driver source code. ([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)) and do installation.
user command (./configure && make && make install). Before installation please check your sound card is supported ([http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main))

After that just run alsamixer.

Restart computer.

i think its supported , how would i find the source code a amd

---

