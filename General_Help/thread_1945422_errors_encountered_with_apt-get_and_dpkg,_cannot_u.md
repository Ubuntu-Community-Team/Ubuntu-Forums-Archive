---
title: "errors encountered with apt-get and dpkg, cannot upgrade/install/autoremove"
date: 2012-03-23
forum: General Help
---

### Post by Zaszzz on 2012-03-23
I've encountered this problem and searched and tried many of the  suggestions I've found to no avail. This occurs on Lucid,  2.6.32-39-generic. 

For example, sudo apt-get autoremove gives:
```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pidgin-data
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
11 not fully installed or removed.
Need to get 0B/610kB of archives.
After this operation, 27.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libopenal1' missing, assuming package has no files currently installed.
(Reading database ... 479634 files and directories currently installed.)
Preparing to replace screen 4.0.3-14ubuntu1.2 (using .../screen_4.0.3-14ubuntu1.2_i386.deb) ...
Unpacking replacement screen ...
dpkg: error processing /var/cache/apt/archives/screen_4.0.3-14ubuntu1.2_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Errors were encountered while processing:
 /var/cache/apt/archives/screen_4.0.3-14ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```First  there's the warning for libopenal1, which I'm not too concerned with as  the sound card doesn't work on this laptop. But this part```
dpkg:  error processing  /var/cache/apt/archives/screen_4.0.3-14ubuntu1.2_i386.deb (--unpack):
 unable to install (supposed) new info file  `/var/lib/dpkg/tmp.ci/prerm': Is a directory
``` happens with pretty  much every apt-get command. The /var/lib/dpkg/tmp.ci directory doesn't  exist first of all. Creating this directory and file doesn't do anything  and they are just removed anyways after an apt-get command.

I've  also tried manually removing the screen deb file and doing sudo apt-get  remove --purge screen. The former does nothing and the latter says  ```
dpkg: error processing screen (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
```So  then I try sudo apt-get install --reinstall screen but this just gives  me the same error as all the other apt-get commands. I've also seen  suggestions concerning sudo dpkg --configure -a, but this also turns up  errors concerning libgksu2-0 and I've been unable to find anything to  help with that also.
```
sudo dpkg --configure -a
Setting up libfreetype6 (2.3.11-1ubuntu2.6) ...

Setting up linux-image-2.6.32-40-generic (2.6.32-40.87) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-40-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-40-generic /boot/vmlinuz-2.6.32-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-40-generic /boot/vmlinuz-2.6.32-40-generic

Setting up linux-headers-2.6.32-40 (2.6.32-40.87) ...
Setting up linux-libc-dev (2.6.32-40.87) ...
Setting up linux-headers-2.6.32-40-generic (2.6.32-40.87) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-40-generic /boot/vmlinuz-2.6.32-40-generic

Setting up libgksu2-0 (2.0.13~pre1-1ubuntu4.2) ...
update-alternatives: error: /var/lib/dpkg/alternatives/libgksu-gconf-defaults corrupt: invalid status
dpkg: error processing libgksu2-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-generic (2.6.32.40.47) ...
Setting up linux-generic (2.6.32.40.47) ...
Setting up linux-headers-generic (2.6.32.40.47) ...
Setting up libpng12-0 (1.2.42-1ubuntu2.4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libopenal.so.1 is not an ELF file - it has the wrong magic bytes at the start.

Errors were encountered while processing:
 libgksu2-0

```

Any assistance in getting apt-get to work for me would be greatly appreciated!

---

### Post by plucky on 2012-03-23
Have you tried ```
sudo apt-get clean
sudo apt-get install -f
```

The first command will clear out the .deb archive(/var/cache/apt/archives),so if you want to keep all the updated .deb files do not use the command until you have saved the files elsewhere.

Apt-get will then download a new copy of the files it needs and hopefully fix the problem.

Good Luck

---

### Post by Zaszzz on 2012-03-23
I have tried both those commands. sudo apt-get clean runs and doesn't show any output so I assume it completes correctly. sudo apt-get install -f gives the same error message I pasted above.

---

### Post by Zaszzz on 2012-03-24
So does anyone here know anything about apt-get? Am I just screwed with Ubuntu here?

---

### Post by plucky on 2012-03-24
Try using **Synaptic Package Manager** to Fix Broken Packages.

If that doesn't work try using ```
sudo apt-get install --reinstall screen
``` to re-install the package and post the complete result from the output.

If that doesn't work,then try removing the package with ```
sudo apt-get remove --purge screen
``` and again post the terminal output.

As a last resort (if you are confident with editing system files),you can edit the file /var/lib/dpkg/status and remove the package in there.The package name is screen and it looks like ```
Package: screen
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 1052
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 4.0.3-14ubuntu1.2
Depends: libc6 (>= 2.4), libncursesw5 (>= 5.6+20071006-3), libpam0g (>= 0.99.7.1), dpkg (>= 1.15.4) | install-info, upstart-job
Recommends: byobu
Conffiles:
 /etc/screenrc 12c245238eb8b653625bba27dc81df6a
 /etc/init/screen-cleanup.conf 441f4a1c5b41d7f23427be5aa6ccbbcc
Description: terminal multiplexor with VT100/ANSI terminal emulation
 screen is a terminal multiplexor that runs several separate "screens" on a
 single physical character-based terminal.  Each virtual terminal emulates a
 DEC VT100 plus several ANSI X3.64 and ISO 2022 functions.  Screen sessions
 can be detached and resumed later on a different terminal.
 .
 Screen also supports a whole slew of other features.  Some of these are:
 configurable input and output translation, serial port support, configurable
 logging, multi-user support, and utf8 charset support.
Homepage: http://savannah.gnu.org/projects/screen
Original-Maintainer: Jan Christoph Nordholz <hesso@pool.math.tu-berlin.de>
```


Good Luck

---

### Post by Zaszzz on 2012-03-24
The Fix Broken Packages option didn't seem to have any effect. The output of [FONT=monospace]sudo apt-get install --reinstall screen [/FONT]and[FONT=monospace] sudo apt-get remove --purge screen [/FONT]is linked in the first post. I'll try editing the /var/lib/dpkg/status file and will post the result.[FONT=monospace]
[/FONT]

---

### Post by Zaszzz on 2012-03-24
Ok, I removed the screen package from the status and tried doing sudo apt-get install -f and it gave me another error concerning libgksu2-0. I went ahead and also removed the libgksu2-0 from the status file and tried running sudo apt-get install -f and it completed! I was also able to do apt-get autoremove and apt-get upgrade. Finally, Update Manager will actually work now.

Thanks for the help!

---

