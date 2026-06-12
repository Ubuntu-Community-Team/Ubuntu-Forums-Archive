---
title: "&quot;blank windows&quot;??"
date: 2011-09-16
forum: General Help
---

### Post by vanhenryjr on 2011-09-16
I am not sure exactly how to ask this question-When I open up more than one program at a time I can only see the first program I have opened-every other "window" is just white.

example-open up mozilla browser-looks great. then open up evolution email-window opens on top of mozilla but is just white screen. If I go to mozilla and minimize it then still evolution is just a white screen-but if I close mozilla then i can open evolution and see it. This seems to be the case on all new windows opened. I can open multiple tabs in mozilla and see all them-but if I open mozilla in a new window the latest one is white. This did not happen with ubunut 10.10.

using ubuntu 11.04 on an older HP pavilion a1430n with a 17" samsung syncmaster 930b screen

---

### Post by amingv on 2011-09-16
Something similar happened to me while test-driving Ubuntu 11.04 +Unity a couple of months ago. Turned out the graphics card I was using wasn't well supported and this caused an error with desktop effects/compositing in Unity. Disabling compositing or running the classic desktop made the windows behave normally.

Unfortunately I no longer have that Ubuntu install, and I don't remember the exact steps to disable compositing. For now I can only suggest you try running gnome in classic mode (you select this at the Login screen>Sesstion type) and see if it makes a difference.

---

### Post by vanhenryjr on 2011-09-16
> **amingv said:**
> Something similar happened to me while test-driving Ubuntu 11.04 +Unity a couple of months ago. Turned out the graphics card I was using wasn't well supported and this caused an error with desktop effects/compositing in Unity. Disabling compositing or running the classic desktop made the windows behave normally.

Unfortunately I no longer have that Ubuntu install, and I don't remember the exact steps to disable compositing. For now I can only suggest you try running gnome in classic mode (you select this at the Login screen>Sesstion type) and see if it makes a difference.

thanx. I did switch to the classic mode a few weeks ago and still have this problem. It probably is a graphics card issue. Not sure how to deal with it, or even what graphics card is on the machine.

---

### Post by bbrg548 on 2011-09-21
> **vanhenryjr said:**
> thanx. I did switch to the classic mode a few weeks ago and still have this problem. It probably is a graphics card issue. Not sure how to deal with it, or even what graphics card is on the machine.

I had the same issue (or something that sounds similar). When I checked the third-party drivers (for my NVIDEA card) there were 2 options and the "current - recommended" one had been selected by default. I switched to the older one and that has fixed the problem for me.

---

### Post by vanhenryjr on 2011-09-21
> **bbrg548 said:**
> I had the same issue (or something that sounds similar). When I checked the third-party drivers (for my NVIDEA card) there were 2 options and the "current - recommended" one had been selected by default. I switched to the older one and that has fixed the problem for me.

thanx. after working with it i did the same exact scenario and went back to the older driver and am able to view all open windows as well. I should have posted in here to close this out.

---

