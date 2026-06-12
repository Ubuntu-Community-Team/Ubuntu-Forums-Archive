---
title: "Ubuntu 11.04 and Unity: sorry for my stupid question :)"
date: 2011-03-28
forum: General Help
---

### Post by Fentanyl on 2011-03-28
I've installed Ubuntu 11.04 (the latest alpha release) on virtualbox.
It starts with gnome, not Unity.... 
On login screen i don't see any "Unity" option, just Gnome....
What did i miss? :)

---

### Post by 3Miro on 2011-03-28
> **Fentanyl said:**
> I've installed Ubuntu 11.04 (the latest alpha release) on virtualbox.
It starts with gnome, not Unity.... 
On login screen i don't see any "Unity" option, just Gnome....
What did i miss? :)

Unity requires hardware acceleration and Virtual Box has bad support for that. I don't think you can get Unity working under Virtual Box (and even if you do, it will not be very good). You can try enabling 3D effects under Virtual Box and installing the Guest Addons, but my guess is that it will not work (the xorg that comes with 11.04 is still new and it will take VBox some time to get 3D support for it). Get the Virtual Box manual from their web-page, they explain it better than I could.

This is not related to the problem but: Unity is Gnome. Most people don't understand this.

---

### Post by An Sanct on 2011-03-28
I run Unity under VirtualBox it runs even better then on my real machine/install (my GPU drivers are not ready yet). So you have two options: Classic desktop and the other option, that I don't remember, Classic is gnome, the other, Unity.

---

