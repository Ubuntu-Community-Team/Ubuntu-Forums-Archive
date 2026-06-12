---
title: "Mounting .iso files"
date: 2006-03-21
forum: General Help
---

### Post by Klingstedt on 2006-03-21
I might be very n00bish now for asking but how do I mount an .iso file in Ubuntu? Is there some program that has the equal functions as daemontools?

---

### Post by ZylGadis on 2006-03-21
iso is really a device image, so you can readily mount it with mount.
E.g. for a cdrom iso:

sudo mount -o loop -t iso9660 image.iso mountpoint

The options etc might be wrong here, I'm writing from memory. Anyway, you get the idea.

No need for daemon tools or other programs that try to cover up windows's inadequacies :)

---

### Post by Petarded on 2006-03-21
[http://www.ubuntuguide.org/#mountunmountisofileswithoutburning](http://www.ubuntuguide.org/#mountunmountisofileswithoutburning)  <----

---

### Post by Klingstedt on 2006-03-21
Well im afraid i didnt get them right :S you don't think you could look'em up for me? :D Then you would be a God in my eyes :D

Edit: Okey there I got them :D thx ;)

---

### Post by mr.p on 2006-03-21
Anyone got a script that will let you do this by just right clicking the *.iso in Nautilus or something?

---

