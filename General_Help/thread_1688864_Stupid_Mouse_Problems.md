---
title: "Stupid Mouse Problems"
date: 2011-02-15
forum: General Help
---

### Post by ColeTurner on 2011-02-15
I am now using Ubuntu. 
I am having stupid mouse problems. 
When I highlight text in a website and right click on it, nothing happens.
When I click on things like File, Edit etc in a window, nothing happens.
Why is this happening?

---

### Post by mgois on 2011-02-16
Same problem here. It started to occur after updating the system first thing today. The updated packages were:
===============================================================================
[ACTUALIZAR] librxtx-java 2.2pre2-1 -> 2.2pre2-3~maverick1
[ACTUALIZAR] libssl0.9.8 0.9.8o-1ubuntu4.3 -> 0.9.8o-1ubuntu4.4
[ACTUALIZAR] libvlc5 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] libvlccore4 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] login 1:4.1.4.2-1ubuntu3 -> 1:4.1.4.2-1ubuntu3.2
[ACTUALIZAR] openssl 0.9.8o-1ubuntu4.3 -> 0.9.8o-1ubuntu4.4
[ACTUALIZAR] passwd 1:4.1.4.2-1ubuntu3 -> 1:4.1.4.2-1ubuntu3.2
[ACTUALIZAR] vlc 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] vlc-data 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] vlc-nox 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] vlc-plugin-notify 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
[ACTUALIZAR] vlc-plugin-pulse 1.1.4-1ubuntu1.3 -> 1.1.4-1ubuntu1.4
===============================================================================

Now the mouse stops working randomly. Sometimes I can click buttons, use the scroll, focus windows, other times I can't.

---

### Post by mgois on 2011-02-16
Looking more carefully, yesterday's updates were:
===============================================================================
[ACTUALIZAR] gir1.0-pango-1.0 1.28.1-1ubuntu3 -> 1.28.2-0ubuntu1
[ACTUALIZAR] libpango1.0-0 1.28.1-1ubuntu3 -> 1.28.2-0ubuntu1
[ACTUALIZAR] libpango1.0-common 1.28.1-1ubuntu3 -> 1.28.2-0ubuntu1
[ACTUALIZAR] libpango1.0-dev 1.28.1-1ubuntu3 -> 1.28.2-0ubuntu1
===============================================================================

It seams reasonable to me to assume that, an update do libpango is more likely to cause this problems than any of the other packages mentioned in the previous post.
Additionally, it seems that, when the mouse fails, it always occurs in a rectangular area in the center of the screen.
Any tips?

---

