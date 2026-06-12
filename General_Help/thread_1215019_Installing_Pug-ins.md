---
title: "Installing Pug-ins"
date: 2009-07-16
forum: General Help
---

### Post by Cecil Ennett on 2009-07-16
I have been trying to view internet movies, but I can't view any. I have installed, I thought, the plug-ins for my browser, still no luck. Is there any help in this area? I would appreciate it.

---

### Post by starcraft.man on 2009-07-16
> **Cecil Ennett said:**
> I have been trying to view internet movies, but I can't view any. I have installed, I thought, the plug-ins for my browser, still no luck. Is there any help in this area? I would appreciate it.

If by movies you mean stream video, it depends on the stream. I generally use VLC, I think it handles most things. First please make sure you've installed all the codecs you need with the following:
```

sudo apt-get install ubuntu-restricted-extras totem-mozilla
```

Then, I'd advise you to install the non-native codecs for windows formats from medibuntu. Please read guide [here]("https://help.ubuntu.com/community/Medibuntu"). Please read sections 1-4, then after adding the repository, please skip to section 7 to install the codecs. You may also want to install the dvdcss libraries in section 6 if you want but it's not related to streaming.

Then, I'd suggest you try the stream again, by now, totem (the default video player with mozilla plugin) should be capable of playing the video. 

Also, always helpful if you post link to stream in question so we can simply know what format it's in and how to support. If you have trouble after my advice, that is what I'd ask you to do and then well try to further diagnose the trouble.

---

