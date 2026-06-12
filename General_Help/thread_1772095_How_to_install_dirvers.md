---
title: "How to install dirvers"
date: 2011-05-31
forum: General Help
---

### Post by judoka1113 on 2011-05-31
I'm trying to install drivers for my Ralink 2573 USB rt73usb ethrnet card; however when I go to the cite and download them then extract them go to the Module folder and do ~$make I get this[HTML]make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
rt73.ko failed to build!
make: *** [module] Error 1
[/HTML]
What should I do?

---

### Post by mastablasta on 2011-05-31
i think you need to install building tools first before you can build. probably *build-essential* but maybe also some other things.
 
Is there no readme file that is in the drivers package? usually these say what tool you need or ther eis instruction on their website site.

---

### Post by judoka1113 on 2011-05-31
I installed GNOME build tools to make GNOME modules and found the site that explains how to install so I followed the instructions and did:
[B]Blacklist the mac80211-based rt73usb & rt* drivers to avoid conflicts
[/B]create a new file in /etc/modprobe.d called blacklist-rt73.conf
 	Code:
 	sudo nano /etc/modprobe.d/blacklist-rt73.conf 
and paste the following in it:
 	Code:
 	# Blacklist rt73usb (mac80211) as it's beta and conflicts with the 
#  stable ieee80211 based rt73 module
blacklist rt73usb

# Other modules that possibly conflict with rt73
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt2x00usb 
**Download the latest version of the RT73 USB Enhanced Driver**
(in your home directory or in /tmp or wherever you like, it will no longer be needed after)
 	Code:
 	wget [http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.3.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.3.tar.bz2)
tar xjf rt73-k2wrlz-3.0.3.tar.bz2
cd rt73-k2wrlz-3.0.3 
you should now be in the top-level directory you just extracted ( rt73-k2wrlz-3.0.3 )

**Prepare DKMS config**
create a file in rt73-k2wrlz-3.0.3 directory, called dkms.conf
 	Code:
 	nano dkms.conf 
and paste the following in it:
 	Code:
 	PACKAGE_NAME="rt73-k2wrlz"
PACKAGE_VERSION="3.0.3"

# make sure kernel is 2.6.27 or newer, just in case
# [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)
BUILD_EXCLUSIVE_KERNEL="2.6.(27|28|29|[3-9][0-9])"

MAKE[0]="make -C Module"
CLEAN="make -C Module clean"

BUILT_MODULE_NAME[0]="rt73"
BUILT_MODULE_LOCATION[0]="Module"
DEST_MODULE_LOCATION[0]="/kernel/drivers/net/wireless"

AUTOINSTALL="yes" 
**Create a traball archive of the source directory** (with our dkms.conf in it)
 	Code:
 	tar czf rt73-k2wrlz-3.0.3-dkms.tar.gz rt73-k2wrlz-3.0.3 
**Load the rt73-k2wrlz tarball to DKMS source tree**
 	Code:
 	sudo dkms ldtarball --archive=rt73-k2wrlz-3.0.3-dkms.tar.gz 
but when I get to this line and do:

**Build rt73 module with DKMS**
 	Code:
 	sudo dkms build -m rt73-k2wrlz -v 3.0.3 
I get:
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-28-generic -C Module....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-28-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.
0
0
ERROR: binary package for rt73-k2wrlz: 3.0.3 not found


Any ideas what to do now?

---

