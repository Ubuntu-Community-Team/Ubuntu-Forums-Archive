---
title: "screen resolution problem"
date: 2006-05-09
forum: General Help
---

### Post by norqui on 2006-05-09
Dear ubuntuers,

After updating the system, the screen resolution 1024x760 does not longer work the way it worked before the updating and I have to switch to 800x600, which is a little unconfortable to my LCD notebook display. Any clue to what may have happened?

best

Norberto Moreno
Talavera de la Reina (Spain)

---

### Post by Sendervictorius on 2006-05-09
In a terminal run:
sudo dpkg-reconfigure xserver-xorg

Then close any open windows or programs you have running on your desktop and press CTRL-ALT-Backspace to restart X.

It should fix the problem, but if it does not work, check out his howto guide: [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto) If you need more help, come back to this thread.

---

### Post by rumli on 2006-05-09
This happened to me once after an update as well.  It turned out that my monitor sync and refresh rates had somehow been deleted from my /etc/X11/xorg.conf file.

As the previous poster says, follow the steps on [https://wiki.ubuntu.com/FixVideoResolutionHowto]("https://wiki.ubuntu.com/FixVideoResolutionHowto") to fix your screen resolution problems.

---

