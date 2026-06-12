---
title: "How to stop GUI from loading"
date: 2012-01-09
forum: General Help
---

### Post by viswanathk on 2012-01-09
Hello,

How do I stop the Xserver or lightdm from loading in Ubuntu 11.10. I am planning on making my computer a server, so I wouldn't need it. For the info I can't find /etc/inittab in Ubuntu. I read in my unix class that it contains the run levels  which I can edit :(

---

### Post by prshah on 2012-01-10
> **viswanathk said:**
> 
How do I stop the Xserver or lightdm from loading in Ubuntu 11.10. I am planning on making my computer a server, so I wouldn't need it. For the info I can't find /etc/inittab in Ubuntu. I read in my unix class that it contains the run levels  which I can edit :(

Ubuntu 10.10 and above use upstart to control runlevels, and not System V type init scripts as you are studying.

You will have to check in the "/etc/init" directory for the correct script to disable in order to stop lightdm loading. I do not know which script will be correct for lightdm, but for gnome, you should look at /etc/init/gdm.conf.

NOT SURE: Since upstart allows userspace controlling of init, you can also disable it with a command similar to ```
sudo service gdm disable
```

---

