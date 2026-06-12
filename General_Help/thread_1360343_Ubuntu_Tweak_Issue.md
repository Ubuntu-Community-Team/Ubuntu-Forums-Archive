---
title: "Ubuntu Tweak Issue"
date: 2009-12-20
forum: General Help
---

### Post by dh04000 on 2009-12-20
I accidentally installed the karmic version of ubuntu tweak to my jaunty install.

I want to install the earlier jaunty version, because of all of the errors this newer version is causing.

But, I can't remove ubuntu tweak even with synaptic package manager.

Nor with sudo apt-get remove ubuntu-tweak.


Can someone write me a terminal command powerful enough to clean it out so I can install the earlier ubuntu-tweak in its place?

Please.

Thank you.

---

### Post by RedSingularity on 2009-12-20
What about 

sudo apt-get autoremove --purge ubuntu-tweak

---

### Post by dh04000 on 2009-12-20
Didn't work

Heres the read out

sudo apt-get remove ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-tweak
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 5063kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155856 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
devin@devin:~$

---

### Post by RedSingularity on 2009-12-20
What output do you get when trying to remove this?

---

### Post by dh04000 on 2009-12-20
Here's the read out with your code, its the same basically.

sudo apt-get autoremove --purge ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-tweak*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 5063kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155856 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
devin@devin:~$

---

### Post by RedSingularity on 2009-12-20
Well you could locate all the Ubuntu tweak items on you computer and delete them manually. 

sudo find / -name ubuntu-tweak*

---

### Post by dh04000 on 2009-12-20
Here's the readout
How do I go about deleting them all?

sudo find / -name ubuntu-tweak*
/var/lib/dpkg/info/ubuntu-tweak.list
/var/lib/dpkg/info/ubuntu-tweak.prerm
/var/lib/dpkg/info/ubuntu-tweak.md5sums
/var/lib/dpkg/info/ubuntu-tweak.conffiles
/var/lib/dpkg/info/ubuntu-tweak.postinst
/var/crash/ubuntu-tweak.0.crash
/tmp/ubuntu-tweak_0.4.8-1~jaunty1_all.deb
/home/devin/.gconf/apps/ubuntu-tweak
/etc/dbus-1/system.d/ubuntu-tweak-daemon.conf
/etc/apt/sources.list.d/ubuntu-tweak.list
/etc/apt/sources.list.d/ubuntu-tweak.list.save
/usr/bin/ubuntu-tweak-daemon
/usr/bin/ubuntu-tweak
/usr/share/locale/fo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_AU/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/el/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sq/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/mk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/cs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/vi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/eo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ms/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ml/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ru/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ja/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ro/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bg/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/jv/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/oc/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/it/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ar/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/th/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hu/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ca/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ga/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/he/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/be/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_CN/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/tr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/te/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/lt/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ko/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_GB/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/kk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nb/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/uk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt_BR/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_CA/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/de/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fy/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/gl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_TW/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ka/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/id/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/is/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fa/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/es/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sv/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/da/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/doc/ubuntu-tweak
/usr/share/python-support/ubuntu-tweak.private
/usr/share/icons/hicolor/64x64/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/48x48/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/32x32/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/24x24/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/16x16/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/22x22/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/36x36/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/96x96/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/128x128/apps/ubuntu-tweak.png
/usr/share/pixmaps/ubuntu-tweak.png
/usr/share/applications/ubuntu-tweak.desktop
/usr/share/ubuntu-tweak
/usr/share/ubuntu-tweak/ubuntu-tweak.py
/usr/share/ubuntu-tweak/data/applogos/ubuntu-tweak.png
/usr/share/ubuntu-tweak/data/pixmaps/ubuntu-tweak.png
/usr/share/ubuntu-tweak/data/pixmaps/ubuntu-tweak-64.png
devin@devin:~$

---

### Post by RedSingularity on 2009-12-20
Paste into terminal

sudo rm /usr/share/locale/fo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_AU/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/el/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sq/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/mk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/cs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/vi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/eo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ms/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ml/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ru/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ja/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ro/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bg/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/jv/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/oc/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/it/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ar/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/th/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hu/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ca/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ga/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/he/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/be/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_CN/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/tr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/te/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/lt/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ko/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_GB/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/kk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nb/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/uk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt_BR/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_CA/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/de/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fy/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/gl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_TW/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ka/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/id/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/is/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fa/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/es/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt/LC_MESSAGES/ubuntu-tweak.mo

then run the find command again and half should be gone.

---

### Post by dh04000 on 2009-12-20
it told me that permission was denied on each one.

Example:

/usr/share/locale/pt/LC_MESSAGES/ubuntu-tweak.mo: Permission denied

---

### Post by dh04000 on 2009-12-20
I think I figured it out, each item needs sudo rm individually.

---

### Post by RedSingularity on 2009-12-20
Ah i was trying to avoid that so you wouldnt have to do all that copy and pasting.

---

### Post by wilee-nilee on 2009-12-20
So when you installed ubuntu tweak it sounds like you used a ppa, if not you should, this will overwrite the karmic files general and leave you all set.
[https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)

---

### Post by dh04000 on 2009-12-20
New issue.

When i try to install the older ubuntu tweak .deb, it get this error

/tmp/ubuntu-tweak_0.4.8-1~jaunty1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.


Any ideas?

---

### Post by RedSingularity on 2009-12-20
Save it then open it.

---

### Post by dh04000 on 2009-12-20
> **RedSingularity said:**
> Ah i was trying to avoid that so you wouldnt have to do all that copy and pasting.

(In case anyone else sees this and has the same problem)

I ended up doing all of the coping and pasting, once all of the non-directory were gone, I could remove via synpatic.

Then I added the jaunty ppa and installed via sudo apt-get install ubuntu-tweak.


Now it works!

Thanks for the help guys! :)

No better place to be a linux user than here at ubuntu forums. You guys rock!

---

### Post by RedSingularity on 2009-12-20
Glad you got it working :)

---

