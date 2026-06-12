---
title: "Amarok"
date: 2009-11-08
forum: General Help
---

### Post by cowboy7305 on 2009-11-08
No sound coming from amarok using ubuntu 9.1 ,can play music on rhythmbox no trouble every thing else seems to be working on amorok but no sound 
any chance i have not downloaded something 
many thanks

---

### Post by kio_http on 2009-11-09
Go in kde system settings
Multimedia.
Test which "device" works
Then click prefer and set it a higher priority

---

### Post by Yellow Pasque on 2009-11-09
A lot of people solve this issue by installing the libxine-1-plugins package.

If you can't get amarok to work with xine, then get phonon-gstreamer package and use qtconfig to set Phonon to use the gstreamer backend (amarok uses Phonon).

---

