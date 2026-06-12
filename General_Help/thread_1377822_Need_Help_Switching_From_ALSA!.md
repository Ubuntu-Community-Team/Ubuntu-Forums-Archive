---
title: "Need Help Switching From ALSA!"
date: 2010-01-10
forum: General Help
---

### Post by LukeLinux on 2010-01-10
Maybe ALSA works better for other sound cards than my Realtek ALC888 (that's off the top of my head; it may be a slightly different model), but for me, I really need OSS for sound. ALSA will work for a little while, but if there's more than three or four sounds playing at once (a common occurrence in games) it gets fuzzy, and if a few of those sounds don't stop within a couple seconds, sound dies completely. Furthermore, if the sound dies, attempting to exit the program freezes up the system if the program is running in fullscreen.

For certain programs, I've been able to switch them over to only using OSS for sound, and this works perfectly. I was surprised to find that these programs ran almost twice as smooth with OSS as with ALSA...I never would have tied slow graphics to a sound issue. So I'd really like to switch my entire system **away from ALSA **and **over to OSS**. If I can just switch individual programs, that works for me, too. I just need some way to lose ALSA! 

I'm not afraid of using the terminal, so command-line solutions are welcome; I just don't know any way to use it to change a program's affinity for sound system on my own with anything but a GUI.

Thanks!

---

### Post by LukeLinux on 2010-01-10
*bump!

---

### Post by LukeLinux on 2010-01-13
*double bump...

---

### Post by khelben1979 on 2010-01-13
Have you checked in [here]("http://www.4front-tech.com/forum/viewforum.php?f=3&sid=75b9120ab59e58654f48670b919b9c23")?

If you completely just uninstall ALSA from your Linux system you should get rid of it and then concentrate on having a working OSS afterwards.
[URL="http://www.opensound.com/"]
Open Sound System homepage[/URL].

---

