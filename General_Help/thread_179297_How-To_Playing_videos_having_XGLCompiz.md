---
title: "How-To: Playing videos having XGL/Compiz"
date: 2006-05-19
forum: General Help
---

### Post by El Menda on 2006-05-19
**Admins please change the place of this topic**. I made a mistake placing it in Warty Warthog. Thanks

This guide goes for those people like me who couldnt watch videos after installing XGL (on Dapper) or they were playing really slow.

1. Install mplayer:```

sudo apt-get install mplayer
```

If it is not found add the multiverse repositories in /etc/apt/sources.list and then sudo apt-get update:
```
deb http://es.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ dapper multiverse

```

2. Go to options in mplayer and change the driver you are using to another one which works well. 
For me it worked the "x11 - XImage/Shm" driver, but for other people the OpenGL is the one which works good.

3. If you cant watch the video in fullscreen mode (you only see black borders),  type:
```
sudo nano /etc/mplayer/mplayer.conf
```
and go to the line which says:
```

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
#zoom=yes
```

The only thing you need is removing the # at the begining of zoom=yes

Now you can play all your videos/DVD's!!! :D

---

### Post by Ubuntuud on 2006-05-19
Sounds simple... Too bad it doesn't work. Have you tried playing a .mov? Or an ASF? They both give me weird outlines around objects (such as a human head) on the video.

btw. why do you place this at warty?

---

### Post by El Menda on 2006-05-19
[QUOTE=Ubuntuud]Sounds simple... Too bad it doesn't work. Have you tried playing a .mov? Or an ASF? They both give me weird outlines around objects (such as a human head) on the video.[/QUOTE]
Hi. I've just tried it with .avi .mpg .m4v .mov which are the most common formats, and it works well.

[QUOTE=Ubuntuud]btw. why do you place this at warty?[/QUOTE]
Yeah sorry, I had a lot of windows opened and I clicked on New Thread in the wrong place ](*,)

---

### Post by FedeXX on 2006-09-16
Elmenda, you are my heroooooooo! :biggrin: Thank you!

The X11 driver works better than the Opengl one, which on my laptop works only in fullscreen, and not so well (a couple of white frames each minute). With the zoom option enable the X11 driver works great in fullscreen too, and my cpu is much more "relaxed".

A little advice: switch to on the "enable frame dropping" option in mplayer to keep a good audio/video synchronization.

Thanks again!

---

