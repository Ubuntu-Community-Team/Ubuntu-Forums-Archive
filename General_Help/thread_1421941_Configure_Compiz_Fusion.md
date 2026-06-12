---
title: "Configure Compiz Fusion"
date: 2010-03-04
forum: General Help
---

### Post by Scottty on 2010-03-04
Hello

I have Ubuntu 9.10 running on Virtualbox with XP running as the host

I am trying to configure Compiz Visual Effects by going to System--->Preferences--->Appearance

Once it opens click I click on Visual Effects select Extra option

From there I get the message "Desktop effects could not be enabled"

I have a GeForce 7300 SE video card and I bought my computer last year so I hope I have the proper specs to enable the visual effects

Thank you

Scott

---

### Post by wojox on 2010-03-04
Did you activate the driver for it. System > Admin > Hardware Drivers?

---

### Post by Scottty on 2010-03-04
I tried that out
> 
Did you activate the driver for it. System > Admin > Hardware Drivers?


and this is what my system said

> 
No proprietary drivers are used on this system


It also says
> 
Virtual Guest additions for Linux Module
Tested by Ubuntu developers
Licence free
This driver is activated and currently in Use


Thanks
Scott

---

### Post by Scottty on 2010-03-05
Well I solved one issue:

I learned by going to the VirtualBox program and before starting up Linux I configured the Hardware by clicking on the Details Tab(In Sun Virtual Box and then lookng down to where it say Display and I clicked on it. There I turned on 3D Acceleration. 

Then I started up Ubuntu on Virtualbox and went 

System--->Preferences--->Appearance

Once it opens click on Visual Effects select Extra option and click on close.

It actually works now

However now I have a new issue:
I get the message
"Could not switch monitor configuration"
"Could not set the configuration for CRTC 56"

Can someone tell me what this means and how to solve it.

Thanks
Scott

---

