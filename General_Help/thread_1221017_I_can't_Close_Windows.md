---
title: "I can't Close Windows"
date: 2009-07-23
forum: General Help
---

### Post by Virtualbox on 2009-07-23
Alright, so today I started messing around with dual screening my laptop (presario R3000) which runs ubuntu. I downloaded EnvyNG, and something with the program went wrong. It asked for a restart which I did, and then the screen resolution went down. So... I deleted that program and typed in "sudo nvidia-xconfig" to switch back to my origional nvidia graphics card installed on my computer. It restarted again and everything went back to normal... Except, now the bar on top of each window is gone! The bar with minimize, maximize, and X (for closing the window) I can't figure out what to do.. Btw... I have compiz fuison running, and a nvidia graphics card. PLEASE HELP!

---

### Post by wojox on 2009-07-23
You could change Visual Effects to none.

Or 

Use Alt+spacebar to minimize, maximize and close windows.

---

### Post by Virtualbox on 2009-07-23
Are there any other ways. I tried setting the visual effects to none, but then right when I turn it to Extra or normal, the bar I was talking about earlier disappears. And don't you need to set it to extra for compiz fusion? I think that's the way it was before. Any other help would be appreciated, and thank you wojax for at least getting my minimize, maximize, and exit bar back by having me set the desktop effects to none.

---

### Post by 3rdalbum on 2009-07-23
The "title bar" is drawn by the window manager. If you set the effects to "None", then you are actually switching to the non-composited, Metacity window manager.

When you change the visual effects setting, it switches your window manager to Compiz. If something goes wrong with Compiz and causes it to crash, then there's nothing running to draw the title bars of your windows.

Open the Appearance program and go to the Visual Effects tab. Set it to None. Now open a terminal and type the following:

```
compiz --replace
```

If there are problems with Compiz loading, you will see error messages being printed to the terminal. After they end, you can click "None" in Appearance and Metacity will be loaded again.

Post those error messages here and we can try and help you. It sounds like a graphics driver problem.

---

### Post by Virtualbox on 2009-07-23
Thanks 3rdalbum... I tried that, and what happened is it kind of reset my screen, then the title bars went away on each window, then the terminal window went all white, with no outline or anything. So I went back into the visual effects screen, and turned it to "none" Then the terminal window showed up... I got this same repeating message: 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x2000046 to texture

It repeated about 10-15 times, weird... so you said it may be a graphics card driver error or something? What can I do to get it back to normal? Thanks for all your guys help! If any information is needed from me, just post another reply here. THANKS!

---

### Post by Strongman332 on 2009-07-23
hit "e" at the grub screen when you boot. select the safe graphics option. then hit "b" to boot. when it asks you want it to reconfigure x server(it may say x-11 i dont remember) select automatic. it should boot and every thing be ok. then restart again to be sure

---

### Post by Virtualbox on 2009-07-23
> **Strongman332 said:**
> hit "e" at the grub screen when you boot. select the safe graphics option. then hit "b" to boot. when it asks you want it to reconfigure x server(it may say x-11 i dont remember) select automatic. it should boot and every thing be ok. then restart again to be sure
 
THANK YOU STRONGMAN!!! (yes caps ARE necessary) 
wow, I did just that and it worked! ugh, I'm so happy, too long working on this... Thank you to everybody who offered suggestions. God I love ubuntu and their support! Again, Thanks!

---

