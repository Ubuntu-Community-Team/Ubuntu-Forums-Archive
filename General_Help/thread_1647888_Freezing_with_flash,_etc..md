---
title: "Freezing with flash, etc."
date: 2010-12-18
forum: General Help
---

### Post by Gainesian on 2010-12-18
Hello Ubuntu forums, obviously I am a new member, so any inadvertent breach of forum protocols I apologize for.

Anyways. I am having a problem. I am running Ubuntu 10.04 on a Sony Vaio FW series. It has Nvidia graphics that I don't think the OS is taking advantage of, whatever. It also came with 64-bit Windows, it's a 32-bit OS, and again, as far as I have been concerned, whatever. It's been functioning fine for the half a year since I installed it.

Until recently. My computer has been freezing. What happened first is that the screen randomly whited out, fading in splotches to black and then back to white. This freaked me out, but restarting seemed to smooth things out. Then windows in the OS wouldn't resize, then Flash videos would freeze the OS up, repeating the 2 seconds of sound it last played. Over and over again. In a loop. On a white screen. Sometimes with vertical stripes. 

This all happens inconsistently, and whenever I restart it's fine again. I just want to know if there's a deeper issue so that I can resolve it. Otherwise I have been completely satisfied, as a previous Windows and OSX user who is computer-competent within a GUI.

Thanks in advance for your help! :D

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Did you install the proprietary drivers for your card? Look under System > Administration > Hardware Drivers and if available, activate the recommended one's.

And go to Applications > Accessories > Terminal and post the output of this commmand.

```
lspci | grep VGA
```

---

### Post by Gainesian on 2010-12-18
I'm a fool, the card is ATI. Here's the output of that command:
"VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]"

So. I installed the recommended drivers. Is it now going to be fixed? I find it really incredible that my computer functioned for so long without those...

---

### Post by theasprint on 2010-12-18
So your card is ATI. Well, report if there is any problems. And remember to mark your thread as [solved] if everything is all right!

---

### Post by Gainesian on 2010-12-18
I will indeed, thanks. It's kosher to give it a day or so before tagging "solved," right? It just has been an intermittent problem, so I don't know if it truly is "solved" yet.

---

