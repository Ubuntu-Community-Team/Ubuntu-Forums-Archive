---
title: "Full laptop battery triggers low battery error."
date: 2012-03-11
forum: General Help
---

### Post by oxf on 2012-03-11
When I have a full charge on my laptop battery I occasionally get the following message.

"battery critically low......about to hibernate" The batter symbol in the upper panel is also red/empty. 

The battery is NOT low, it's full or almost full. This does not happen every time, maybe one in five or six boots and usually occurs a couple of minutes into the session. Very annoying. When it happens it hibernates and then I have to log back in and restart after which all is fine.

Anyone know how to fix this?

Katya.

Acer Aspire one
Ubuntu Maverick

---

### Post by oxf on 2012-03-12
bmp

---

### Post by oxf on 2012-03-13
Anyone?

---

### Post by oxf on 2012-03-13
.

---

### Post by varunendra on 2012-03-14
A quick search gave me a lot of links that discuss similar problems but _none of them is 'Exactly' similar to yours_:

[https://bugs.launchpad.net/null/+bug/572541](https://bugs.launchpad.net/null/+bug/572541)
(bug-report about gnome-power-manager)

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069)
(duplicate of above)

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/860427](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/860427)
(similar to above two)

[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190)
(bug-report about 'upower' module. Comments #149, #150 at the bottom of the page say it seems to have been fixed in 12.04 beta-1)

**They are all slightly different than your problem since in your case, the battery is 'actually' being detected as 'Empty'** (i.e., close to 0-10%? Can you confirm that?). Just because of this one reason, I doubt that maybe yours is a hardware problem- most probably a bad connector or a dying battery!

If you think the above links correctly represent your problem, then the most frequent and probably the most promising workaround is given here: [http://ubuntuforums.org/showthread.php?p=11402594](http://ubuntuforums.org/showthread.php?p=11402594)

But if your battery is 'actually' being detected as low (0-10%), then the above trick is not going to work for you. In that case, cleaning the battery contacts (and the laptop's), or trying a different battery, if available, are the only things I can suggest.

Good Luck!

---

### Post by oxf on 2012-03-14
Thanks Varun for those links!
I am at work now so will have to check them later.

I don't think it is a battery/connector problem because after it hibernates and log back in the battery is then detected as full and lasts for several hours as normal. I have checked the battery contacts many times

I think the most likely candidates are the gnome-power bug or upower module.
I will read through the links (hope it's not above me!) and try that and post back later.

Many thanks!
Katya

---

