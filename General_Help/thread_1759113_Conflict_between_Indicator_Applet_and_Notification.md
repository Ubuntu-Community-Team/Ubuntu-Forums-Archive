---
title: "Conflict between Indicator Applet and Notification Area Applet"
date: 2011-05-15
forum: General Help
---

### Post by adiasd on 2011-05-15
Hi Folks,

I was using both the Indicator Applet and the Notification Area applets in my panel but realized that very often when I started the system, the icons of these applet appeared mixed. Some items were duplicated (for example the keyboard indicator) where others were missing (sometimes the battery indicator, sometimes the sound indicator, etc). When that happened I had to remove them and add them to panel again.

This seems to be a bug that makes one applet interfere with the other (maybe because there are some items that appear in both but when you add both initially nothing is duplicated but after a system restart the problem happens).

After searching for some way to fix this apparent bug without success I decided to remove the Indicator applet and keep just the Notification Area. It works but then I don't have the sound applet anymore, because it was part of the Indicator Applet.

I searched for a standalone sound applet but I couldn't find any. Do you know of any such applet that I could install in the system? If I can find any it would be fine to me and I would be satisfied using just the Notification Area.

Thanks for any help here.

---

### Post by dino99 on 2011-05-15
those applets (using the old gtk2) are not really maintained as we get gnome3 in the near future, but do you really need a sound applet ?

Set your prefs with alsamixer, then each sound apps have builtin prefs

---

