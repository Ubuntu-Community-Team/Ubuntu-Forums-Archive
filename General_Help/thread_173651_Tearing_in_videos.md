---
title: "Tearing in videos"
date: 2006-05-10
forum: General Help
---

### Post by Biffy on 2006-05-10
This is hard to explain but i will try as good as i can:

I am using TV-OUT. If i play a video so i can see it on my TV, there will be tearing in the picture. This can be fixed by using the vidix driver, it takes away the tearing, but when using fglrx, there is only a pink window where the video should be. Not on my monitor, but on my TV. If i use vesa as a video driver in X, it works fine.

So this means if i want a good rendered video, i must shutdown X and enable vesa in xorg.conf. I want to know either how to fix the issue with the pink screen, or a video driver that eliminates tearing. I have tried Xine with the openGL driver, but the tearing is still there. 

Any ideas?

---

### Post by the_tiger on 2006-05-10
The tearing sounds to me like a problem associated with refresh rate. Is there nowhere in the config files to modify the output rate of your tv socket?

---

### Post by Biffy on 2006-05-11
[QUOTE=the_tiger]The tearing sounds to me like a problem associated with refresh rate. Is there nowhere in the config files to modify the output rate of your tv socket?[/QUOTE]

When i am using the vidix driver, there is no tearing, so i don't think refresh rate is the problem here.

---

### Post by Biffy on 2006-05-24
I can't solve this! Im using the gl2 driver. And when playing videos in fullscreen i get the tearing. When this is happening in games there is a option called vsync that removes the tearing. Is there a vsync option in mplayer?

---

