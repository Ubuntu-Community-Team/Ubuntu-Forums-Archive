---
title: "Adobe Flash Player Plugin?"
date: 2012-08-02
forum: General Help
---

### Post by Coolmariorocks on 2012-08-02
I have the ubuntu adobe flash player plugin from the software centre.. and By the way i am on ubuntu 10.10 since this computer can't handle the newer ubuntu.. :|.  I'm wondering how do i do a clean install of the flash player plugin? I know to uninstall it but is there a profile folder that it is in that i should delete after the sudo apt-get remove of it? I removed the flash player plugin in the past to see if it would fix the problem i am having on browsers that need it like firefox, opera.. but chrome don't need it as it has built in flash player.

---

### Post by Dylan1473 on 2012-08-02
I don't know if this would actually fix the issue but you can usually *fully* uninstall things (config files and all) with the command ```
sudo apt-get --purge remove [package name]
```

EDIT: Somewhat off-topic, but you mention your computer can't handle the newer Ubuntu. This is probably mostly an issue of your desktop environment - have you tried using a lighter weight one such as XFCE, LXDE or (if you're a more advanced user and interested in/willing to put the effort into lots of customization) Openbox?

---

