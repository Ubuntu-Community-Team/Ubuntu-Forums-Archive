---
title: "Ubuntu 12.04 - Desktop messed up"
date: 2012-04-27
forum: General Help
---

### Post by BHXSpecter on 2012-04-27
I upgraded from 11.10 to 12.04 and first it had the login screen just showed a paper with an red 'x' by my name and in the top right corner. Then it finally let me log in but it was so the icons on the menu bar were gray square with no icons, the desktop icons were just white squares and none of the windows had any title bars or min/max/close buttons. I did ubuntu-bug lightdm but didn't know if I needed to run any other commands.
> 
ProblemType: Bug
ApportVersion: 1.23-0ubuntu4
Architecture: amd64
Date: Fri Apr 27 19:38:00 2012
Dependencies:
 adduser 3.112+nmu1ubuntu5
 base-passwd 3.5.24
 busybox-initramfs 1:1.18.5-1ubuntu4
 coreutils 8.5-1ubuntu6
 cpio 2.11-7ubuntu1
 dbus 1.4.14-1ubuntu1
 debconf 1.5.42ubuntu1
 debianutils 4.2.1ubuntu2
 dpkg 1.16.1.2ubuntu7
 findutils 4.4.2-1ubuntu3
 gcc-4.6-base 4.6.3-1ubuntu5
 ifupdown 0.7~alpha5.1ubuntu5.1
 initramfs-tools 0.99ubuntu13
 initramfs-tools-bin 0.99ubuntu13
 initscripts 2.88dsf-13.10ubuntu11
 insserv 1.14.0-2.1ubuntu2
 iproute 20110315-1build1
 klibc-utils 1.5.25-1ubuntu2
 libacl1 2.2.51-5ubuntu1
 libattr1 1:2.4.46-5ubuntu1
 libblkid1 2.20.1-1ubuntu3
 libbz2-1.0 1.0.6-1
 libc-bin 2.15-0ubuntu10
 libc6 2.15-0ubuntu10
 libdb5.1 5.1.25-11build1
 libdbus-1-3 1.4.18-1ubuntu1
 libdrm-intel1 2.4.32-1ubuntu1
 libdrm-nouveau1a 2.4.32-1ubuntu1
 libdrm-radeon1 2.4.32-1ubuntu1
 libdrm2 2.4.32-1ubuntu1
 libelf1 0.152-1ubuntu3
 libexpat1 2.0.1-7.2ubuntu1
 libffi6 3.0.11~rc1-5
 libgcc1 1:4.6.3-1ubuntu5
 libglib2.0-0 2.32.1-0ubuntu2
 libklibc 1.5.25-1ubuntu2
 liblzma2 5.0.0-2
 libmount1 2.20.1-1ubuntu3
 libncurses5 5.9-4
 libncursesw5 5.9-4
 libnih-dbus1 1.0.3-4ubuntu9
 libnih1 1.0.3-4ubuntu9
 libpam-modules 1.1.3-7ubuntu2
 libpam-modules-bin 1.1.3-7ubuntu2
 libpam-runtime 1.1.3-2ubuntu2.1
 libpam0g 1.1.3-7ubuntu2
 libpciaccess0 0.12.902-1
 libpcre3 8.12-4
 libplymouth2 0.8.2-2ubuntu30
 libpng12-0 1.2.46-3ubuntu4
 libselinux1 2.1.0-4.1ubuntu1
 libslang2 2.2.4-2ubuntu1
 libtinfo5 5.9-4
 libudev0 175-0ubuntu9
 libuuid1 2.20.1-1ubuntu3
 libxau6 1:1.0.6-4
 libxcb1 1.8.1-1
 libxdmcp6 1:1.1.0-4
 lsb-base 4.0-0ubuntu20
 makedev 2.3.1-89ubuntu2
 module-init-tools 3.16-1ubuntu2
 mount 2.20.1-1ubuntu3
 mountall 2.36
 multiarch-support 2.13-20ubuntu5.1
 ncurses-bin 5.9-4
 netbase 4.45ubuntu3
 passwd 1:4.1.4.2+svn3283-3ubuntu5
 perl-base 5.14.2-6ubuntu2
 plymouth 0.8.2-2ubuntu30
 procps 1:3.2.8-10ubuntu5
 sed 4.2.1-9
 sensible-utils 0.0.6ubuntu2
 sysv-rc 2.88dsf-13.10ubuntu11
 sysvinit-utils 2.88dsf-13.10ubuntu4.1
 tar 1.25-3
 tzdata 2012b-0ubuntu0.11.10
 udev 173-0ubuntu4.2
 upstart 1.5-0ubuntu5
 util-linux 2.19.1-2ubuntu3
 xz-utils 5.0.0-2
 zlib1g 1:1.2.3.4.dfsg-3ubuntu4
DistroRelease: Ubuntu 12.04
InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
NonfreeKernelModules: nvidia
Package: lightdm 1.0.6-0ubuntu1.6
PackageArchitecture: amd64
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 3.0.0-17.30-generic 3.0.22
SourcePackage: lightdm
Tags:  precise
Uname: Linux 3.0.0-17-generic x86_64
UpgradeStatus: Upgraded to precise on 2012-04-27 (0 days ago)



---

### Post by mace2 on 2012-04-27
Same thing happened to me, tried to update my GF's laptop. Except on the desktop her mouse wouldn't work. Ended up having to reformat and put a fresh install on and it worked then.

---

### Post by BHXSpecter on 2012-04-28
Yeah, I thought that would be the solution. Not worth the effort and the annoyance of losing everything. The GUI may be ugly and the login menu may still say 11.10 with red 'x' in two spots (and resolution may be off a little), but I'll just deal with it.

[REVISION]
Had to break down and do a fresh install with a USB that had 12.04 on it. I couldn't back anything up so I am glad that all my programming things were on a separate drive.

---

