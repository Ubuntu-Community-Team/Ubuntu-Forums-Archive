---
title: "Refreshing problem"
date: 2009-09-27
forum: General Help
---

### Post by enduser on 2009-09-27
Maybe an overstatement: not sure.

I run worldcommunitygrid on ubuntu. (yay me) (YOU MUST TOO!!!) :P

It runs so perfectly that my laptop now sucks.

When i right click there is no general desktop "refresh" option which on windows xp or vista usually is equated to "wake up and let me use more ram for a bit".

How do I add a refresh option to my desktop right click?

Is there a way to have WCG be better about sharing resources when the user returns? 

I don't need the computer really, but every time I try to "learn" something new about Linux I have a moral dilemma. I don't want the program to stop running. I just need to not "chop-lag" while using more of the ram.

It feels like a problem on both ends. Being the on stuck in the middle I would like advice on how to keep WCG running while being able to use my computer.

Thanks

-Jonathan

---

### Post by elliotn on 2009-09-27
wow there isnt a refresh in ubuntu, remember ubuntu isnt windows. Some says it refresh itself so no need for a refresh button

---

### Post by 3rdalbum on 2009-09-27
The Nautilus desktop refreshes itself. So does Windows, actually, but some people in Asia use the "Refresh" menu item to kill time while waiting for some other task to complete; so Microsoft never removed it. Or so I hear.

The actual solution to your problem is not to refresh Nautilus, it's to increase the "niceness" of the WCG program.

In the System Monitor, find the WCG program in the Processes tab. (if you click the header of the CPU column, it should be right at the top). Right-click the process and go to Change Priority...  now push the slider to the very RIGHT. Yes, that's correct; the RIGHT.

This makes the program more "nice" (yes, that's a Linux term) and WCG will step aside whenever another program wants CPU resources, and then step back in when your programs are basically idle.

---

### Post by enduser on 2009-09-28
What do you mean by automatic? How often?

In my experience (with windows at least) there is a time when you NEED or want to manually refresh. When something isn't displaying properly or hasn't left memory refresh is a lot better of an option than a restarting the entire program.

---

