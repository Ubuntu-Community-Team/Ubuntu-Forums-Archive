---
title: "Why does my linux suck so bad?"
date: 2009-07-30
forum: General Help
---

### Post by sams2100 on 2009-07-30
I'm a huge fan of linux, I have used it for many years, but for some reason this installation of Ubuntu 9.04 appears to have a huge flaw.  Whenever I have an application that goes crazy and begins to consume all the memory, the entire machine locks up for about 10 minutes while it burns through all the swap until it finally says its out of memory and kills the process.  During that time, I cannot move my mouse, cannot hit the caps lock key, absolutely nothing, especially cannot get any sort of terminal window up to kill the process early.

Is there some setting somewhere that Ubuntu has changed that prevents apps from playing nice with each other?  I mean even windows can handle a rogue process going crazy, at least well enough to let you get to a process list and kill it, but for some reason my linux just freezes for 10 minutes until the damage is done, the entire time grinding away at the hard drive.  Shouldn't I be able to hit Ctrl-Alt-F1 or bring up a terminal window in X to kill the rogue process?  Nothing works for the 10 minutes of that process consuming all the memory.  The window of the application will turn gray and that is the last thing I see, not even the clock will update after that.

---

### Post by wojox on 2009-07-30
What application goes crazy?

---

### Post by sams2100 on 2009-07-30
I have two applications that will do this, The Gimp and aMule.  Both will sometimes just go crazy and begin consuming all the ram, I can watch the ram be consumed through gkrelm and then when it runs out and begins diving into the swap space, the system lasts for about 3 seconds before nothing will work any longer, not even the mouse.  Eventually it runs out of ram, kills off the app that is consuming all the ram, and finally hands over control of my system again. (10 minutes later)  This isn't specific to this computer, I have another one in the other room that has the same exact problem.

---

### Post by alphacrucis2 on 2009-07-30
> **sams2100 said:**
> I have two applications that will do this, The Gimp and aMule.  Both will sometimes just go crazy and begin consuming all the ram, I can watch the ram be consumed through gkrelm and then when it runs out and begins diving into the swap space, the system lasts for about 3 seconds before nothing will work any longer, not even the mouse.  Eventually it runs out of ram, kills off the app that is consuming all the ram, and finally hands over control of my system again. (10 minutes later)  This isn't specific to this computer, I have another one in the other room that has the same exact problem.


What exact operation were you getting Gimp to do when this occurred.

---

### Post by crazyfuturamanoob on 2009-07-30
It's not Linux which sucks. It's the memory leaks in Gimp and eMule.

---

### Post by unperson on 2009-07-30
Hi Sams2100,

I can definitely see how that behavior is pretty undesirable.  I'm guessing that the app is probably eating up 100% of the CPU too.  I think you're right that you ought to still be able to use the OS to shut it down, but I don't know if the fact that it can freeze up like that is really a new thing.  :(

So, I can't exactly answer your question, but I did think of a couple of things:  
 [LIST=1]
[*]You could try starting the offending process with the nice command, so that it has a lower priority.  That might help you in being able to get in there and stop it when it goes nuts.
[*]You could try changing the [swappiness]("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") parameter of the system.  I'm not sure whether this would change anything, though.
[*]If you have a lot of RAM you could try disabling swap entirely.  That would mean that it would run out of memory much faster and not spend a lot of time thrashing the HD.
[/LIST]
None of those are perfect solutions, but it's the best I've got.

---

### Post by MichealH on 2009-07-30
I have Ubuntu 9.04 and Its not bad as I have 20GB swap space. I use EXT3 instead of 4 cos EXT4 has bugs as it says [here]("http://ubuntuforums.org/showthread.php?t=1133719") :(

---

