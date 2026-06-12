---
title: "all about GRUB"
date: 2010-09-14
forum: General Help
---

### Post by nischalinn on 2010-09-14
I am using Ubuntu 10.04.
My** grub menu **shows so many options about** 6-7 options**. I want to display 2 options, one for linux and other for windows. Is it possible via** GUI** or I've to go with commands?

Linux option is shown at the beginning and windows is shown at the bottom, can I **change the order** also?

Can I **change the loading time**? I want to all these via GUI, is it possible??

---

### Post by drs305 on 2010-09-14
If the options are different kernels, you can eliminate them from the menu by using a setting in Startup-Manager (this feature still works in Grub2).

If you want to hide the extra kernels *and* remove them from you system (saving a bit of space), I recommend an app called Ubuntu Tweak.

Both are GUI apps that are very easy to use. To read about how to use them both, refer to the "Removing Older Kernels" section of this link:
[HOWTO: Grub Menu Kernel Display Options ]("http://ubuntuforums.org/showthread.php?t=818177")

If you want to hide the Recovery mode option, that can be done from a setting inside /etc/default/grub.  Refer to the G2-Basics link in my signature line.

---

