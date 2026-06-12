---
title: "Remastersys Boot Selection Screen"
date: 2009-09-10
forum: General Help
---

### Post by kowspot2000 on 2009-09-10
Hello,

For work I was charged with the task of creating a live-cd bootable environment pretty much for vpn-ing and remote desktop-ing. Everything is working fine in the remastersys image, but there is only one thing I would like to change.

When the remastersys iso is booted, it presents the user with the generic boot screen (press enter to boot into live, or type install to install to HD, etc...). Since this is only supposed to be a live CD and the people who are going to be using it are computer illiterate, I would like to remove all options from the screen and leave only the "press enter to boot live", or if possible, boot into live automatically.

Is there a way to do this?

Thanks in advance.

- Josh T

---

### Post by ingramproductions on 2010-06-05
Edit the boot menu file located at:
/etc/remastersys/isolinux/(config file)

You can also edit the boot image here.

---

