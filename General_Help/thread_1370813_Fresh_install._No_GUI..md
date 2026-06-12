---
title: "Fresh install. No GUI."
date: 2010-01-02
forum: General Help
---

### Post by mcpsm_84 on 2010-01-02
I've just installed Ubuntu 9.10, from a live cd. I'm booting to a command line. No GUI. Also, the screen flickers before command line comes up.

From googling, I'm guessing my problem may be on the video driver end. I have a GeForce 8400 GS.

I've tried "startx", "sudo start gnome-desktop", and "sudo gnome desktop", all with no results.

I'm a ubuntu newb.

---

### Post by jbrown96 on 2010-01-02
Since you have a 8400, I'm guessing that it's a desktop with an ethernet connection, so you should have a net connection at the terminal. Try installing the Nvidia driver with ```
sudo apt-get install nvidia-glx-185
``` Once that finishes reboot with ```
sudo reboot
```

---

### Post by muteXe on 2010-01-02
Are you sure you got the desktop iso and not the server iso?

---

### Post by jbrown96 on 2010-01-02
> **muteXe said:**
> Are you sure you got the desktop iso and not the server iso?

If the screen is flickering, then it's the desktop version, and the OP is right it's a graphics driver issue.

---

### Post by mcpsm_84 on 2010-01-03
Thanks, jbrown. The driver fixed it.  \\:D/

---

