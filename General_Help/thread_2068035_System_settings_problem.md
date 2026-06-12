---
title: "System settings problem"
date: 2012-10-08
forum: General Help
---

### Post by Naike on 2012-10-08
Hey.
I recently installed Ubuntu 12.04 on my netbook, and my touchpad settings aren't like I want them to be.
I can't decrease sensitivity and I can't change the scroll speed, which is really annoying, and also generally the system settings menu offers very very limited configuration.
From Kubuntu I remember KDE coming with tons of customizability and configuration for hardware.
Is there a way I can upgrade or add more options to my system settings?
And if not, how do I chage from unity to KDE?

---

### Post by westie457 on 2012-10-08
To change to Kubuntu is the easy part. ```
sudo apt-get install kubuntu-desktop
```
Log out and at the login screen click the cog and choose the one you want.

Removing the Ubuntu Desktop is problematical as the Desktop package is a Meta-package. Removing it does not remove the installed packages, those have to be removed manually. Careful use of Synaptic Package Manager is required and some patience.

---

### Post by Naike on 2012-10-08
Thanks.
I do like the design of Unity though, is there a way to add more options to the system settings menu?

---

