---
title: "Window Header Disappears"
date: 2010-07-08
forum: General Help
---

### Post by Ceiber Boy on 2010-07-08
When I’m using UBUNTU 10.04 the window header will disappears for no apparent reason, when this happened other function will also refuse to work, like being able to switch between desktops and closing program windows 
   
  The window header also contains the close, maximise and minimise buttons.
   
  Has anyone else found this and is their solution please, 
   
  the install I have is clean.
   
  Thanks

---

### Post by Akiviri on 2010-07-08
Hi

I have had this similar problem, but only on startup. The problem - for me at least - appears to be in compiz. If you get the compiz fusion icon (it's in the software center - or you might be able to sudo apt-get install compiz-fusion) when your headers disappear, go to applications > system tools > compiz fusion icon ....click on it - and it should appear on your upper panel. Right click it and select "Reload window manager" and your headers should reappear. That works for me at least.

I haven't had them randomly disappear on me, not yet at least. You may want to, if you have compiz installed i mean, double check that "window decoration" is checked off in the compizconfig settings manager (You can find that under system > preferences) 

Aside from that - do a search of this site, and see what you can find. I'm sure there are other people have had this problem...google turned up a bunch of hits at least - it seems to have been a problem for awhile with compiz...although it is a first for me.

Good luck

---

### Post by jimbop99 on 2010-07-08
I've had the same issue. It does seem to be related to a setting in compiz. I've playing around with the settings to see which affect(s) are causing the windows boarder to disappear.

---

### Post by Ceiber Boy on 2010-07-09
Disabeling compiz and updating seams to have done the trick, as it's a works machine I don't mind having the nice graphics and effects disabled. I do wonder if the graphics card is a the root of this problem!?

---

### Post by Budoc on 2010-07-09
> **Akiviri said:**
> Hi

I have had this similar problem, but only on startup. The problem - for me at least - appears to be in compiz. If you get the compiz fusion icon (it's in the software center - or you might be able to sudo apt-get install compiz-fusion) when your headers disappear, go to applications > system tools > compiz fusion icon ....click on it - and it should appear on your upper panel. Right click it and select "Reload window manager" and your headers should reappear. That works for me at least.

I haven't had them randomly disappear on me, not yet at least. You may want to, if you have compiz installed i mean, double check that "window decoration" is checked off in the compizconfig settings manager (You can find that under system > preferences) 

Aside from that - do a search of this site, and see what you can find. I'm sure there are other people have had this problem...google turned up a bunch of hits at least - it seems to have been a problem for awhile with compiz...although it is a first for me.

Good luck

Thank you very much for this solution!

Just to add to the above, the fusion icon is available from the repositories as "fusion-icon".
Also, logging out and then back in also works, but it isn't as elegant as the quoted solution.

---

