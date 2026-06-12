---
title: "Installing Xen-4.0.1 on Ubuntu 10.10"
date: 2011-01-29
forum: General Help
---

### Post by hirantha on 2011-01-29
I'm trying to install Xen-4.0.1. on Ubuntu 10.10. Once I run the "make world" after few minutes following error appears in the console.

[COLOR="SeaGreen"]make -f buildconfigs/mk.linux-2.6-pvops build
make[3]: Entering directory `/home/hirantha/xen-4.0.1'
set -ex; \
	if ! [ -d linux-2.6-pvops.git ]; then \
		rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp; \
		mkdir linux-2.6-pvops.git.tmp; rmdir linux-2.6-pvops.git.tmp; \
		git clone -o xen -n git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-pvops.git.tmp; \
		(cd linux-2.6-pvops.git.tmp; git checkout -b xen/stable-2.6.32.x xen/xen/stable-2.6.32.x ); \
		mv linux-2.6-pvops.git.tmp linux-2.6-pvops.git; \
	fi
+ '[' -d linux-2.6-pvops.git ']'
+ rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp
+ mkdir linux-2.6-pvops.git.tmp
+ rmdir linux-2.6-pvops.git.tmp
+ git clone -o xen -n git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-pvops.git.tmp
Initialized empty Git repository in /home/hirantha/xen-4.0.1/linux-2.6-pvops.git.tmp/.git/
fatal: Unable to look up git.kernel.org (port 9418) (Name or service not known)
make[3]: *** [linux-2.6-pvops.git/.valid-src] Error 128
make[3]: Leaving directory `/home/hirantha/xen-4.0.1'
make[2]: *** [linux-2.6-pvops-install] Error 2
make[2]: Leaving directory `/home/hirantha/xen-4.0.1'
make[1]: *** [install-kernels] Error 1
make[1]: Leaving directory `/home/hirantha/xen-4.0.1'
make: *** [world] Error 2[/COLOR]

Could some one please help me to solve this problem?

Note: I dont have the internet connection @ home.

---

