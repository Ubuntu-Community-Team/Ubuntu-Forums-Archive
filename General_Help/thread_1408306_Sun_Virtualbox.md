---
title: "Sun Virtualbox"
date: 2010-02-16
forum: General Help
---

### Post by Denton Larson on 2010-02-16
Hi Everybody

I am sort of a noob. I installed Sun Virtualbox and at first it worked great. But it has a problem. Do you see what I did?

I copied in the problems


failed to open a session for the virtual machine Denton OS.
Virtual machine 'Denton OS' has terminated unexpectedly during startup.

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

dlarson@dlarson-desktop-dell:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for dlarson: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
dlarson@dlarson-desktop-dell:~$ cat /var/log/vbox-install.log
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
dlarson@dlarson-desktop-dell:~$ 

Denton Larson

---

### Post by snowpine on 2010-02-16
> **Denton Larson said:**
> Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```
sudo apt-get install dkms
```

---

### Post by JKyleOKC on 2010-02-16
I suspect that what you did was to install updates that included a new kernel version. The error message tells you what to do to fix it: run this command from the terminal: ```
sudo /etc/init.d/vboxdrv setup
```When sudo asks for your password, type it in but you won't see any indication that you're doing so. Once the setup action has rebuilt the vboxdrv module, go to Synaptic and install the DKMS package. It will automatically do this rebuilding the next time your kernel gets updated. Instead of using Synaptic, you can do as snowpine suggests...

---

### Post by Denton Larson on 2010-02-16
> **snowpine said:**
> ```
sudo apt-get install dkms
```

Boy I have something goofed up.

I am running 9.04. I did have 9.10 but was way SLOOW so I got 9.04 in the box. But it is asking for 9.10. 
I am so confused.

dlarson@dlarson-desktop-dell:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  intltool-debian po-debconf libmail-sendmail-perl html2text grub-common libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/62.1kB of archives.
After this operation, 393kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter

Err cdrom://Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4) karmic/main dkms 2.1.0.1-0ubuntu1
  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
dlarson@dlarson-desktop-dell:~$ 

HELP!

Denton Larson

---

### Post by snowpine on 2010-02-16
> **Denton Larson said:**
> Boy I have something goofed up.

I am running 9.04. I did have 9.10 but was way SLOOW so I got 9.04 in the box. But it is asking for 9.10. 


I do not understand what you did here, can you explain in more detail? :) 

Anyway, you can stop it from asking for the CD by:

```
gksu gedit /etc/apt/sources.list
```

Find where it lists the CD and type a # symbol at the beginning of this line (to comment it out so it's skipped). Save the changes and try again.

---

