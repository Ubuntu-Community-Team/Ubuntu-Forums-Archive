---
title: "Apt-get error preventing any package management"
date: 2009-11-27
forum: General Help
---

### Post by mm144 on 2009-11-27
I'm running kubuntu 9.10 
and when i am trying to update, install, re-install, or even uninstall packages, i receive an error of
E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. 
i realise what it's saying but i have tried re-installing, and uninstalling  and even dpkg --purge. 

dpkg: error processing adobe-flashplugin (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

anyone have any ideas?

---

### Post by sgosnell on 2009-11-27
Try installing it from the Adobe site.  That has always worked better for me.  Just go to abobe.com, click on Get Adobe Flash Player, and select the Ubuntu .deb.  It should install.

---

### Post by mm144 on 2009-11-27
I have tried that but because of that error, it refuses to install anything.  KPackageKit fails to function as a result as well.

When i try to run sudo dpkg - i installadobeflash.deb

pdate-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb


when i try this command as the man page suggests:

 sudo dpkg   --purge --force-remove-reinstreq  adobe-flashplugin
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 85736 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin

actually the above command is an extrapolation based on the man page because 
 sudo dpkg --force-remove-reinstreq  adobe-flashplugin
gives me....
dpkg: need an action option

---

### Post by peterroots on 2009-12-07
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)

does post number 8 here help? This or a variation on it to match your situation exactly may do the trick

---

