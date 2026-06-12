---
title: "Synaptic is broken because of brscan3 and apt-get install anything doesnt work"
date: 2010-08-14
forum: General Help
---

### Post by shaiss on 2010-08-14
I was installing my brother printer and tried setting up the scanner with brscan3.  The install failed and now I can't remove it.  any help?

> shai@ShaiGarage64:~/downloads$ sudo dpkg --remove --force-remove-reinstreq brscan3
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 90387 files and directories currently installed.)
Removing brscan3 ...
grep: /etc/sane.d/dll.conf: No such file or directory
mv: cannot stat `/etc/sane.d/dll.conf': No such file or directory
/usr/local/Brother/sane/setupSaneScan3: 26: cannot create /etc/sane.d/dll.conf: Directory nonexistent
cat: /etc/sane.d/dll.conf.tmp: No such file or directory
dpkg: error processing brscan3 (--remove):
 subprocess installed pre-removal script returned error exit status 2
grep: /etc/sane.d/dll.conf: No such file or directory
/usr/local/Brother/sane/setupSaneScan3: 26: cannot create /etc/sane.d/dll.conf: Directory nonexistent
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 brscan3

This is what I get when I try to install anything:
> shai@ShaiGarage64:~/downloads$ sudo aptitude install linux-headers-2.6-amd64The following NEW packages will be installed:
  cpp-4.3{a} gcc-4.3{a} gcc-4.3-base{a} linux-headers-2.6-amd64 
  linux-headers-2.6.32-5-amd64{a} linux-headers-2.6.32-5-common{a} 
  linux-kbuild-2.6.32{a} 
The following partially installed packages will be configured:
  brscan3 
0 packages upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 35.6MB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the brscan3 package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the brscan3 package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
shai@ShaiGarage64:~/downloads$ 


I solved it with the help of this post
[http://ubuntuforums.org/showpost.php?p=9212413&postcount=17](http://ubuntuforums.org/showpost.php?p=9212413&postcount=17)
> sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

replace flashplugin-nonfree with brscan3 and rm -rf the directories aptitude can't remove.

---

