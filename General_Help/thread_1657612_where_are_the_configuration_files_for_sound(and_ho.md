---
title: "where are the configuration files for sound?(and how do i change them?) (pulse audio)"
date: 2011-01-01
forum: General Help
---

### Post by chriskin on 2011-01-01
i want to make a script to change the sound configuration from "balanced right/left and low volume" to "louder right speaker and louder volume" and back.

i want to learn where i can find the configuration file and what command i have to use to restart pulse audio after my script changes the file.

(if you can also tell me what the changes have to be to get the above mentioned results , i will send you a tasty popcorn emoticon :D)

---

### Post by solar george on 2011-01-01
I'd suggest you look into pactl and pacmd (from the [pulseaudio-utils]("apt://pulseaudio-utils") package) to change pulseaudio options without reloading pulseaudio and that their website might be the best place to work out what options you need for the commands (also try using the man pages).

---

