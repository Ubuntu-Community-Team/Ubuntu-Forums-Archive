---
title: "Boot hangs after changing plymouth theme"
date: 2010-07-22
forum: General Help
---

### Post by justin_3994 on 2010-07-22
I have a fresh install of 10.04 and i have changed my playmouth theme to spinfinity and now when  i boot its plays the animation and then just stops with the ubuntu logo on the screen.....ice let it sit at this state for hours...when i push the power button on my computer the logo goes away and ubuntu proceeds to shut down......i cant log into my desktop to change the theme back to the default....im on another partition at the moment....how do i change my theme back to the default?

---

### Post by Roti78 on 2010-08-24
sudo update-alternatives --config default.plymouth

this bug has been reported:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/590103](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/590103)

---

