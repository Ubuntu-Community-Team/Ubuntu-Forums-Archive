---
title: "basic video driver problem..."
date: 2006-06-13
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-13
hey all, I don't really have any video accelleration on my laptop anymore... its weird. anyways when I do fglrxinfo 

```

eclypse@Eclypse:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


```
indicating that I have no video acceleration, how do I fix this again? I kind of forgot. also, I only get 200fps in glxgears, and it looks even less then that, but anyways, I got 1700 when the video drivers were actually working. 

thanks to all that reply.

---

### Post by RudolfMDLT on 2006-06-13
Mesa is just a rescue driver when your current driver doesn't work. You are probally using ATI?

Check out the following links:
[https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29](https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29)
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
[http://www.ubuntuforums.org/showthread.php?t=195845](http://www.ubuntuforums.org/showthread.php?t=195845)

For Nvidia:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)
[http://ubuntuforums.org/showthread.php?t=195065&highlight=Setup+Nvidia](http://ubuntuforums.org/showthread.php?t=195065&highlight=Setup+Nvidia)

---

### Post by Patrick-Ruff on 2006-06-13
ok, yeah I was using ATI drivers and all that, I'de prefer a quick answer rather then a link, since I'm on dialup and its insanely slow...


but thanks anyways.

---

### Post by RudolfMDLT on 2006-06-14
[QUOTE=Patrick-Ruff]ok, yeah I was using ATI drivers and all that, I'de prefer a quick answer rather then a link, since I'm on dialup and its insanely slow...


but thanks anyways.[/QUOTE]


Sorry Patrick,

As I wasn't sure what you where running and as you clearly saw, the answer was not simple! Next time tell me/anyone else that you're on a dailup and we'll just create on huge post for you! :)

---

