---
title: "Gimp would not start"
date: 2010-01-29
forum: General Help
---

### Post by Kdar on 2010-01-29
I tried to install Gimp 2.7 today, but after few crashes, I decided to move back to 2.6

However when I remove Gimp 2.7 (with it's ppa)and after I installed 2.6. When I tried to load Gimp from Menu would not work. Nothing would start.

When I tried to run command "gimp-2.6" in terminal
I get this error message:
> gimp-2.6: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory

What can I do to fix it?

---

### Post by whiskeylover on 2010-01-29
sudo apt-get install libgegl-0.0-0

---

### Post by Kdar on 2010-01-29
I tried that already. Didn't work.

> Building dependency tree       
Reading state information... Done
libgegl-0.0-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  xloadimage libjpeg-progs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[xxxxxxxxxx-desktop ~]$ 


---

### Post by whiskeylover on 2010-01-29
Try this URL

[http://www.linuxquestions.org/questions/slackware-14/cannot-open-gimp-after-upgrade-to-version-2.6.5-707586/](http://www.linuxquestions.org/questions/slackware-14/cannot-open-gimp-after-upgrade-to-version-2.6.5-707586/)

---

### Post by Kdar on 2010-01-29
> **whiskeylover said:**
> Try this URL

[http://www.linuxquestions.org/questions/slackware-14/cannot-open-gimp-after-upgrade-to-version-2.6.5-707586/](http://www.linuxquestions.org/questions/slackware-14/cannot-open-gimp-after-upgrade-to-version-2.6.5-707586/)

Thanks for link. It helped me.

I had to remove babl, gegl and gimp

And then install everything again.

---

