---
title: "How to drag a window?"
date: 2010-11-06
forum: General Help
---

### Post by linux_dream on 2010-11-06
I've upgrated to the newest version of Ubuntu (10.10) and now when I press over the temperature/date settings, the window displayed appear too top of my screen so that the upper drag zone is out of my screen.  How can I drag the window down?

---

### Post by uRock on 2010-11-06
Right-click the window's button on the panel, then click move.

---

### Post by lovinglinux on 2010-11-06
..or click ALT and drag by clicking anywhere on the window.

---

### Post by linux_dream on 2010-11-06
I appreciate your help guys, but none of this work.  How do I take a screenshot so that you can see by yourself?  I'm guessing the "print" button on my keyboard, but where do the picture go?

Edit: Found out.  Check upper right section of the picture.  Basically I've tried alt+drag over the whole window, totally stuck window.

---

### Post by Verbeck on 2010-11-06
> **linux_dream said:**
> I appreciate your help guys, but none of this work.  How do I take a screenshot so that you can see by yourself?  I'm guessing the "print" button on my keyboard, but where do the picture go?

after you press print screen, a dialogue box should appear asking where to save the screen shot. also check your desktop

---

### Post by linux_dream on 2010-11-06
> **Verbeck said:**
> after you press print screen, a dialogue box should appear asking where to save the screen shot. also check your desktop
Thanks.  I found out by myself.  Hmm I've uploaded it in jpg file but doesn't seem to work.  I'll try png.

---

### Post by uRock on 2010-11-06
Did you upgrade or clean install 10.10?

---

### Post by linux_dream on 2010-11-06
> **uRock said:**
> Did you upgrade or clean install 10.10?
I upgrade from the previous version (10.04).

---

### Post by linux_dream on 2010-11-06
Is my screenshot posted in post #6 useful?  This shows the problem I'm having.

---

### Post by mc4man on 2010-11-06
> How can I drag the window down?
You can't - the pop out from the clock applet is non-movable.

Where is the applet?, on a side panel?
If so then you need to move the applet down on the panel - it will pop out w/ location at top so you need to give it room at the top

(as mentioned - r. click on the applet - move

(or run it from a top or bottom panel

---

### Post by linux_dream on 2010-11-07
> **mc4man said:**
> You can't - the pop out from the clock applet is non-movable.

Where is the applet?, on a side panel?
If so then you need to move the applet down on the panel - it will pop out w/ location at top so you need to give it room at the top

(as mentioned - r. click on the applet - move

(or run it from a top or bottom panel
Oh I see.
The problem is that it's already in the bottom panel.  In my screenshot you can see the part that has been selected.  It's where one sees "32°C  sáb 6 de nov, 19:09".
So if I get it right, there's no cure?

---

### Post by lovinglinux on 2010-11-07
> **linux_dream said:**
> Oh I see.
The problem is that it's already in the bottom panel.  In my screenshot you can see the part that has been selected.  It's where one sees "32°C  sáb 6 de nov, 19:09".
So if I get it right, there's no cure?

Remove the applet from the panel and add it again. If that doesn't work, I would recommend deleting all your panels and start over. This must be a bug or a problem with the config files. Resetting the panels should take care of that.

---

### Post by linux_dream on 2010-11-07
> **lovinglinux said:**
> Remove the applet from the panel and add it again. If that doesn't work, I would recommend deleting all your panels and start over. This must be a bug or a problem with the config files. Resetting the panels should take care of that.
I've just deleted my bar and manually added all the elements I had.  When I first clicked on the "clock" the problem seemed solved: it poped up at the top of my screen but not out of my screen.  However I couldn't move it.  If I remember well, in the previous version of Ubuntu I could move it like a normal window.
Then the worst happened: when I closed and clicked again, the same problem appeared.  It's out of my screen.  
I guess I should give up?

---

### Post by mc4man on 2010-11-08
> I guess I should give up?
There does seem to be an issue when running the clock applet from the bottom screen. Here it doesn't go off screen but does start in the upper half and when location is expanded gets near the top.

If you have no visual effects enabled then it starts off of the bottom panel like would be expected.

What you need is possibly someone who know compiz - don't really use it here except for scroll on desktop (cube.

Was able to adjust it's position thru comizconfig settings manager -> place windows as in screens. The values shown (x.y.) moved it to the very bottom right corner on a small laptop, what works for you may/would be different.

Note this was a guess on how to do, you may wish better advice.

The position change is not reflected in 'real time' so you need to close the applet, adjust the values, reopen to check ect.
If trying I'd start at 0,0 and see where that is then adjust.

**Word of warning** - do not create an undefined named window position (name=) and whatever you do make sure the "Keep In Workarea"  is checked.

Otherwise you can easily end up with all your windows opening offscreen which is quite an interesting situation and one you'll want to avoid

---

### Post by linux_dream on 2010-11-08
Thanks a lot mc4man.  I've choose the same values as you did and it ended perfectly.  I would have never guessed how to work it out alone.  
I'll mark the thread as solved.

---

