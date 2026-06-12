---
title: "firefox middle click"
date: 2006-04-28
forum: General Help
---

### Post by pinky on 2006-04-28
Hello,
from other distribution i'm used to that a middle click with the mouse into firefox will insert the url from the clipboard into the url-bar and load the site. But on Ubuntu a middle click into the browser window generates no reaction.

Does someone know how i can change this, so that firefox behaves like on every other distribution?

Thanks!

---

### Post by BryanL0911 on 2006-04-28
It works for me.... 

Did you check your xorg.conf to see what mouse you are loading?

---

### Post by lotheac on 2006-04-28
First, type "about:config" in your urlbar. Filter by "middlemouse" and set "middlemouse.contentLoadURL" to true. It's probably off by default because new users might not find themselves familiar with this kind of behaviour.

---

### Post by pinky on 2006-04-28
Thank you lotheac, now it works :)

---

### Post by kkinder on 2006-07-10
This bugged me too, although I figured out how to manually set the preference.

Given the fact that the middle-mouse-URL behavior is the Linux default, and that it's extremely useful, I think that behavior should be restored as the default. It's one of the nicest features FF has.

---

### Post by yooden on 2007-01-06
Hi,

> **lotheac said:**
> First, type "about:config" in your urlbar. Filter by "middlemouse" and set "middlemouse.contentLoadURL" to true. It's probably off by default because new users might not find themselves familiar with this kind of behaviour.

First, thanks for your tip, it worked for me.

Second, that is among the most stupid decisions I can remember in Free Software. You disable an age-old feature because new users might be confused by it? Why bothering to change stuff at all?

I'm just swinging between Debian and Ubuntu, this stupidity might have made the decision for me. Not because it's hard to fix, but because I cannot see the rationale for this AT ALL, and I'm afraid Ubuntu might have more dumb suprises for me. (Yes, I'm aware that it's not a paying customer Ubuntu looses.)

Still incredulous,
Yooden

---

