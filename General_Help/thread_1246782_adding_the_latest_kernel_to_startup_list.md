---
title: "adding the latest kernel to startup list"
date: 2009-08-22
forum: General Help
---

### Post by djowtlawz on 2009-08-22
Hi I recently upgraded to 0.04 but for some reason I did not update the menu.lst

Can someone tell me how I can install the newest/working headers and update the menu.lst?

much appreciated.

---

### Post by fragos on 2009-08-22
> **djowtlawz said:**
> Hi I recently upgraded to 0.04 but for some reason I did not update the menu.lst

Can someone tell me how I can install the newest/working headers and update the menu.lst?

much appreciated.

I'm going to assume you updated over the internet and didn't use a live CD. Menu.lst is updated for the Ubuntu repositories and all 3rd party items which were for the prior release are disabled. You'll need to verify that those repositories support the 9.04 jaunty version and edit the menu.lst. I recommend you use System-> Administration-> Software Sources for that purpose.

---

### Post by drs305 on 2009-08-22
Try installing StartUp-Manager and see if it can sort things out for you. It's a GUI app for changing settings in menu.lst

In addition to setting the default OS, it can change the menu timeout, how many kernels to view, and more. 

Click the "SUM" link in my signature line for how to install and run StartUp-Manager. The guide also briefly discusses how to manually edit the menu.lst file if you prefer.

---

