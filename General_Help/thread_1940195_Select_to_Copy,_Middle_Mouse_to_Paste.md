---
title: "Select to Copy, Middle Mouse to Paste"
date: 2012-03-13
forum: General Help
---

### Post by HOLOGRAPHICpizza on 2012-03-13
One thing that I miss from some old experiences with Unix and X is being able to simply select text to copy it and use the middle mouse button to paste.

Any idea how to enable this behavior in Ubuntu 11.10 / Xfce4?

---

### Post by Bucky Ball on 2012-03-13
Well, I'm using 10.10 with Xfce and that's exactly what it does. I just select the text I want to paste and hit the scroll wheel and I'm done. I haven't used any tweaks to make this so; it has always been that way. ;)

Maybe it's a peculiarity of 11.10. What's the brand of the mouse? You might want to have a browse here:

[http://au.search.yahoo.com/search;_ylt=A0oGkmQuK19PBhQAPS4L5gt.?p=scroll%20wheel%20to%20paste%20ubuntu%2011.10&fr2=sb-top&fr=altavista&rd=r1](http://au.search.yahoo.com/search;_ylt=A0oGkmQuK19PBhQAPS4L5gt.?p=scroll%20wheel%20to%20paste%20ubuntu%2011.10&fr2=sb-top&fr=altavista&rd=r1)

---

### Post by timgood on 2012-03-13
I'm using 11.10 (64bit) and it works the way it has always worked. Must be something peculiar to your set up?

---

### Post by Bucky Ball on 2012-03-13
> **timgood said:**
> Must be something peculiar to your set up?

+1. That's my guess, too. What brand mouse?

---

### Post by sudodus on 2012-03-13
It works by default (but you can tweak your mouse settings) in xubuntu, and I think it does also in 'vanilla' ubuntu.

Have you installed xfce in 'vanilla' ubuntu? There is also an option to install xubuntu-desktop
```
sudo apt-get install xubuntu-desktop
``` that should give you a more complete desktop environment.

---

### Post by Bucky Ball on 2012-03-13
> **sudodus said:**
> It works by default (but you can tweak your mouse settings) in xubuntu, and I think it does also in 'vanilla' ubuntu.

Have you installed xfce in 'vanilla' ubuntu? There is also an option to install xubuntu-desktop
```
sudo apt-get install xubuntu-desktop
``` that should give you a more complete desktop environment.

Perhaps, but there is no control to tweak the mouse in the way the OP wants there. Why clog a vanilla install (or any other) with unwanted xubuntu packages dragged in by installing xubuntu-desktop???

This is something to do with the OP's particular configuration, hardware/software. I have exactly the same setup (Ubuntu using Xfce4) on a couple of machines and this is not an issue. Same for timgood and he/she is using 11.10 with xfce4, as the OP is. ;)

---

### Post by aeiah on 2012-03-13
im guessing this is a mouse/X issue rather than anything to do with xfce or any other desktop environment.

does shift+insert work instead of middle-click? if so, its only half broken ;) you could try and see what xev outputs for your mouse buttons i guess, or see if there's something peculiar with your mouse.

left and middle buttons are button 1 and button 2 respectively

---

### Post by sudodus on 2012-03-13
> **Bucky Ball said:**
> Perhaps, but there is no control to tweak the mouse in the way the OP wants there. Why clog a vanilla install (or any other) with unwanted xubuntu packages dragged in by installing xubuntu-desktop???

This is something to do with the OP's particular configuration, hardware/software. I have exactly the same setup (Ubuntu using Xfce4) on a couple of machines and this is not an issue. Same for timgood and they are using 11.10, exactly as the OP is. ;)
@Bucky Ball
Glad to read that the OP's problem is *not* because of 'only' xfce! By the way, why are you running Ubuntu like this instead of Xubuntu? I guess you have some very good reasons.

But where's the pizza, I'm getting hungry ;-)

---

### Post by HOLOGRAPHICpizza on 2012-03-13
Ahhh, thank you all, my middle mouse button was simply not working. haha Thanks though! xD

---

