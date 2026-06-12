---
title: "Ubuntu is running in low graphics mode..."
date: 2010-06-20
forum: General Help
---

### Post by JThompson118 on 2010-06-20
(Consider yourselves forewarned: I'm completely new and will be incredibly stupid. Give me slack. :P)

So I'm trying to run my S-Video cord from my HP Desktop to my television screen. Everything was set up, then I looked up how to get it to start playing on forums here. I went to my NVIDIA, and when I went to change what apparently had to be changed, it was already set up in the format I was supposed to set it up as. I hit "save", and then restarted my computer, as the step-by-step instructions said. Upon restarting, I got an interesting message saying that Ubuntu had to be run in low graphics mode. I don't know the logistics of my computer, or really anything (it was given to me, and I don't know how to check :P) I've been reading some things here, and a few things sounded like what was wrong with me, but when I followed the directions, it got me no where. I'm coming to you to prevent me from chucking this thing out my window :P. 

So, what I'm asking from you:

1)How do I get out of Low Graphic Mode
2)How do I set up my NVIDIA to play to my TV?

Thank you!

---

### Post by dim3000 on 2010-06-20
> **JThompson118 said:**
> (Consider yourselves forewarned: I'm completely new and will be incredibly stupid. Give me slack. :P)

So I'm trying to run my S-Video cord from my HP Desktop to my television screen. Everything was set up, then I looked up how to get it to start playing on forums here. I went to my NVIDIA, and when I went to change what apparently had to be changed, it was already set up in the format I was supposed to set it up as. I hit "save", and then restarted my computer, as the step-by-step instructions said. Upon restarting, I got an interesting message saying that Ubuntu had to be run in low graphics mode. I don't know the logistics of my computer, or really anything (it was given to me, and I don't know how to check :P) I've been reading some things here, and a few things sounded like what was wrong with me, but when I followed the directions, it got me no where. I'm coming to you to prevent me from chucking this thing out my window :P. 

So, what I'm asking from you:

1)How do I get out of Low Graphic Mode
2)How do I set up my NVIDIA to play to my TV?

Thank you!

Please link to which instructions you used, also you did not state any actual info so:

a) Check "Hardware Drivers" make sure nVidia current version is enabled and activated!

b) goto a terminal, and provide output of this command:
```
lspci | grep VGA
```

c) in a terminal, do this: 
```
cat /var/log/Xorg.0.log > Xorg.log
```
upload the created Xorg.log file contents using:
 [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Provide the link to the paste.

---

