---
title: "looking in the trash causes the desktop to crash"
date: 2009-07-09
forum: General Help
---

### Post by jeffersonbenson on 2009-07-09
the title says it all. I just updated to the latest and when I deleted some stuff, it went to the recycling bin like it should. However, when I went to click on the trash icon on my panel, all my icons disappeared from my desktop. I keep a lot of files there and it was strange to see them all just disappear. After that I tried to access the trash through Nautilus by clicking on trash. No dice. Nautilus closes and that's that. No crash reports, warnings or anything. This is really frustrating because I have to reboot every time in order to get my icons back. I just switched after growing up with windoze all my life and would really like some help. Thanks.:guitar:

---

### Post by dmbortz@gmail.com on 2009-09-19
Just run:

dbus-launch nautilus &

from a terminal and you won't have to log out and log back in.

David

---

