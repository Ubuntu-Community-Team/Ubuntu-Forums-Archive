---
title: "How to reset gnome to default?"
date: 2010-12-19
forum: General Help
---

### Post by pato wlmc on 2010-12-19
Ok, so here's the deal; today I used a Dual-Display on my laptop for the first time in my life. I decided to add panels the second monitor, to make it easier to navigate trought tabs and stuff.
Everything went pretty awesome until the end of the day When I  turned off the second monitor. I did so by clicking on System > Preferences > Monitors > OFF ( or something like that )
And then suddenly the two panels I have added to the other monitor went into my "Main one" so I ended up having 4 panels on a single screen, two on top, two at the bottom.

I thought on deleting them, but I was a little lazy about creating them again tomorrow, so I thought that hiding the pannel should do the work, but As soon As i marked the Hide pannels choice gnome feezed.

I rebooted, whit no succes, It boots, and it loads, but gnome wont answer.

I belive that those "pannels" are stored somewere on the system, so if you could tell me were, I coild just make the necesary changes, or in the worst case, reset the defaults.

Thanks in advice for your answer.

P.D. Sorry for the terrible english, but I'm not american

---

### Post by pato wlmc on 2010-12-19
Got it working guys!
I went to: /home/.gconf/apps/panel/toplevels  and moved "panel_0 ; panel_1" to my Desktop (There were also top_panel & bottom_panel, I supossed those were the default ones )

Then booted as normal, and then I was able to delete those panel Right away

---

