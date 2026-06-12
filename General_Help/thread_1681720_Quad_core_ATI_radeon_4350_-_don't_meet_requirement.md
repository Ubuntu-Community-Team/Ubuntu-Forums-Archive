---
title: "Quad core ATI radeon 4350 - don't meet requirements"
date: 2011-02-04
forum: General Help
---

### Post by AdamGM on 2011-02-04
Greetings!

I'm attempting to install WoW via wine, and when I run the installer I am told my hardware doesn't meet the requirements.

Obviously something is wrong, but I'm really not sure what to do.  

Thanks in advance!
-Adam

---

### Post by mikewhatever on 2011-02-04
Have you installed the proprietary ATI graphics driver? It should be available under System->Admin->Additional Drivers.

---

### Post by AdamGM on 2011-02-04
Thanks for the reply.

I have since installed the propietary drivers as you described. It doesn't seem to have worked properly - when I launch wow and check out the video settings, it's set on low with the red bar going through the rest of it, indicating I can't move it up.

With my setup I should be able to nearly max them I would think. I did insert the opengl code into the config.wtf.

Edit: possibly worth noting that it changes my resolution a great deal when I launch wow. There is a large black banner all the way around my screen from the resolution changing so much.

---

### Post by AdamGM on 2011-02-04
I'm also not sure why, whenever I launch wow from Wine, it makes a new wow shortcut (icon) on my desktop..

---

### Post by mikewhatever on 2011-02-05
Hi again, 
I am no wine or WoW expert, in fact, had never used the two. Hopefully someone with the first hand experience will chime in, meanwhile, take a look at the WoW page at winehq.org.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

---

### Post by khelben1979 on 2011-02-05
One thing which is important to note here is that the graphic settings will not match what you'll get on a Windows system with your hardware, because Wine uses [OpenGL]("http://en.wikipedia.org/wiki/Opengl") instead of [DirectX]("http://en.wikipedia.org/wiki/Directx").

I think if you're using the latest version of Wine you will have the best possible results. It's easy to compile Wine from source if the newest package is not available.

If the ATi non-free driver is working, there is no solution for you to be able to use higher settings for your current graphic card.

---

