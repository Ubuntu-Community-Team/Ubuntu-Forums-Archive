---
title: "update manager chromium untrusted packages endless loop"
date: 2011-05-05
forum: General Help
---

### Post by sea_dawg on 2011-05-05
Hello all,

When prompted to install the latest updates I click "Install Updates" and get the message "Requires installation of untrusted packages".  Please see the attached image.

The only choices offered are "Close" and "Details".  Clicking "Close" takes me back to the Update Manager.  Then when I click "Install Updates" again the same message pops up.  It is an endless loop.  

Clicking on "Details" I get 

```
apt apt-transport-https apt-utils chromium-browser chromium-browser-inspector chromium-browser-l10n chromium-codecs-ffmpeg firefox firefox-branding firefox-gnome-support libjson-glib-1.0-0 libperl5.10 perl perl-base perl-modules usb-creator-common usb-creator-gtk vino winetricks xulrunner-1.9.2
```

I've tried searching the forum and haven't seen anything like this.

Thank you.

Ubuntu 10.10

---

### Post by zvacet on 2011-05-06
Try to install packages via terminal 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sea_dawg on 2011-05-06
Thank you, this leads to two more questions

Would ```
sudo apt-get update
``` perform the same updates that Update Manager is listing?

Would ```
sudo apt-get upgrade
``` perform the Natty upgrade?
If so, I an not interested in the upgrade at this time.

---

### Post by polki@mac.com on 2011-05-06
Nope, it will only upgrade your current packages, it won't pull anything from Natty.

---

### Post by sea_dawg on 2011-05-06
Thank you both!  It worked like a charm.

---

