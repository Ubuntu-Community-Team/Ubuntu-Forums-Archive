---
title: "Update manager error: Package Operation Failed"
date: 2011-01-07
forum: General Help
---

### Post by HaveLotsToLearn on 2011-01-07
Have received errors the last two times I've run Update Manager.
This one says:
Package Operation Failed
The installation or removal of a software package failed.
Details:
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170993 files and directories currently installed.) 
Preparing to replace dpkg 1.15.8.4ubuntu3 (using .../dpkg_1.15.8.4ubuntu3.1_i386.deb) ... 
Unpacking replacement dpkg ... 
Processing triggers for man-db ... 
Setting up dpkg (1.15.8.4ubuntu3.1) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170993 files and directories currently installed.) 
Preparing to replace ifupdown 0.6.10ubuntu3 (using .../ifupdown_0.6.10ubuntu3.1_i386.deb) ... 
Unpacking replacement ifupdown ... 
Preparing to replace libcups2 1.4.4-6ubuntu2.2 (using .../libcups2_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcups2 ... 
Preparing to replace libcupscgi1 1.4.4-6ubuntu2.2 (using .../libcupscgi1_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcupscgi1 ... 
Preparing to replace libcupsdriver1 1.4.4-6ubuntu2.2 (using .../libcupsdriver1_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcupsdriver1 ... 
Preparing to replace libcupsimage2 1.4.4-6ubuntu2.2 (using .../libcupsimage2_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcupsimage2 ... 
Preparing to replace libcupsmime1 1.4.4-6ubuntu2.2 (using .../libcupsmime1_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcupsmime1 ... 
Preparing to replace libcupsppdc1 1.4.4-6ubuntu2.2 (using .../libcupsppdc1_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement libcupsppdc1 ... 
Preparing to replace cups-common 1.4.4-6ubuntu2.2 (using .../cups-common_1.4.4-6ubuntu2.3_all.deb) ... 
Unpacking replacement cups-common ... 
Preparing to replace cups-bsd 1.4.4-6ubuntu2.2 (using .../cups-bsd_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement cups-bsd ... 
Preparing to replace cups-client 1.4.4-6ubuntu2.2 (using .../cups-client_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement cups-client ... 
Preparing to replace cups-ppdc 1.4.4-6ubuntu2.2 (using .../cups-ppdc_1.4.4-6ubuntu2.3_i386.deb) ... 
Unpacking replacement cups-ppdc ... 
Preparing to replace cups 1.4.4-6ubuntu2.2 (using .../cups_1.4.4-6ubuntu2.3_i386.deb) ... 
cups stop/waiting 
Unpacking replacement cups ... 
Preparing to replace apparmor 2.5.1-0ubuntu0.10.10.2 (using .../apparmor_2.5.1-0ubuntu0.10.10.3_i386.deb) ... 
Unpacking replacement apparmor ... 
Preparing to replace libapparmor1 2.5.1-0ubuntu0.10.10.2 (using .../libapparmor1_2.5.1-0ubuntu0.10.10.3_i386.deb) ... 
Unpacking replacement libapparmor1 ... 
Preparing to replace libapparmor-perl 2.5.1-0ubuntu0.10.10.2 (using .../libapparmor-perl_2.5.1-0ubuntu0.10.10.3_i386.deb) ... 
Unpacking replacement libapparmor-perl ... 
Preparing to replace apparmor-utils 2.5.1-0ubuntu0.10.10.2 (using .../apparmor-utils_2.5.1-0ubuntu0.10.10.3_i386.deb) ... 
Unpacking replacement apparmor-utils ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for ufw ... 
Processing triggers for doc-base ... 
Processing 1 changed doc-base file(s)... 
Registering documents with scrollkeeper... 
Setting up initramfs-tools (0.98.1ubuntu6) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
E: mkinitramfs failure cpio 141 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-24-generic; however: 
  Package linux-image-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up ifupdown (0.6.10ubuntu3.1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Installing new version of config file /etc/init/network-interface-security.conf ... 
Installing new version of config file /etc/init/network-interface.conf ... 
start: Job is already running: network-interface-security 
Setting up libcups2 (1.4.4-6ubuntu2.3) ... 
Setting up libcupscgi1 (1.4.4-6ubuntu2.3) ... 
Setting up libcupsdriver1 (1.4.4-6ubuntu2.3) ... 
Setting up libcupsimage2 (1.4.4-6ubuntu2.3) ... 
Setting up libcupsmime1 (1.4.4-6ubuntu2.3) ... 
Setting up libcupsppdc1 (1.4.4-6ubuntu2.3) ... 
Setting up cups-common (1.4.4-6ubuntu2.3) ... 
Setting up cups-client (1.4.4-6ubuntu2.3) ... 
Setting up cups-bsd (1.4.4-6ubuntu2.3) ... 
Setting up cups-ppdc (1.4.4-6ubuntu2.3) ... 
Setting up cups (1.4.4-6ubuntu2.3) ... 
Installing new version of config file /etc/init/cups.conf ... 
cups start/running, process 8630 
Setting up apparmor (2.5.1-0ubuntu0.10.10.3) ... 
 * Starting AppArmor profiles        Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [ OK ] 
 * Reloading AppArmor profiles        Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [ OK ] 
Setting up libapparmor1 (2.5.1-0ubuntu0.10.10.3) ... 
Setting up libapparmor-perl (2.5.1-0ubuntu0.10.10.3) ... 
Setting up apparmor-utils (2.5.1-0ubuntu0.10.10.3) ... 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
E: mkinitramfs failure find 141 cpio 141 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-2.6.35-24-generic 
 linux-image-generic 
 linux-generic 
 initramfs-tools 
Setting up initramfs-tools (0.98.1ubuntu6) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
cpio: write error: Broken pipe 
find: `standard output': Broken pipe 
find: write error 
E: mkinitramfs failure find 1 cpio 1 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-24-generic; however: 
  Package linux-image-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
cpio: write error: Broken pipe 
find: `standard output': Broken pipe 
find: write error 
E: mkinitramfs failure find 1 cpio 1 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 

The last error said something about "Max Reports".

What I can't tell is whether the updates actually installed.  And can any of you tell what I need to fix/replace?

Thanks for the help!

---

### Post by HectorG on 2011-01-07
Having similar issue update manager just hangs at 

"preparing to replace cups 1.4.4-6ubuntu2.2"

---

### Post by HectorG on 2011-01-08
My issue was resolved by doing the following...


sudo dpkg --configure -a
sudo apt-get install -f

uninstall akirad repository from synaptic (not sure why this fixed it yet)

Try your update now

---

### Post by skela on 2011-01-09
I'm having the same problems HectorG, but cant fix it, because it hangs at 
"preparing to replace cups 1.4.4-6ubuntu2.2"

when i do:
sudo dpkg --configure -a

whats the solution?

---

### Post by HectorG on 2011-01-09
I think what really fixed mine was the Akirad was corrupt. Go in to synaptic and seee if it is installed, if it is try removing it. Don't let the update manager try to update because it will continue to hang. Try canceling it when it prompts you.   

Check your sources. Do you have anything in there that is not normally from ubuntu? It might be some bad sources installing something that is breaking your system. For instance I have some for Digikam that I use to get the latest stable version available. I removed those although that wasn't the problem.  

Then  as far as I can recall I tried this...
 
sudo apt-get autoremove

sudo dpkg --configure -a

sudo apt-get install -f


Have you tried forcing the uninstall of cups although mine warned against that I think I did it anyways but that should probably be the last result.

---

### Post by babil on 2011-01-09
Kill the 'dpkg' process first:
```

ps aux | grep dpkg | awk '{print $2}' | sudo xargs echo

```

The follow with:
```

sudo apt-get autoremove
sudo dpkg --configure -a
sudo apt-get install -f

```

---

### Post by HaveLotsToLearn on 2011-01-12
I'm still having problems.  Today's error might be a clue for the experts out there on what I'm missing:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170993 files and directories currently installed.) 
Preparing to replace libc6-dev 2.12.1-0ubuntu10 (using .../libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ... 
Unpacking replacement libc6-dev ... 
Preparing to replace libc-dev-bin 2.12.1-0ubuntu10 (using .../libc-dev-bin_2.12.1-0ubuntu10.1_i386.deb) ... 
Unpacking replacement libc-dev-bin ... 
Preparing to replace libc-bin 2.12.1-0ubuntu10 (using .../libc-bin_2.12.1-0ubuntu10.1_i386.deb) ... 
Unpacking replacement libc-bin ... 
Processing triggers for man-db ... 
Setting up libc-bin (2.12.1-0ubuntu10.1) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170993 files and directories currently installed.) 
Preparing to replace libc6 2.12.1-0ubuntu10 (using .../libc6_2.12.1-0ubuntu10.1_i386.deb) ... 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
/var/lib/dpkg/tmp.ci/preinst: 399: readlink: not found 
Unpacking replacement libc6 ... 
Setting up libc6 (2.12.1-0ubuntu10.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170993 files and directories currently installed.) 
Preparing to replace liblcms1 1.18.dfsg-1ubuntu2 (using .../liblcms1_1.18.dfsg-1ubuntu2.10.10.1_i386.deb) ... 
Unpacking replacement liblcms1 ... 
Preparing to replace xserver-common 2:1.9.0-0ubuntu7 (using .../xserver-common_2%3a1.9.0-0ubuntu7.1_all.deb) ... 
Unpacking replacement xserver-common ... 
Preparing to replace xserver-xorg-core 2:1.9.0-0ubuntu7 (using .../xserver-xorg-core_2%3a1.9.0-0ubuntu7.1_i386.deb) ... 
Unpacking replacement xserver-xorg-core ... 
Processing triggers for man-db ... 
Setting up initramfs-tools (0.98.1ubuntu6) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
E: mkinitramfs failure cpio 141 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-24-generic; however: 
  Package linux-image-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up libc-dev-bin (2.12.1-0ubuntu10.1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up libc6-dev (2.12.1-0ubuntu10.1) ... 
Setting up liblcms1 (1.18.dfsg-1ubuntu2.10.10.1) ... 
Setting up xserver-common (2:1.9.0-0ubuntu7.1) ... 
Setting up xserver-xorg-core (2:1.9.0-0ubuntu7.1) ... 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
E: mkinitramfs failure find 141 cpio 141 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-2.6.35-24-generic 
 linux-image-generic 
 linux-generic 
 initramfs-tools 
Setting up initramfs-tools (0.98.1ubuntu6) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
cpio: write error: Broken pipe 
find: `standard output': Broken pipe 
find: write error 
E: mkinitramfs failure find 1 cpio 1 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-24-generic; however: 
  Package linux-image-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic 
/usr/sbin/mkinitramfs: 98: readlink: not found 
/usr/sbin/mkinitramfs: 351: cannot create : Directory nonexistent 
cpio: write error: Broken pipe 
find: `standard output': Broken pipe 
find: write error 
E: mkinitramfs failure find 1 cpio 1 gzip 2 
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

