---
title: "Errors were encountered while processing:  ipheth-dkms  ipheth-utils"
date: 2010-11-28
forum: General Help
---

### Post by fox-mulder on 2010-11-28
hi i did sudo apt-get update and followed with upgrade command and this happen, tell me why

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ipheth-dkms is already the newest version.
ipheth-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of ipheth-utils:
 ipheth-utils depends on ipheth-dkms; however:
  Package ipheth-dkms is not configured yet.
dpkg: error processing ipheth-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ipheth-dkms
 ipheth-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


```
 
DKMS make.log for ipheth-1.0+git20100207 for kernel 2.6.35-23-generic (i686)
Sun Nov 28 20:37:29 CET 2010
make -C /lib/modules/2.6.35-22-generic/build M=/var/lib/dkms/ipheth/1.0+git20100207/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.o
/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.c: In function &#8216;ipheth_alloc_urbs&#8217;:
/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.c:125: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.c:128: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.c:135: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.c:147: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[2]: *** [/var/lib/dkms/ipheth/1.0+git20100207/build/ipheth.o] Error 1
make[1]: *** [_module_/var/lib/dkms/ipheth/1.0+git20100207/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

```

---

### Post by fox-mulder on 2010-11-28
for bump sake

---

### Post by fox-mulder on 2010-11-29
> **fox-mulder said:**
> **for bump sake**

 
   ..

---

### Post by lilmissdids on 2010-11-29
I have the same problem. Just updated to 10.10 and encountered that... can anyone help?

---

### Post by fox-mulder on 2010-11-29
> **lilmissdids said:**
> I have the same problem. Just updated to 10.10 and encountered that... can anyone help?

finally some one has the same error, and this error stops the things i need update,

!$!$@% error3..

---

### Post by fox-mulder on 2010-12-07
:sad:
i got more problems now, -> 

```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```then i tried with rm /var/lib/dpkg/lock ..
then sudo dpkg --configure -a 

```
root@username-HP-Mini-210-1000:/home/username# rm /var/lib/dpkg/lock
root@username-HP-Mini-210-1000:/home/username# sudo dpkg --configure -a
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libibus2 (1.3.7-1ubuntu4) ...
Setting up ibus-gtk (1.3.7-1ubuntu4) ...
Setting up python-ibus (1.3.7-1ubuntu4) ...
Processing triggers for hicolor-icon-theme ...
Setting up libwbclient0 (2:3.5.4~dfsg-1ubuntu8.1) ...
Setting up libisc60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up libisccc60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Processing triggers for libgtk2.0-0 ...
Setting up linux-libc-dev (2.6.35-1023.41) ...
Setting up python-dockmanager (0.1.0~bzr76-0ubuntu1~10.10~dockers1) ...
Setting up libqtcore4 (4:4.7.0-0ubuntu4.2) ...
Setting up libdns66 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Processing triggers for python-support ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       ipheth (1.0+git20100207)...                                        [ fail ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up telepathy-haze (0.4.0-1ubuntu0.1) ...
Setting up liblwres60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up samba-common (2:3.5.4~dfsg-1ubuntu8.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ibus (1.3.7-1ubuntu4) ...
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/ja_JP (xinput-ja_JP) in auto mode.
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/ko_KR (xinput-ko_KR) in auto mode.
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_CN (xinput-zh_CN) in auto mode.
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_TW (xinput-zh_TW) in auto mode.
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_HK (xinput-zh_HK) in auto mode.
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_SG (xinput-zh_SG) in auto mode.
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.5.4~dfsg-1ubuntu8.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up dockmanager (0.1.0~bzr76-0ubuntu1~10.10~dockers1) ...
Setting up tomboy (1.4.2-0ubuntu1) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up appmenu-gtk (0.1.9-0ubuntu4.1) ...
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for gconf2 ...
Setting up libldap-2.4-2 (2.4.23-0ubuntu3.4) ...
Setting up libqt4-xml (4:4.7.0-0ubuntu4.2) ...
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-23-generic
Building initial module for 2.6.35-23-generic

Error! Bad return status for module build on kernel: 2.6.35-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up gwibber-service (2.32.2-0ubuntu2) ...
Setting up linux-headers-2.6.35-23 (2.6.35-23.41) ...
Setting up libisccfg60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up libbind9-60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up linux-headers-2.6.35-23-generic (2.6.35-23.41) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       ipheth (1.0+git20100207)...                                     [fail] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-sql (4:4.7.0-0ubuntu4.2) ...
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.5.4~dfsg-1ubuntu8.1); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ipheth-utils:
 ipheth-utils depends on ipheth-dkms; however:
  Package ipheth-dkms is not configured yet.
dpkg: error processing ipheth-utils (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-sql-mysql (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-dbus (4:4.7.0-0ubuntu4.2) ...
Setting up bind9-host (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up dnsutils (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up libqtgui4 (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-svg (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-network (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-script (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-opengl (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-designer (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-qt3support (4:4.7.0-0ubuntu4.2) ...
Processing triggers for python-central ...
Setting up gwibber (2.32.2-0ubuntu2) ...
Processing triggers for python-central ...
Setting up openjdk-6-jre-headless (6b20-1.9.2-0ubuntu1) ...
Setting up openjdk-6-jre (6b20-1.9.2-0ubuntu1) ...
Setting up openjdk-6-jre-lib (6b20-1.9.2-0ubuntu1) ...
Setting up icedtea-6-jre-cacao (6b20-1.9.2-0ubuntu1) ...
Setting up icedtea6-plugin (6b20-1.9.2-0ubuntu1) ...
Setting up docky (2.1.0~bzr1710-0ubuntu1~10.10~dockycore1) ...
Setting up docky-dbg (2.1.0~bzr1710-0ubuntu1~10.10~dockycore1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for menu ...
Errors were encountered while processing:
 man-db
 linux-image-2.6.35-23-generic
 samba-common
 smbclient
 samba-common-bin
 ipheth-dkms
 linux-headers-2.6.35-23-generic
 winbind
 ipheth-utils
root@username-HP-Mini-210-1000:/home/username# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libgexiv2-0 libsmbclient ttf-mscorefonts-installer update-inetd xdg-utils
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
root@username-HP-Mini-210-1000:/home/username#
```BUMP!

---

### Post by fox-mulder on 2010-12-08
Update

```
root@username-HP-Mini-210-1000:/home/username# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-23-generic
Building initial module for 2.6.35-23-generic

Error! Bad return status for module build on kernel: 2.6.35-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of ipheth-utils:
 ipheth-utils depends on ipheth-dkms; however:
  Package ipheth-dkms is not configured yet.
dpkg: error processing ipheth-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ipheth-dkms
 ipheth-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by fox-mulder on 2010-12-13
i solved this by entering the command

```
sudo apt-get remove ipheth-dkms
```

happy holidays foulks

---

