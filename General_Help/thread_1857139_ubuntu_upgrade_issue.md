---
title: "ubuntu upgrade issue"
date: 2011-10-09
forum: General Help
---

### Post by gent79 on 2011-10-09
Hi,

I'm running into a problem after upgraded libstdc++. Please share your valuable ideas of how to solve such issue. 

root@reid-gent79:~# uname -a
Linux reid-gent79 2.6.32-33-generic-pae #72-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011 i686 i686 i386 GNU/Linux

root@reid-gent79:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gettext git-core latex-xft-fonts linux-generic linux-generic-pae linux-headers-generic linux-headers-generic-pae linux-image-generic
  linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up udev (173-0ubuntu3) ...
udev start/running, process 3914
info: unrecognized option '--convert-db'
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of kbd:
 kbd depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing kbd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of alsa-base:
 alsa-base depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing alsa-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kexec-tools:
 kexec-tools depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing kexec-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of media-player-info:
 media-player-info depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing media-player-info (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wireless-crda:
 wireless-crda depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing wireless-crda (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pcmciautils:
 pcmciautils depends on udev (>= 136-1); however:
  Package udev is not configured yet.
dpkg: error processing pcmciautils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 udev
 initramfs-tools
 dmsetup
 kbd
 alsa-base
 kexec-tools
 media-player-info
 wireless-crda
 pcmciautils
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

