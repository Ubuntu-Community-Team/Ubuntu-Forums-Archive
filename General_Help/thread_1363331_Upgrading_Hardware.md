---
title: "Upgrading Hardware"
date: 2009-12-24
forum: General Help
---

### Post by osarusan on 2009-12-24
I bought a new processor and motherboard, and will by upgrading my machine. Same harddrive. One quick question: is it better to do a complete wipe & reinstall, or will my Ubuntu install handle the upgrade with no problem?

Thanks.

---

### Post by fragos on 2009-12-24
Install the new mobo and run with the existing hard disk. It should work correctly. Note that it will use the video driver from the old system so you may have a little configuring to do if for example you went from Nvidia on the old system to ATI. It will be looking in /etc/X11/xorg.conf for which video driver to use.

---

### Post by osarusan on 2009-12-24
Thanks!
I'm pretty good with editing xorg.conf, so that should be no problem. Glad to hear that's all I'll have to worry about. :-)

---

