---
title: "Flashplugin problem after using Computer Janitor"
date: 2009-12-08
forum: General Help
---

### Post by ALF102 on 2009-12-08
Ok, just now I just use the 'Computer Janitor' to clean up some stuff. Then its stuck on a file name "adobe-flashplugin" which I did not spot because there were many other files as well. Thus it cause the adobe-flashplugin to lost its archive. When I try to reinstall, the installer gave me an error. 

    Then I notice that when I open the update manager, I receive the "partial upgrade" that tells me that not all updates can be install. So I click partial upgrade and it try to fix the problem, then I get this message:

The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?


  So, I click on "Yes"

Here's the terminal log of the partial upgrade:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 148270 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin
update-alternatives: error: no alternatives for iceape-flashplugin
dpkg: error processing adobe-flashplguin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument 'abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Error were encountered while processing:
 adobe-flashplugin

After that I get the following message:

The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.


What to do? I cannot even install it from the deb package.

---

### Post by ALF102 on 2009-12-09
I guess no ones want to help huh?

---

### Post by MelDJ on 2009-12-09
in terminal try sudo apt-get remove adobe-flashplugin
then reinstall
be patient. some of us don't get replies for weeks. ;)

---

### Post by ALF102 on 2009-12-10
Ok, I did what you've told and this came up in the terminal:

~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

After that, I install it, which didn't succed because of the following error message:

[B]Could not open 'install_flash_player_10_linux.deb'
[/B]  The package might be corrupted or you are not allowed to open the file.
  Check the permission of the file.

And to think I've just newly download this deb package few minutes after that.

---

### Post by ALF102 on 2009-12-10
Ok, I did what you've told and this came up in the terminal:

~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

After that, I install it, which didn't succed because of the following error message:

[B]Could not open 'install_flash_player_10_linux.deb'
[/B]  The package might be corrupted or you are not allowed to open the file.
  Check the permission of the file.

And to think I've just newly download this deb package few minutes after that.

---

### Post by MelDJ on 2009-12-10
try this thread [http://ubuntuforums.org/archive/index.php/t-1203768.html](http://ubuntuforums.org/archive/index.php/t-1203768.html)
or if that doesn't work, try [http://ubuntuforums.org/showthread.php?t=1285455](http://ubuntuforums.org/showthread.php?t=1285455)

---

### Post by ALF102 on 2009-12-11
Oh thank you thank you thank you, its now fixed. I only did it halfway from all the steps I followed in your links and its fixed. BTW, I'm from Perak

---

