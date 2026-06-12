---
title: "Unable to install Ati driver"
date: 2010-05-28
forum: General Help
---

### Post by rueben on 2010-05-28
Hello,

Today (28/5/2010) ubuntu update manager showed an update for ati drivers. But the installation was stopped halfway. There was an error (installArchives() failed). After that I can't seem to uninstall and reinstall the driver. 

Can anyone help me figure out how to fix this?

Thank you in advance

---

### Post by mac9416 on 2010-05-28
What errors do you get when attempting to uninstall or reinstall the driver? Can you copy/paste them here?

---

### Post by rueben on 2010-05-28
rueben@rueben-laptop:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fglrx (2:8.732-0ubuntu0sarvatt2~lucid) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.732 DKMS files...

------------------------------
Deleting module version: 8.732
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.732 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-22-generic
Building for architecture i686
Building initial module for 2.6.32-22-generic

Error! Application of patch arch_fglrx_2.6.34.patch failed.
Check /var/lib/dkms/fglrx/8.732/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-kernel-source (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing xorg-driver-fglrx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
 fglrx-kernel-source
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rueben on 2010-05-28
Fixed it.Found the solution at [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver).

Sorry to have created a new thread and wasting your time. I'm new to ubuntu and I panicked when this happened.

---

### Post by mac9416 on 2010-05-28
Not a problem, rueben. I'm glad you found the solution. I admit I was rather stumped.  :-)

---

### Post by connellc on 2011-08-12
Fixing FGLRX using [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) ALSO helped me.

After purging FGLRX using the instructions, my screen stopped flickering, and an added benefit was I was able to get my other sound card devices back. 

(Because Ubuntu had "replaced" the "non-functioning" Realtek ALC887 soundcard,  I had also been trying to get the sound associated with my Radeon ATI R6xx graphics card - the portion with the HDMI ATI R6xx sound - working, and my screen had been already flickering at the time, so I had tried to update the Catalyst. A proprietary FGLRX was getting in the way.) 

Now that I have some access to my Realtek ALC887 soundcard, I will just work with fixing those and skip the sound on the HDMI ATI R6xx graphics card, because I don't want to mess with FGLRX anymore. 

(It was a royal PAIN  trying to read the Firefox screen in low graphics mode. It was like looking at a mad psychedelic display without the "benefits" of LSD, LOL)

I'm SO GLAD my screen does not flicker - that' s the main thang.

---

