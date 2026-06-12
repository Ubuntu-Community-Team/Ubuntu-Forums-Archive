---
title: "Screensave"
date: 2011-05-13
forum: General Help
---

### Post by Skunkle on 2011-05-13
I was trying to change the Pictures Folder screensaver to only use one pic. I changed the destination but now the Pictures Folder option is gone from my screensaver menu. 


I typed :
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop

And changed the exec and tryexec lines to :
Exec=slideshow --location /home/me/Pictures/Backgrounds/a.jpg
TryExec=slideshow --location /home/me/Pictures/Backgrounds/a.jpg

Have I gone completely wrong here and made a fool of myself, or have I gone a little wrong and make somewhat of fool of myself. Or have I just overlooked something simple ?

---

