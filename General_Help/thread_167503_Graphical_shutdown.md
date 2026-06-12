---
title: "Graphical shutdown"
date: 2006-04-28
forum: General Help
---

### Post by ecentinela on 2006-04-28
After some update on dapper, the graphical shutdown is not appearing.
Now, I only see a black screen until the PC restarts or halts.
Somebody knows how can I solve this?

Thanks.

---

### Post by chriscando on 2006-04-30
I had a simular problem. I would get the samething when I tried to switch to a virtual console (Ctrl+Alt+1), use Ctrl+Alt+7 to get back if you try this.  My guess is that the video driver you are loading doesnt support the different resolution that the shutdown screen displays. You may need to edit your /etc/X11/xorg.conf file.  In Section "Device" I was using Driver "via", I changed "via" to "vesa", and restarted X (Ctrl+Alt+Backspace) and that fixed it for me.

Before you edit you xorg.conf file you should make a backup in case something goes wrong so you can copy it back if the graphical interface fails to show,
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

---

