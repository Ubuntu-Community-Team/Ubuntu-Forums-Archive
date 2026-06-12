---
title: "How do I patch a kernel driver module?"
date: 2009-09-01
forum: General Help
---

### Post by DeLaNooch on 2009-09-01
How do I go about patching a kernel module? More specifically, I want to patch my Mac80211 driver. Do I need to patch and re-compile the whole kernel? Or can I just patch and reinstall the specific module? If someone can just answer that question and point me in the right direction I'm sure I can figure it out.

Thanks,
Jordan

---

### Post by Cato2 on 2009-09-02
You should be able to just patch and recompile the specific module - you end up with a .ko file that you put in a modules directory.

See [http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html) for what looks like a good HOWTO.  Also, check the linux-wireless site.

For wireless, often it's easier to first try to install a newer kernel - e.g. if on Intrepid, find the Jaunty kernel image (linux-image-xxx) on the Ubuntu package site, download the .deb, dpkg -i the .deb, and you're done.  I did this for a Hardy box recently, installed the Intrepid kernel to solve a WiFi kernel panic with rt2x000 mac80211 based driver.

---

