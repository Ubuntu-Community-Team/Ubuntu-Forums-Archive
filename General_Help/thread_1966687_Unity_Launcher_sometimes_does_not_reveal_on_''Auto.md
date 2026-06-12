---
title: "Unity Launcher sometimes does not reveal on ''Autohide' mode after upgrading to 12.04"
date: 2012-04-27
forum: General Help
---

### Post by kwanylongy on 2012-04-27
Hi all,

After upgrading 12.04, my Unity Launcher sometimes does not reveal itself when my mouse cursor is moved to the left-handside of the screen. The 'reveal location' of my Unity Launcher is set to 'left' so it definitely isn't that that is causing the problem. I find this extremely annoying and it wasn't as such in 11.10... is this a bug?

I have made a video to show the problem, available [here]("http://www.youtube.com/watch?v=ob8XtVoucVA&feature=youtu.be").

Thanks in advance! :p

Carlos

---

### Post by compmodder26 on 2012-04-27
Have you set the reveal sensitivity to the highest setting?  You can do so through the Appearance settings.  I've noticed that even with the sensitivity set as high as it will go, I have to keep moving my cursor to the left (even after I'm already to the far left edge) before the launcher will reveal.

---

### Post by kwanylongy on 2012-04-27
Thanks for your reply

I did set the sensitivity to the highest when I made the video.

It seems that the launcher only reveals itself when the mouse cursor hits the left side at high speed

---

### Post by kwanylongy on 2012-04-28
Solved it!

The 'unresponsiveness' of the Unity launcher is designed to be this way. 
To fix it, go to Compiz Manager -> Unity Plugin -> Experimental, set 'Launcher Reveal Pressure' to its minimal value (which is 1).

---

### Post by TurtleKing on 2012-04-28
> **kwanylongy said:**
> Solved it!

The 'unresponsiveness' of the Unity launcher is designed to be this way. 
To fix it, go to Compiz Manager -> Unity Plugin -> Experimental, set 'Launcher Reveal Pressure' to its minimal value (which is 1).

More like a work-around, but I will take it.

Thanks.

---

