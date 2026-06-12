---
title: "changing to widescreen"
date: 2010-07-10
forum: General Help
---

### Post by Autodave on 2010-07-10
Old monitor was a 4:3.  Got new monitor which is 16:9.  Under SYSTEM > PREFERENECES > MONITORS, 800 x 600 is the maximum shown. Viewing the Xorg file shows many more resolutions.  However, it also says not using because HSYNC out of range.  How can I make use of these and get the resolution higher?  (I know that when the machine was running Winblows, I could run a much higher resolution then.

---

### Post by dino99 on 2010-07-10
xorg.conf is no more needed with actual kernel, so rename yours (or delete it if you no longer need it for the old monitor)

to delete it:

sudo rm -f /etc/X11/xorg.conf

---

### Post by Autodave on 2010-07-10
> **dino99 said:**
> xorg.conf is no more needed with actual kernel, so rename yours (or delete it if you no longer need it for the old monitor)

to delete it:

sudo rm -f /etc/X11/xorg.conf


Removed file and rebooted.  Still only have max size of 800 x 600 to chose.  Now what?

---

