---
title: "Ubuntu 9 Will Install But 10 Will Not?"
date: 2010-06-23
forum: General Help
---

### Post by CaseyC on 2010-06-23
I have a 

Dell Latitude E6410, brand new business laptop. I was trying to install Ubuntu onto the machine today, but as soon as the first screen comes up i chose the first option which is i believe "Boot" then the screen goes black but still has power. I tried several editions of Linux including Fedora, Backtrack 4, and a few others but all the latest releases. 

Then I tried Ubuntu 9 which was a old cd i had laying around, and it worked fine until i went into the desktop GUI. Then it would instantally freeze up. I went in the BIOS and disabled multicore CPU and just enabled one core, and it worked fine. 

So from this point i was going to upgrade to the latest edition of Ubuntu. So i did the updates and restarted the laptop, then when it was booting it did the same thing as before the screen went black but before it did, i saw some message flicker real fast across the screen. I think it said something like unknown something you might experience problems. 

I can only assume this is some sort of driver issue. But Fedora, Ubuntu 10, and Backtrack 4 all do about the same thing, go blank and never load into the live cd part. 



So my question is, is there anything I can do to get Ubuntu 10 to install. Can i find the correct drivers somewhere for it and intergrade it in the ISO before i burn it and try to install it? I tried to find the spec's for this specific laptop online but was having some troubles. 

Any suggestion on what to do to get Ubuntu 10 installed?

---

### Post by CaseyC on 2010-06-23
bump. 

any idea's ? should i just stick with ubuntu 9.10?

---

### Post by Noz3001 on 2010-06-23
Maybe the OS is choosing a resolution your screen can not display. Try Ctrl+Alt+F1 and use **dpkg-reconfigure xserver-xorg**. See if you can set the resolution and correct driver.

---

