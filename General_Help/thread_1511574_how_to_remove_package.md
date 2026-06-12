---
title: "how to remove package"
date: 2010-06-17
forum: General Help
---

### Post by morgonhed on 2010-06-17
Hi,

my 10.04 installation (that worked fine for weeks) does not boot anymore (soft lockup).

After some googling I suspect that the problem is the installation of the hostap_utils-package that I performed the last time I could use it.

I am on a Thinkpad X30 without CD-drive and don't have my docking station at hand, but fortunately I still have a working 8.04 installation on it and I from that I can mount the 10.04 partition.

So my question is: Is there a good way to remove a package from a 10.04 installation when you cannot boot it directly but have access to the filesystem?

Alternatively could someone please post all the files that belong to the hostap_utils package so I can just delete them manually (even though that probably is not a clean way to remove a package..).

Many thanks!

---

### Post by morgonhed on 2010-06-17
Ok - figured it out myself.

Here is what I did:

Mounted the 10.04 filesystem to /mnt, went to /mnt/var/chache/apt/archive (that's where the debs of the installed packages are kept), then you can find out with a "dpkg -c" what files have been installed, moved these files somewhere else. Then 10.04 booted again, finally moved the packages-files back to their previous location and removed them cleanly with "apt-get purge".

Please let me know if there would have been a better way (somehow I think I will need such a procedure again).

I must say I never had so much problems with a Linux-distro before (this is not the only issue I had with 10.04).

I mean all you do is a apt-get install and then your system won't even boot anymore? 

Come on...

---

