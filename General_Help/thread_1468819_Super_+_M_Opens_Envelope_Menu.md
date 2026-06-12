---
title: "Super + M Opens Envelope Menu"
date: 2010-05-01
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-01
I always bind Super + M to minimize in keyboard shortcuts, but after I bound it and used it, instead of minimizing the current window, it opened the envelope menu.  How can I change this?  I am using Ubuntu 10.04.

---

### Post by spuny on 2010-05-01
system > preferences > Keyboard shortcuts .. scroll down to window management, then you will find Minimize window click on shortcut and press super + M, and it should work!

---

### Post by Joseph Schwenker on 2010-05-01
> **spuny said:**
> system > preferences > Keyboard shortcuts .. scroll down to window management, then you will find Minimize window click on shortcut and press super + M, and it should work!

You just repeated everything that I just said.  I already said that I had gone to keyboard shortcuts and bound it.  After I have bound it, when I use it, it opens the envelope menu instead of minimizing anything.

---

### Post by spuny on 2010-05-01
> **Joseph Schwenker said:**
> You just repeated everything that I just said.  I already said that I had gone to keyboard shortcuts and bound it.  After I have bound it, when I use it, it opens the envelope menu instead of minimizing anything.

Sorry! I told you what I know, anyway I will search for you and if I found something I will let you know..

---

### Post by Joseph Schwenker on 2010-05-05
bump

---

### Post by Joseph Schwenker on 2010-05-06
Hmm... sometimes the shortcut works, and othertimes not.  Could it be related to the [many random problems]("http://www.uluga.ubuntuforums.org/showthread.php?t=1473128") that I am experiencing?

---

### Post by jarg on 2010-05-20
I am really interested in a fix for this. I removed the envelope menu, but now, super+m opens the audio menu (which I need). Anyone know where this configuration is set? Or if there is a simple volume applet so I can remove the entire indicator applet.

---

### Post by Joseph Schwenker on 2010-05-20
What I find interesting is that sometime super m minimizes the window, and sometimes it opens the envelope menu.  It varies from session to session.

---

### Post by jarg on 2010-05-25
Does anyone know how to fix this?

---

### Post by akakingess on 2010-05-25
Just curious, does it work consistently on some windows/apps, and inconsistently on others, or is it just inconsistent across the board? Also, have you checked launchpad.net to see if there is a bug report on it?

---

### Post by jarg on 2010-05-25
I bind super+M as maxmumize in compiz. It seems to be working on this install*.

*I messed up on my last install, be careful with "sudo" kids.

---

### Post by Joseph Schwenker on 2010-05-25
> **akakingess said:**
> Just curious, does it work consistently on some windows/apps, and inconsistently on others, or is it just inconsistent across the board? Also, have you checked launchpad.net to see if there is a bug report on it?

It's inconsistent across the board.  I have not checked launchpad.net yet.

---

### Post by jarg on 2010-05-26
> **jarg said:**
> I bind super+M as maxmumize in compiz. It seems to be working on this install*.

*I messed up on my last install, be careful with "sudo" kids.

Actually nevermind it is just inconsistent.

In Firefox the me menu opens, at least right now.

[https://launchpad.net/bugs/558581](https://launchpad.net/bugs/558581)
Third comment has a workaround I haven't tested yet.

---

### Post by akakingess on 2010-05-26
If you don't mind, let us know if that work around works for you or not, and if so, than mark the thread solved and let others know at least the link to the solution. That's why I love launchpad.net!

---

### Post by jarg on 2010-05-26
I only just now got a chance to look at it closely. Do you know how to use it? Do I replace some file with it or do I run it some how?

---

### Post by akakingess on 2010-05-27
> **jarg said:**
> I only just now got a chance to look at it closely. Do you know how to use it? Do I replace some file with it or do I run it some how?

Wow, to be honest, if you are talking about Ingo's workaround (I too, just now looked at it) it looks like he has rewritten and recompiled an applet. I know I'm not to that level yet, at least not comfortably, and don't know how advanced you are, but that's what it looks like. When he states applet.c or whatever it was, I believe that refers to the source code for it, and the numbers after are referring to line #'s within the code. I don't think that you have to do all that for your situation. Do you use Compiz? I personally don't, I have all effects disabled in order for my machine to run a little more smoothly. I don't know if that would help with your situation or not. Let me know if that was the workaround you were talking about or was there something else that I completely overlooked (known to happen). Either way, good luck, and let us know.

---

### Post by jarg on 2010-05-27
I actually want to disable the menu's shortcut so I can use a compiz effect. I have used super+m for over a year for maxmumize, I refuse to change for my computer—computers must change for humans.

If anyone knows of a volume applet that isn't in the same indicator applet, I could just delete both because the me menu is beyond useless.

That patch is beyond me to implement.

---

### Post by jarg on 2010-06-02
Bump,

Does anyone know what I could replace the me menu with or how to change the shortcut?

---

### Post by akakingess on 2010-06-02
You can always right-click on it and change what it points to, or just remove it, although now that's it's been a few days I will have to re-read the whole thread to see if I can find a better answer. I will check back in about 45 minutes (hopefully, with an answer that will work for ya).

---

### Post by jarg on 2010-06-02
The problem is, the volume, power, and me menu are all in the same indicator for some reason. If I remove it I lose those and can't control the volume on my computer (a useful feature), know how much battery I have left, etc.

I want to remove it, but in my last install I managed to remove only the me menu, but the shortcut then opened the volume applet (a completely illogical behavior IMHO).

Edit, through a process of completely random trial and error of installing random packages in synaptic, I found that if you replace the indicator with "indicator-applet-complete", not sure which repository it is in, it won't respond to the super+M shortcut.

This is a serious screw up on Ubuntu's part, nothing should be so hard coded in that the user has to install an unofficial clone in order to get their computer like it was in the last version.

---

### Post by Joseph Schwenker on 2010-06-12
When I replace it with Indicator Applet Complete, then super + m does nothing, it just types the m key.  Additionally, I like my clock applet to be between the indicator applet and indicator session applet.  I really want all of those applets up there to be unified.

---

### Post by jarg on 2010-06-15
That is actually the effect I wanted for super+M because I then set it to something else in compiz fusion.

I don't know how to fix that, Ubuntu screwed up big time with the indicators.

---

