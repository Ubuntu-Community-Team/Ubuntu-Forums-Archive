---
title: "How do I re-install an non-working nvidia graphic driver."
date: 2012-06-22
forum: General Help
---

### Post by kimme on 2012-06-22
My HTPC (ASRock Nettop ION) has had installed the latest nvidia driver and after I tried to get the overscan to work on my 32" LCD TV with an HDMI setup it stopped working. I can bootup, but not login to my own account in Ubuntu 12.04 and the funny thing is that it gets to the login screen after my failed attemp and my "Guest" account works just fine and that account I can login to.

I have tried to "Alt+Ctrl+F1" from the login screen and "sudo apt-get purge nvidia-current" and then "sudo apt-get install nvidia-current" without success. So now I'm askin....

How do I reset the driver and start all over again with the troublesome latest nvidia-current driver from the login screen, as I can't login to my own account?

---

### Post by lg21 on 2012-06-22
Boot to single user mode and: ```
sudo nvidia-xconfig

```

---

### Post by kimme on 2012-06-22
Still no go from here, and now I found out that it's the dreaded .Xauthority bug that has happened to my HTPC. An quick "sudo chown kimme:kimme ~/.Xauthority" made my login to go smooth again.... :) Now only to begin fixing the overscan bug that got me here in the first place....

---

