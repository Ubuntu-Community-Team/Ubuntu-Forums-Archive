---
title: "Need to reinstall ubuntu-desktop, gnome-terminal, gnome-core but synaptic wont let me"
date: 2012-01-14
forum: General Help
---

### Post by landstander on 2012-01-14
System Specs:
Netbook: ASUS EeePC 1005PR-PU17-BK
RAM: Full (2GB)
OS: Ubuntu 10.04 (64bit)

Problem (short description):
----------------------------
I had to purge gnome-terminal due to a severe problem, in order to purge it synaptic said I also had to remove ubuntu-desktop, and gnome-core. After that was done, attempting to reinstall those files resulted in synaptic reporting Authentication Errors and gave 404 errors when trying to contact any of the repositories for any of these files. 

Problem (longer description):
-----------------------------
Synaptic reports the following errors:

> 
"NOT AUTHENTICATED..."
fuse-utils (version 2.8.1-1.1ubuntu3.1) will be installed
gnome-terminal (version 2.30.2-0ubuntu1) will be installed
gnome-terminal-data (version 2.30.2-0ubuntu1) will be installed
gvfs-fuse (version 1.6.1-0ubuntu1build1) will be installed
ubuntu-desktop (version 1.197) will be installed"

W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/pool/main/f/fuse/fuse-utils_2.8.1-1.1ubuntu3.1_amd64.deb](http://mirrors.cat.pdx.edu/ubuntu/pool/main/f/fuse/fuse-utils_2.8.1-1.1ubuntu3.1_amd64.deb)
  404  Not Found

W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb](http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb)
  404  Not Found

W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.30.2-0ubuntu1_amd64.deb](http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.30.2-0ubuntu1_amd64.deb)
  404  Not Found

W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.6.1-0ubuntu1build1_amd64.deb](http://mirrors.cat.pdx.edu/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.6.1-0ubuntu1build1_amd64.deb)
  404  Not Found

W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.197_amd64.deb](http://mirrors.cat.pdx.edu/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.197_amd64.deb)
  404  Not Found


Synaptic also give the following errors when trying to "reload" or Update the sources list:
> 
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/main/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/restricted/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/universe/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/main/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://mirrors.cat.pdx.edu/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


Questions:
----------
How can I solve this problem and get the necessary files reinstalled? 

Note: I am assuming that the only reason I am able to type this is due to my previous GUI session still being active. I am also assuming that I have no terminal access since gnome-terminal has also been uninstalled. I am making this post from the computer that has the problem so my Internet connection is not the problem.

Does this mean I will no longer have access to a working OS if my computer shuts down? Is there a way to fix this using the currently active GUI interface, synaptic, and gedit?

Thanks.

---

### Post by cortman on 2012-01-14
What DE are you currently using?

Any other DE comes with its own terminal emulator, so you should be able to get terminal access.
As far as not being able to download packages, can you confirm that you're online?
If so, try changing your mirrors. [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by landstander on 2012-01-14
cortman

Thank you for your quick response.
What is a DE?

I just checked and yes, that was the problem. I had forgotten that I had manually set the server in synaptic or that I could even do that in synaptic.

The files are now, magically authenticated, and are downloading and being installed.

PROBLEM SOLVED!!! :)
Thank you. :)

---

### Post by cortman on 2012-01-14
> **landstander said:**
> cortman

Thank you for your quick response.
What is a DE?

I just checked and yes, that was the problem. I had forgotten that I had manually set the server in synaptic or that I could even do that in synaptic.

The files are now, magically authenticated, and are downloading and being installed.

PROBLEM SOLVED!!! :)
Thank you. :)

Glad to know it was that simple! Enjoy Ubuntu!

Oh, and DE stands for "Desktop Environment". Gnome, Unity, KDE, XFCE, LXDE, E17, etc., are all DE's. A graphical layer over the base UI.

---

