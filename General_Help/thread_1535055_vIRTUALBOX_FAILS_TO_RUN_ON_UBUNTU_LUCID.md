---
title: "vIRTUALBOX FAILS TO RUN ON UBUNTU LUCID"
date: 2010-07-20
forum: General Help
---

### Post by winpras on 2010-07-20
Right from when I upgraded my linux from jaunty to lucid,  Virtualbox(PUEL) failed to open. Following errors were displayed >   p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

I have tried ixing the issue but never managed to..  and have loked in several forums but never found any relevant discussion on this issue,.,,

However when I uninstalled PUEL version of virtual box and installed ose version, virtualbox opens without any hassles....

How to make PUEL version work on Lucid....   I am comfortable with PUEL as I connect usb devices....

---

### Post by Vaphell on 2010-07-20
i use vbox from oracle provided repos just fine
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
more here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

remove any trace of vbox and install it from scratch. upgrade probably messed up something.


also this may help (from that vbox page)
Note: Ubuntu users might want to install the dkms  package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the linux kernel version changes during the next apt-get upgrade. The dkms package can be installed through the Synaptic Package manager or through the following command:

---

