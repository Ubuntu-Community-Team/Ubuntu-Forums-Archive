---
title: "Broken update and wierd behavior with symlinks"
date: 2010-09-09
forum: General Help
---

### Post by jabeavers on 2010-09-09
I updated my Xubuntu 10.04 yesterday and some packages had errors on install. I think I have tracked it down to python2.6 install. I ran apt-get install mousepad just to see the errors and this is part of what it returned:

0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
15 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up update-manager-core (1:0.134.10) ...
file does not exist: /usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeApport.py
file does not exist: /usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeAptCdrom.py
file does not exist: /usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeAufs.py
file does not exist: /usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py
...
file does not exist: /usr/lib/python2.6/dist-packages/computerjanitor/plugin_tests.py
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 1
...
Errors were encountered while processing:
 update-manager-core
 gdebi-core
 gdebi
 gdebi-kde
 jockey-common
 jockey-gtk
 python-aptdaemon
 aptdaemon
 python-aptdaemon-gtk
 software-center
 update-manager
 update-manager-kde
 packagekit-backend-apt
 packagekit
 kpackagekit
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then, I checked where it said the missing files were and found several broken symlinks like this:

lrwxrwxrwx 1 root root     33 2010-08-09 20:34 xapian.py -> ../../../share/pyshared/xapian.py

All of the broken symlinks need another ../ on the front. I was considering creating a script that will read the broken symlinks, add another ../ on the front of the target and then change the symlink target to that address.

Is there an easier way to fix this, like, reinstall some program??

Thanks,
John

---

### Post by sikander3786 on 2010-09-09
Have you tried this.

```


sudo apt-get clean

sudo apt-get install -f

sudo dpkg --configure -a

```

Search for broken packages in Synaptic and try to fix them.

---

### Post by jabeavers on 2010-09-09
That didn't seem to do anything. When I apply the filter in synaptic for broken packages it shows none.

---

### Post by sikander3786 on 2010-09-09
Seems to be a bug.

[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/366304](https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/366304)

---

### Post by jabeavers on 2010-09-09
Thanks, I think I'll try to fix with a script that will fix the broken links. I'll let you know how it goes and post the script if it works.

---

### Post by jabeavers on 2010-09-09
Ok, I made my script that fixed all the broken links and the packages with errors install and configured just fine. Here is my script:

#!/bin/bash

fixLink(){
        FILE="$1"
        TARGET=`readlink $FILE`
        TARGET="../$TARGET"
        ln -f -s $TARGET $FILE
}

find $1 -type l | (while read FN ; do test -e "$FN" || fixLink "$FN" ; done )
exit 0


Of course, back up your files before attempting and take all necessary precautions. You pass the directory in python2.6 that has the broken links; mine was /usr/lib/python2.6/dist-packages. So my command looked like this:

fixPy2.6Links /usr/lib/python2.6/dist-packages/

Hope this helps someone. Thanks for you all's help. Later.

---

