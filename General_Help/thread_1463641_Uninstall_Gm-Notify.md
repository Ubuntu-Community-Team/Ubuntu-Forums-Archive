---
title: "Uninstall Gm-Notify"
date: 2010-04-27
forum: General Help
---

### Post by Xorlathor on 2010-04-27
I installed gm-notify ([https://launchpad.net/gm-notify](https://launchpad.net/gm-notify)) using the setup.py file that came with it, I no longer have any use for it and want to install it - how can I? 

I deleted the following - 

in /usr/share/applications delete:
gm-notify.desktop
gm-notify-config.desktop

in /usr/local/lib/python2.6/dist-packages:
gmailatom.*
gm_notify*
gmxdgsoundlib.*
keyring.*

in /usr/local/bin:
gm-notify-config.py
gm-notify.py
(set-gmail-password.py)

and those files:
/usr/share/locale/da/LC_MESSAGES/gm-notify.mo
/usr/share/locale/de/LC_MESSAGES/gm-notify.mo
/usr/share/locale/ca/LC_MESSAGES/gm-notify.mo

delete Folder: /usr/share/gm-notify


What else do I do? There's still an icon in the menu under applications/other/google mail, and also in system/preferences/ gmail notifier configuration, and I can't remove them via the "edit menus" command. Any help?

---

### Post by bapoumba on 2010-04-27
I gather you did not install it form the ppa archive. What steps did you have to perform to use the setup.py file? (I did not look into it)
It may be easier to activate the ppa archive, install it with a package manager (synaptic, apt-get, aptitude) and then uninstall it.

---

### Post by Xorlathor on 2010-04-27
> **bapoumba said:**
> I gather you did not install it form the ppa archive. What steps did you have to perform to use the setup.py file? (I did not look into it)
It may be easier to activate the ppa archive, install it with a package manager (synaptic, apt-get, aptitude) and then uninstall it.

Good idea, I think I'll try to uninstall it via the ppa and then use synaptic.

---

### Post by bapoumba on 2010-04-27
> **Xorlathor said:**
> Good idea, I think I'll try to uninstall it via the ppa and then use synaptic.

Once you have loaded the ppa, first install it. If you have any error, please paste the output in here. If no error, then remove it :)

---

### Post by Xorlathor on 2010-04-27
> **bapoumba said:**
> Once you have loaded the ppa, first install it. If you have any error, please paste the output in here. If no error, then remove it :)

Fixed by adding the PPA and then removing. Thanks for your help!

---

### Post by bapoumba on 2010-04-27
Glad to see you sorted it out!

---

### Post by flegma9 on 2010-06-09
Hi guys - I'm new on linux and have the same problem. Is there some kind of tutorial how to uninstall it via the ppa. Thanx!

---

