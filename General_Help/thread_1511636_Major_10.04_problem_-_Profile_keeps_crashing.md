---
title: "Major 10.04 problem - Profile keeps crashing"
date: 2010-06-17
forum: General Help
---

### Post by Halfling Rogue on 2010-06-17
I've got Ubuntu 10.04 (installed on top of Dapper, which is now in a separate partition) on a Dell Latitude D600. Ever since I've installed 10.04, it has this thing where, when I do certain things in Firefox, my current session will hang, close, and then send me back to the Ubuntu login screen.

I thought it was initially a Flash conflict, as it primarily (but not consistently) happens when I'm trying to view YouTube videos through Plurk.com, but it's now happened as a result of my simply navigating Plurk, viewing Flash videos on other websites, having a site with Flash open in a different tab, and also one time where I attempted to drag an image directly from Firefox to Gimp (that was the worst -- I lost the drawing I was in the middle of).

This is *amazingly* frustrating since I have no way of predicting what will trigger it, and every time it happens I lose everything I was working on. ](*,) I will look into submitting a bug, but first I wanted to check whether anyone else has this problem, and what potential trouble areas I should look into, if any.

---

### Post by requeth on 2010-06-17
I'd recommend first installing Google Chrome and seeing if you can reproduce the issue with Chrome being the only browser open.

If it still occurs: Check to see if there's a proprietary driver available for your system. Often times this can help. You can find this by going to System: Administration: Hardware.

If it stops occuring: Try removing all of your FireFox plugins and reboot. See if this solves the issue. If not try re-installing Firefox.

---

### Post by Halfling Rogue on 2010-08-07
> **requeth said:**
> I'd recommend first installing Google Chrome and seeing if you can reproduce the issue with Chrome being the only browser open.

If it still occurs: Check to see if there's a proprietary driver available for your system. Often times this can help. You can find this by going to System: Administration: Hardware.

If it stops occuring: Try removing all of your FireFox plugins and reboot. See if this solves the issue. If not try re-installing Firefox.

Started getting errors shortly thereafter repeatedly saying that the Flash plugin had crashed. Guess that explains it! I wound up getting a new machine anyway, so the issue is a moot point now. Thanks for your advice. :)

---

