---
title: "need help getting Unity login screen back"
date: 2012-04-06
forum: General Help
---

### Post by petermg on 2012-04-06
I don't know how I did it, but after messing with Compiz settings, trying to install a different driver for my ATI chip, I no longer have the unity login screen, it's the GDM one.  Yes I installed GDM, but even when I uninstall GDM I can't get any login screen back, even though Unity is installed.  HELP! I'm on 11.10 ubuntu.

Thank you.

---

### Post by davidnottingham on 2012-06-17
sudo dpkg-reconfigure lightdm

Will prompt you to make it default. More information here:

    [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

courtesy of Jorge Castro

[http://askubuntu.com/questions/58023/how-can-i-make-lightdm-the-default-display-manager](http://askubuntu.com/questions/58023/how-can-i-make-lightdm-the-default-display-manager)

---

