---
title: "Dell E173FP monitor - cannot display video"
date: 2010-02-24
forum: General Help
---

### Post by dc_atkinson on 2010-02-24
I have recently installed ubuntu using wubi on a dimension 9100 PC .  When i boot up ubuntu I get a message that it cannot display current video mode when the GUI tries to launch.  The monitor is a Dell E173FPb

From digging about on google it seems I need to edit the xorg.conf file?  However, it doesn't exist in the /etc/X11 directory.   Does wubi not create this file?   

I then created a template of this xorg.conf with the "sudo X -configure" command.  I then copied the created file to /etc/X11/xorg.conf and editied the Monitor settings.  however, I still get the same error even when I put in the HorizSync and VerRefresh settings shown on the Dell webpage (31-80 and 56-76 respectively).

Can anyone help?  I am new to ubuntu and have run out of ideas!

many thanks
David

---

### Post by cscj01 on 2010-03-04
I can't help you, but I have the same problem with the E173FPc.  Mine started today after applying the CUPS and kernel updates.  I am running Karmic.  One thing I am going to try is remove all lines in the xorg.conf file for the Monitor section except the Identifier and Monitor values.  Hopefully a Linux guru can help us out.

---

