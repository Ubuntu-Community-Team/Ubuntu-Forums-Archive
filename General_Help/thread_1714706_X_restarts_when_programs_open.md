---
title: "X restarts when programs open"
date: 2011-03-25
forum: General Help
---

### Post by Kazurik on 2011-03-25
Hello there, my X server restarts and boots me to the log screen when I start programs. I recently took the Nvidia card out of my computer and put in an ATI card. This is of course after uninstalling the Nvidia drivers through the restricted drivers interface. This worked out very well but eventually I went back to Nvidia. I removed the ATI drivers put in the Nvidia card and installed/selected the Nvidia drivers just as I did when I did this the other way previously. However now when I start just about any program the entire X server boots me back to the login screen. Any idea on how I can fix this?

---

### Post by PCNetSpec on 2011-03-25
Have you got any ATI specific settings in /etc/X11/xorg.conf ?

if so, you may want to  try disabling the NVIDIA drivers in **System>Administration>Additional Drivers**, renaming xorg.conf to something like xorg.conf.old, and reinstalling the NVIDIA drivers.

---

### Post by Kazurik on 2011-03-25
I was so very sure I had already tried that but I followed your directions exactly and it works perfectly now. Thanks for the solution!

---

