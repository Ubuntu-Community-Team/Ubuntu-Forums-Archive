---
title: "Map scroll wheel side click to middle button"
date: 2012-01-28
forum: General Help
---

### Post by spoon_ on 2012-01-28
I got a new mouse: a Logitech M500. It has a rather annoying feature. The scroll wheel can be pushed left/right to scroll left/right. The feature is annoying because it's extremely difficult to middle click without activating side scrolling. 

So my question is: is there some way to map side scrolling to middle clicking?

Thanks!

Edit: I've followed [this guide]("http://blog.burlock.org/ubuntu/196-disabling-the-mouse-scroll-wheel-left-and-right-click-for-ubuntu-1010") to simply disable the left/right scrolling buttons, but this is less than ideal.

---

### Post by spoon_ on 2012-01-29
Found a simple solution. Follow the same guide as mentioned above, but replace the ButtonMapping line with

> 
Option "ButtonMapping" "1 0 3 4 5 2 2 8 9 10 11 12"


The interesting thing is that for some reason, leaving the middle click button enabled doesn't work at all. I had to put a 0 in the second position. Prior to making this post I tried it without the 0 and it didn't work so I assumed doing this required something more sophisticated.

---

### Post by bugbugbugb on 2012-07-05
Download the logitech setpoint contral panel software and you can assign the left and right scroll to middle click. My patience with the middle button grew thin within an hour -.-

---

