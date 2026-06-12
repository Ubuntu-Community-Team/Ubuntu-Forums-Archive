---
title: "xine-check (DVD playback issue)"
date: 2006-02-05
forum: General Help
---

### Post by Wolfbite on 2006-02-05
I've installed gxine, and enabled the dma,  and now my DVDs are playing with both sound and picture. However, while it runs pretty nice, it's not smooth enough. There's still some blur, which is very noticable when there's fast action onscreen, and it really hurts my eyes. 

Now, for some reason, when I try to write xine-check or xine-whatever, my terminal says: xine: command not found. Which is driving me nuts. I can't even check anything. Can anyone help me with this?

At the same time, I would appreciate help as to how I can get rid of the damn blur. :)

---

### Post by ronmarley1 on 2006-02-05
I don't know if it will help, but have you tried totem-xine instead of gxine?  I had a few issues with gxine and switched to the totem front-end and now it works fine.
I'm not sure what to do with the ckecking problems.
Go Seahawks!

---

### Post by Wolfbite on 2006-02-06
[QUOTE=ronmarley1]I don't know if it will help, but have you tried totem-xine instead of gxine?  I had a few issues with gxine and switched to the totem front-end and now it works fine.
I'm not sure what to do with the ckecking problems.
Go Seahawks![/QUOTE]

As of now, totem won't even play my DVD's, haha. ^^ I use PowerDVD in Windows, and it's so awesome to use. I wish I could use it in Ubuntu too. :(

---

### Post by ronmarley1 on 2006-02-06
Have you tried Totem with Xine as opposed to Totem with the default GStreamer?

---

### Post by dcstar on 2006-02-06
[QUOTE=Wolfbite]I've installed gxine, and enabled the dma,  and now my DVDs are playing with both sound and picture. However, while it runs pretty nice, it's not smooth enough. There's still some blur, which is very noticable when there's fast action onscreen, and it really hurts my eyes. 
.......[/QUOTE]
I have noticed that DVD playback seems to be better on my system now that I have managed to enable Hardware Video Acceleration.

glxinfo will tell you if your system has direct rendering enabled.

---

