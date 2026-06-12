---
title: "Ubuntu 10.10, Low Graphics Mode on BOOT"
date: 2010-11-05
forum: General Help
---

### Post by _why on 2010-11-05
Hi, I've run into a problem. Yesterday, when I was about to shut down Ubuntu for the night, I noticed the screen had extended itself to the right unabling me to shut down ubuntu```

``` via the GUI. Being as tired as I was I just pressed the power switch and went to bed.

Today upon booting ubuntu from a Windows 7 Dual Boot, I'm presented with a Low Graphics Mode prompt with several options. 

Trying to boot in Low Graphics Mode results in an endles waiting with no results.

Pressing StartX leaves a black screen with a mouse in the middle. 

I have tried to search this forum for any fix and have attempted the following:

I've backed up my xorg.conf and executed ```
 sudo dpkg-reconfigure xserver-xorg
```
then rebooted, once, twice and thrice. No luck.

Uninstalled Nouveau.

Overwrote xorg.conf with ```
sudo nvidia-xconfig
``` and the file was properly set but my boot problem was not solved. 

When running ```
sudo nvidia-settings
``` I get: ```
ERROR: The control display is undefined; please run `nvidia-settings --help`
for usage information.
```

I'm about to give up. Is there a last hope so I wont have to uninstall?

Much Appreciated!

---

