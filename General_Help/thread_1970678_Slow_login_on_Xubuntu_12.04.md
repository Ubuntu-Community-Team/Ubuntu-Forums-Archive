---
title: "Slow login on Xubuntu 12.04"
date: 2012-05-01
forum: General Help
---

### Post by petehall on 2012-05-01
I have recently installed Xubuntu 12.04. When logging in, the system waits for over a minute during login at the point where the desktop background and a blank menu bar has been drawn. I can move my mouse around during this time.

When I log out and then log in as "Xfce Session", I do not experience this pause. When I then log out and back in as "Xubuntu Session", it's back.

I've attached a bootlog - it looks like Xorg is using a lot of CPU?

[http://imgur.com/Qg3rH](http://imgur.com/Qg3rH)

Pete

Edit: I've solved this by disabling non-essential startup applications and re-enabling them one by one. The culprit is xmodmap. Not sure exactly why, but it's something I can live without, so I've left it disabled.

Pete

---

