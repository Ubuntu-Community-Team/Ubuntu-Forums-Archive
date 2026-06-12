---
title: "ubuntu 9.10  install shoots out errrors."
date: 2010-03-07
forum: General Help
---

### Post by hockey97 on 2010-03-07
This is what happened. I installed apache2 and then replaces the files with the config files already made before.In other words I was doing a restore manually by replacing the files. I got errors saying can't run apache2 due to the config file on line 142 not being proper syntax. 

so then I decided to delete all apache2 and start over again.

I ran : ```
apt-get remove --purge apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert
```

After doing that I seen it delete  all that and plus more stuff I didn't ask it to. LIke ubuntu-desktop and many other stuff.

Now I installed ubuntu-desktop back and reboot the computer just to see if I get it back working good. I then installed apache2 and  php 5 and other files I know that deleted extra but didn't know about the rest that were deleted but don't remeber what all got deleted just some. 

I now get the errors below when you try to install anything on ubuntu.

it will delete the stuff but never install it back. I deleted apache2 again to reinstall it cuz I know some files were missing. So now when I tried to install it again I got this error for anything being installed.



This is what the errors are : ```
E: apache2.2-common: subprocess installed post-installation script returned error exit status 1
E: apache2-mpm-prefork: dependency problems - leaving unconfigured
E: libapache2-mod-php5: dependency problems - leaving unconfigured
E: php5: dependency problems - leaving unconfigured
E: php5-mysql: dependency problems - leaving unconfigured
E: php5-ffmpeg: dependency problems - leaving unconfigured
E: php5-gd: dependency problems - leaving unconfigured
E: php5-geoip: dependency problems - leaving unconfigured


```


How do I fix this? Is there anything I can run?

---

