---
title: "Cannot install Flash: Error 139 from DPKG"
date: 2011-05-12
forum: General Help
---

### Post by matsonfamily on 2011-05-12
I tried to install Flash (flashplugin-installer) via Synaptic, and it failed with an error, so I tried via command-line (apt-get), and got the same error.  Trying with Aptitude gave me the longer error, below, but same error 139 from dpkg.  I've tried removing (can only do so with dpkg), and using aptitude or apt-get to autoclean & autoremove, but still get the error.  I really need the official Flash.  

Thanks!  

P.S.: I've seen plenty of posts with similar titles, but haven't found one with a solution.  If you find it, please post the link, and I'll check it out!

```
matson@workstation4:~$ sudo aptitude install flashplugin-installer 
The following NEW packages will be installed:
  nspluginwrapper{a} 
The following partially installed packages will be configured:
  flashplugin-installer 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 175 kB of archives. After unpacking 582 kB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/multiverse nspluginwrapper amd64 1.2.2-0ubuntu9 [175 kB]
Fetched 175 kB in 1s (124 kB/s)          
Selecting previously deselected package nspluginwrapper.
(Reading database ... 171124 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu9_amd64.deb) ...
Processing triggers for man-db ...
Setting up nspluginwrapper (1.2.2-0ubuntu9) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Segmentation fault
dpkg: error processing nspluginwrapper (--configure):
 subprocess installed post-installation script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on nspluginwrapper (>= 0.9.91.4-2ubuntu1); however:
  Package nspluginwrapper is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 nspluginwrapper
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nspluginwrapper (1.2.2-0ubuntu9) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Segmentation fault
dpkg: error processing nspluginwrapper (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on nspluginwrapper (>= 0.9.91.4-2ubuntu1); however:
  Package nspluginwrapper is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
 flashplugin-installer
                                         
Current status: 0 broken [-1].

```

---

### Post by matsonfamily on 2011-05-12
it seems to be an error with configuring nspluginwrapper?

---

### Post by oldos2er on 2011-05-12
Try FlashAid, [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by zealibib slaughter on 2011-05-12
Have you tried to install nspluginwrapper first then trying to install flashplayer, I doubt it will work but its worth a try.

---

### Post by matsonfamily on 2011-05-13
> **zealibib slaughter said:**
> Have you tried to install nspluginwrapper first then trying to install flashplayer, I doubt it will work but its worth a try.

Thanks, but I have already tried that.  I get the configuration error listed above when trying to install nspluginwrapper 1st, as well.

---

### Post by matsonfamily on 2011-05-13
> **oldos2er said:**
> Try FlashAid, [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Works.  Thanks!  But I still have the problem with Synaptic / DPKG / Apt-Get / Aptitude, that I want to solve.

---

### Post by finderlite on 2011-05-16
I have similar problem (kubuntu 64 bit). And I resolved:
Need delete google-talkplugin and install flashplugin-installer again. :) Good Luck!

---

### Post by matsonfamily on 2011-05-16
> **finderlite said:**
> I have similar problem (kubuntu 64 bit). And I resolved:
Need delete google-talkplugin and install flashplugin-installer again. :) Good Luck!

I want to try it the same way you did... how did you delete the google-talkplugin?  Thanks!!  :)

---

### Post by matsonfamily on 2011-05-16
> **finderlite said:**
> I have similar problem (kubuntu 64 bit). And I resolved:
Need delete google-talkplugin and install flashplugin-installer again. :) Good Luck!

This is amazing... I just decided to do what you did, the standard apt-get way, and it works!  **How in the heck did you figure this out???  I have seen nothing leading to the google-talkplugin.  THANKS!**  :D

---

### Post by john.oneill on 2011-05-19
WOW - same process solved my issue

sudo apt-get remove google-talkplugin

nspluginwrapper, flashplugin-installer and flashplugin-nonfree installed immediately and are working again!

Yeah!

---

### Post by briguy on 2011-05-23
Worked for me too!  Thanks!

---

### Post by bep7987 on 2011-05-25
So can you re-install the google talk plug-in after installing flash, or does it still conflict?

---

