---
title: "wrong resolution detected in ubuntu 9.10"
date: 2009-10-31
forum: General Help
---

### Post by prakreet on 2009-10-31
I have been using ubuntu 9.04 at 1024*768 resolution and 75hz refresh. I have now upgraded to ubuntu 9.10. I have done a clean install completely wiping out the previous 9.04 to avoid any problems. but ubuntu 9.10 is running my computer at 800*600 resoultion and 85 hz refresh rate. pls help me as under this resolution the system is totally unusable...

---

### Post by lilbill on 2009-10-31
Try going to System-->Preferences-->Display

You can change from there

---

### Post by prakreet on 2009-11-02
that's what i am saying.. my resolution 1024*768 is not detected there.. the resolutions available there are all lower than 800*600...

---

### Post by lowpan on 2009-11-02
Do you have a netbook with Poulsbo graphics chip?  Many netbooks use Poulsbo graphics chip, and there is no more video driver support.  So you get the default video with low resolution and low refresh rate.

If so, you should read 
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I followed this fix and fixed my video problem.  But it may have created a filesystem check problem at boot up time, not a drop dead problem, just annoying.  See [http://ubuntuforums.org/showthread.php?t=1308793&highlight=filesystem+checks](http://ubuntuforums.org/showthread.php?t=1308793&highlight=filesystem+checks)

---

### Post by prakreet on 2009-11-02
No.. I have an intel mobo with intel integrated graphics chipset.. And it used to work flawlessly in the last ubuntu 9.04..

---

