---
title: "Broken Xorg configuration on upgrade"
date: 2009-07-19
forum: General Help
---

### Post by exclipy on 2009-07-19
I have a Dell Inspiron 8600 with an ATI Radeon 9600 that I'm using as a second computer/server.  It did have Hardy Heron 8.04.1 on it, but I decided to upgrade.  I followed the graphical upgrade procedure to upgrade to Intrepid 8.10, and on restart, X failed to launch.

During the graphical upgrade procedure, I was given a warning that the fglrx driver for the graphics card didn't exist for Intrepid but I didn't need accelerated graphics so I thought that was fine... At first, I thought it wasn't booting because it was trying to use fglrx but I changed it to the ati driver and it still doesn't work.

I've attached the xorg.conf and the log of the error.

---

### Post by BslBryan on 2009-07-19
Hello, exclipy.  :-)  

This may be a little silly to ask, but have you tried doing an xfix?

---

### Post by exclipy on 2009-07-19
> **BslBryan said:**
> This may be a little silly to ask, but have you tried doing an xfix?

I have now and it didn't help.

---

### Post by BslBryan on 2009-07-19
Hmm.  You did do this from recovery mode, right?

If so, when you changed to the ATI driver, did you remove fglrx?

---

### Post by exclipy on 2009-07-19
> **BslBryan said:**
> If so, when you changed to the ATI driver, did you remove fglrx?

Thank you, removing xorg-driver-fglrx made it work!

---

