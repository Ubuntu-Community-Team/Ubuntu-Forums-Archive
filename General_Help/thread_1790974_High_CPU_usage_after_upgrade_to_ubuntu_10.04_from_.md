---
title: "High CPU usage after upgrade to ubuntu 10.04 from 9.10"
date: 2011-06-25
forum: General Help
---

### Post by fixitdude on 2011-06-25
Just started using 10.04 and now for no reason, Xorg takes a lot of CPU just sitting there doing nothing.

Searching around I find that other people have had the same problem but no solutions have been found. ATI graphics card or nVidia both seem to have problems.

Anyone been able to solve this easily?

Suggestions were:  (for reference)

Try turn desktop effects off (System > Preference > Appearance > Visual Effects).

check if you are running any 3D programs or anything which uses compositing

[http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/](http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/)
"To fix this issue, add the below option to /etc/X11/xorg.conf under the Device section." Option "UseEvents" "on"  (for nvidia)


Keywords High CPU usage, computer erratic and unresponsive, jerky and hard to use, sluggish. Flash player slow. startrek.com player sucks and completely stops and wont start back up if you lose internet connection for only a few seconds, won't re-negotiate the TCP connection and does a poor job of buffering.

---

