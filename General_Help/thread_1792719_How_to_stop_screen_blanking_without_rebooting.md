---
title: "How to stop screen blanking without rebooting?"
date: 2011-06-28
forum: General Help
---

### Post by apollothethird on 2011-06-28
Can someone advise me of how to turn the screen/monitor blank off without rebooting (or if there is a way)?

I have tried:

```
setterm -blank 0
```which has always worked in Slackware, Red Had and Fedora.  I have went into Screen saver and set never to putting the computer to sleep.  I have unchecked screensaver when computer is idle.  Thanks in advance for any other suggestions of what I might be missing.

I have applications running that I need to monitor.  At present every few minutes I have to go over to the computer and hit a key.  I'm hoping I can remove this blanking without having to cancel my applications, make changes to xorg.conf and reboot.

I'm running Ubuntu 11.04, Unity 2D.

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by tcsmith1978 on 2011-06-28
Is there an option to "Lock Screen"? That seems to work for me...

---

### Post by h4x0l2 on 2011-06-28
> **tcsmith1978 said:**
> Is there an option to "Lock Screen"? That seems to work for me...


oddly enough, lock screen fixes many issues with the graphical interface (compiz stuff too). best to keep it enabled.

---

### Post by apollothethird on 2011-06-28
> **tcsmith1978 said:**
> Is there an option to "Lock Screen"? That seems to work for me...

I couldn't imagine that having anything to do with the screen blanking, but tested it anyway.  It would appear if it did have anything to do with it, removing the check mark would be the key.  But, as suspected, id doesn't have anything to do with the blanking screen.  I'm sure it would have to do with being prompted for a password to get back to the desktop from the screen saver, which at this time, I don' t have a screen saver set.  I'm trying to keep the screen always in view of the desktop without having to touch anything to see the desktop.

So far, no matter what I do, it blanks out after a few minutes and I have to hit a key or move the mouse to see my applications.  I often wonder what's in the minds of the programmers that they build such annoyances into the defaults and make it so hard to get out of them.

I'll soon close my applications (which I really wish I didn't have to do) and experiment with performing other things that might stop the screen from going blank.  Hopefully I'll be able to start my applications and allow them to run for days the next time.  So if anyone has any ideas of the best way to go, I'd appreciate having those ideas so that I might not have to reboot many times in stopping Ubuntu from blanking the screen.

Thanks in advance for anyone that has any ideas.

By the way, Tcsmith.  I'm just curious, if you remove the check mark from your screensaver lock does that start your screen to blank?  Does your screen even blank off?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

