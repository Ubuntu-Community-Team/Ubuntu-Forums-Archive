---
title: "Black screen after Log Out"
date: 2012-05-05
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-05
I decided to create a new thread although I found a few similar threads because the existing ones are very old and do not match my hardware configuration.

After one of the recent updates (a week or so ago), after I log out I can't log in again because I only get a black screen. I hear the Ubuntu drums indicating that the login screen is showing, but nothing happens on the screen.

I have an [Acer Aspire TimelineX AS5830TG]("http://us.acer.com/ac/en/US/content/model/LX.RHJ02.220").

EDIT: I should mention that this happens when I log out from my main account. If I try using Guest account and log out from it, the problem doesn't exist.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-05
Bump?

---

### Post by angelus0415 on 2012-05-08
also have the same problem. black screen occurs when i switch user or i logout. but i can login successfully afterwards if i type my password after i hear the drum sound. it's fine after i log in. it's just the black screen before that

i created another account and this problem didn't occur.

help please?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-09
Yes, I also discovered that if I "blindly" type my password, I can actually log back in. Any help, anyone?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-11
I've found a fix [on this address]("http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10"). It's ridiculusly simple: My Display's Default resolution is 1366x768 (16:9), and for some reason it was changed to 1360x768. Change your display's resolution back to the Default and the problem is gone! Lousy 6 pixels... ](*,)

---

### Post by Yossi Gil on 2012-07-14
> **&#1058 said:**
> I've found a fix [on this address]("http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10"). It's ridiculusly simple: My Display's Default resolution is 1366x768 (16:9), and for some reason it was changed to 1360x768. Change your display's resolution back to the Default and the problem is gone! Lousy 6 pixels... ](*,)

Seems to have solved my problem as well on Thinkpad X220.

---

