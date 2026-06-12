---
title: "ATI drivers... again... sorry."
date: 2010-02-24
forum: General Help
---

### Post by severean0 on 2010-02-24
Hi
Sorry to start (yet another) thread about ATI graphics card drivers but I haven't been able to sort out my problem by searching on it.  

My computer:
9.10 Karmic Koala x86_64
ATI Radeon HD 5850
Core i7 920 etc. etc.

Problem:
The latest official ATI drivers from the AMD website aren't allowing me to enable desktop effects. Previously I have been using official ATI drivers, installed according to their instructions, and they have been working but I had a few issues such as screen tearing and no antialiasing of anything, but generally working. The latest version however, for whatever reason isn't found by the OS, and so I can't enable desktop effects. 

The solution I have tried:
I went to System > administration > Hardware drivers, and installed the proprietary drivers in there, and now everything's fine; the quality of the compiz effects is much improved; antialiasing seems to be working and there are very few vsync issues. Screen tearing is still really bad in alien arena, but the graphics seem to be antialiased at least, which is a start. HD video and flash support are fine. The problem now is that I have lost the ATI catalyst control centre, and have gained a very annoying "AMD unsupported hardware" logo permanently emblazoned on the bottom right hand corner of the screen. 

Question is how can I get rid of the annoying logo, keep antialiasing, get rid of vsync issues, and preferably retain the catalyst control centre...? 

There seems to be a third route which I haven't tried; [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) 
but I don't even know where to start with that. 

Any suggestions?
Many thanks, and sorry, again.

---

### Post by severean0 on 2010-02-24
Edit: I lied, under the current config, with Proprietary drivers installed (using system>admin>hardware drivers), although compiz effects are silky smooth, antialiased and perfect, fullscreen HD video is choppy with lots of screen tearing, and moonlight fullscreen performance is very poor...

---

### Post by drdanielfc on 2010-02-24
Did you perform the extra x64 steps?

---

### Post by severean0 on 2010-02-26
> **drdanielfc said:**
> Did you perform the extra x64 steps?

No... I'm not aware of them..?

---

### Post by drdanielfc on 2010-02-26
> **severean0 said:**
> No... I'm not aware of them..?

Deactivate fglrx in hardware drivers then follow the tutorial on the website you posted....there were a couple extra steps for x64 ;)

---

