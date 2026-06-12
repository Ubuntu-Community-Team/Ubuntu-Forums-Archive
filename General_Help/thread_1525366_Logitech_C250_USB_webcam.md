---
title: "Logitech C250 USB webcam"
date: 2010-07-06
forum: General Help
---

### Post by Hawk510 on 2010-07-06
I recently received a Logitech c250 webcam.  All the information I've been able to gather says that this webcam should work right out of the box, but not only does it not work (and cause Cheese to shut down as soon as I open it), it also causes the wireless to stop working as soon as I plug it in.  I'm still fairly stupid when it comes to Linux.  Could the webcam be interfering with my wireless drivers?  Any help would be appreciated!  I'm using Lucid 10.04.

By the way, I tried the cam on Windows Vista and it works perfectly.

---

### Post by mike555 on 2010-07-06
I just got one of those and it just works with cheese ... on lucid .

---

### Post by Hawk510 on 2010-07-07
That's exceedingly unhelpful.  However, I did manage to get things swinging.

It turns out I was lacking something in V4L2.  I installed an extra set of drivers which ended up having it, I guess.

---

