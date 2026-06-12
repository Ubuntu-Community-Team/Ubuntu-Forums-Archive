---
title: "need help running acer update for bios (exe issue)"
date: 2010-04-13
forum: General Help
---

### Post by skippets on 2010-04-13
HI, I have recently installed ubuntu but the fan on my laptop isnt working, I have searched around about this problem and apparently updating the bios may help. 

Im very new to all this just to warn you, so anyway, the file to update the bios is an exe, so I installed wine, but when i used it, it gave me a erroe message about not being able to run a driver and so the exe doesnt run. 

I have searched for the forums for how to run exe files but the responses seem a little confusing and very varied! probably because it is such a frustratingly frequent question that gets raised ;)

also my laptop cant be on for very long without it shutting down from the heat so I am against the clock !

---

### Post by Mark Phelps on 2010-04-14
Updating the system BIOS is a very risky action.  IF you do it wrong, you will end up with an electric "brick" -- because after that, NOTHING will work.

As you discovered, you can't install device drivers using Wine -- it doesn't do that.

You should check the documentation that came with your machine to see if it has anything in there about recommended ways to update the BIOS.  Some machines have a special key combination you push when you boot such that it reads BIOS info from an inserted diskette (older machine) or USB stick (newer machine) and does the BIOS upgrade from that.  But in those cases, you usually need to have the BIOS file extracted to do that.

What BIOS .exe files typically do is extract themselves to external media -- like a diskette or USB stick.  You will need to find someone with a Windows machine, run the exe file on their machine, and extract the contents to media that you can insert in your machine.

---

### Post by skippets on 2010-04-14
Thanks, I will try all that! thanks for the advice

Stupid of me really I should have made a dual boot for trying out ubuntu, I could have easily run the update from windows. 

Oh well im certainly learning if nothing else!

---

