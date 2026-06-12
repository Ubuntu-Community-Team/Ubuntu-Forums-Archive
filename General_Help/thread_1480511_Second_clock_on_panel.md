---
title: "Second clock on panel?"
date: 2010-05-11
forum: General Help
---

### Post by joosto on 2010-05-11
I am actually a bit embarrassed to ask this question because the solution to my problem is probably very simple. Today I noticed that there is a clock in my notification area. This isn't really a problem but it looks pretty right next to another clock.

How can I remove this?

Thanks.

---

### Post by joosto on 2010-05-12
Anyone?

---

### Post by pjones0404 on 2010-05-12
are you not able to right click and remove?

sorry had to ask.

---

### Post by joosto on 2010-05-13
Unfortunately not.

---

### Post by DannyBiker on 2010-06-09
I was creating a new thread but I googled the subject before doing so and found this topic !

Please can someone tell me how to get rid of that silly second clock ? It is happening with different computers; I even have the problem on one of my system with Mint installed.

After "the week beginning irremediably on Sunday" bug under Karmic (for Belgium), I fear one of those Evolution problem (I just hate that application implementation).


Any info on this ?

---

### Post by Vaphell on 2010-06-09
when you right-click, are there some properties or preferences of that clock? does it say what it belongs to?

---

### Post by vandorjw on 2010-06-09
Odd for sure.
Does it stay when you log out and log back in? (Reload the panel)
One thing you can do, is this, if simply restarting the panels do not work is this.

1.) Right click on a blank space, and click "New Panel"
//A new panel should appear on the right side.
2.) Remove the old panel by right clicking and pressing "Delete this Panel"
3.) Move new panel to top.
4.) Add all things back that used to be there. (Not the second clock though)

This should work.

Hopefully someone else knows what the actual problem is.

Cheers CC7

---

### Post by eriktheblu on 2010-06-09
When you right click the superfluous clock, is there an option to unlock? You may need to unlock it before removing.

---

### Post by DannyBiker on 2010-06-10
I (We) can't right-click. The damn thing seems linked to the Sound-Mail-Bluetooth applet (what an idiotic move to put those together).
When I left-click on it, I have the date grayed out and two options "Open Calendar" and "Set Time and Date".

I can't make a printscreen as it doesn't work when I left-click the clock. How practical....

---

### Post by DannyBiker on 2010-06-10
> **cc7gir said:**
> Odd for sure.
Does it stay when you log out and log back in? (Reload the panel)
One thing you can do, is this, if simply restarting the panels do not work is this.

1.) Right click on a blank space, and click "New Panel"
//A new panel should appear on the right side.
2.) Remove the old panel by right clicking and pressing "Delete this Panel"
3.) Move new panel to top.
4.) Add all things back that used to be there. (Not the second clock though)

This should work.

Hopefully someone else knows what the actual problem is.

Cheers CC7

Sorry, didn't see that answer :
No it is not working as the new clock is attached to the notification applet (Battery, Sound, Bluetooth). I don't understand why is it happening on both of my systems, it doesn't make sense...

---

### Post by DannyBiker on 2010-06-10
Created a bug report :

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/592282](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/592282)

---

### Post by DannyBiker on 2010-06-10
Fixed thanks to the bug report :
The issue is most probably due to the Unity installation I made on my systems. It adds the "indicator-datetime" package that obviously shows this new...date and time indicator !
Once the package removed and the session restarted, the indicator is gone !

Thanks for the help.

---

