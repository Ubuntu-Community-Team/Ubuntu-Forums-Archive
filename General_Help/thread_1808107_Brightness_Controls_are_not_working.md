---
title: "Brightness Controls are not working"
date: 2011-07-19
forum: General Help
---

### Post by ZenM4ster on 2011-07-19
Hello everyone I recently purchased an HP Pavilion dv7t 6163us and I installed ubuntu 11.04 on there. Everything works fine except the fn + f2 and fn +f3 which decreases and increases the brightness respectively. can anyone help me with this problem?

It's using the i7-2630qm sandy bridge processor and intel HD graphics 3000.


Thanks 

Zen

---

### Post by gaboalonso on 2011-09-06
> **ZenM4ster said:**
> Hello everyone I recently purchased an HP Pavilion dv7t 6163us and I installed ubuntu 11.04 on there. Everything works fine except the fn + f2 and fn +f3 which decreases and increases the brightness respectively. can anyone help me with this problem?

It's using the i7-2630qm sandy bridge processor and intel HD graphics 3000.


Thanks 

Zen

I am too having this issue with my new HP Pavilion G4 laptop, with ubuntu lucid (10.04).

I wish there was at least some other way to change the brightness, since it is terrible bright for night work.

Thanks.

-Gabe

---

### Post by jfed on 2011-09-06
Have no fear, I sort of have a solution! I have the exact same issue. I have buttons on my keyboard that are SUPPOSED to increase/decrease the brightness. However, they don't. I'm not sure if this is only Ubuntu, because I didn't have the laptop when it ran Windows, somebody else did, but that's not the point. I have a few other friends, people with Acers especially, that the on-board brightness controls work just fine, but after mashing my button for hours on end, I set out to find another solution.

If you're running Gnome, or unity too I think, you probably have compiz as your window manager. If you don't you should probably get it. With compiz you can change your window's brightness settings. However, this doesn't actually decrease the brightness of the monitor, it just sort of blackens the current window, but it help if say you're watching a movie late at night, etc. Here is a screenshot.

[IMG]http://img819.imageshack.us/img819/2872/helpthem.png[/IMG]

This is under (I'm not exactly sure actually because I have Xfce but it should be under something like) System>Preferences>CompizConfig Settings Manager. Inside there, its under accessibility. You can bind a keystroke to increase the current window's brightness, as well as decrease it. Here is a screenshot of how it looks.

[IMG]http://img15.imageshack.us/img15/603/screenshotadw.png[/IMG] 
Mplayer on the left has the brightness turned down a considerable amount, while VLC on the right has it maxed out.

I hope this helped, as this was the only solution I was able to find after searching for some time.

---

### Post by gaboalonso on 2011-09-06
Thanks jfed. I'm glad to report that the issue got resolved after I upgraded to 10.10 Maverick.

---

