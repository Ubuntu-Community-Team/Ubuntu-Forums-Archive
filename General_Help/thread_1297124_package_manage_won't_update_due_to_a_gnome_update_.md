---
title: "package manage won't update due to a gnome update that will not install or uninstall"
date: 2009-10-21
forum: General Help
---

### Post by loom232 on 2009-10-21
I am tld there is 1 update available.for gone - games - data. I try to update it using update manager but it refuses to install or uninstall

I get: 

E: /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb: subprocess new pre-removal script returned error exit status 1


sa result Iam unable to add or remove any programs as I keep getting refered back to the update situation.

You can see I m new o this sysytem. Any help would be appreciated

thanks

---

### Post by DeMus on 2009-10-21
> **loom232 said:**
> I am tld there is 1 update available.for gone - games - data. I try to update it using update manager but it refuses to install or uninstall

I get: 

E: /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb: subprocess new pre-removal script returned error exit status 1


sa result Iam unable to add or remove any programs as I keep getting refered back to the update situation.

You can see I m new o this sysytem. Any help would be appreciated

thanks

Open a terminal: Applications -> Accessories -> Terminal and type
```
sudo apt-get --configure -a
```
Type your password
This will clean up your broken install.

---

### Post by loom232 on 2009-10-21
Thanks for the help ....I tried that command afew times and ll i got was

E: Command line option --configure is not understood
michael@TOSHIBA-User:~$

Have i done sthg wrong?

Any other ideas 

tks

---

