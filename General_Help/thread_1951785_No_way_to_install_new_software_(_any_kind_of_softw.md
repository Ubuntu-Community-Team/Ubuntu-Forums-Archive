---
title: "No way to install new software ( any kind of software )"
date: 2012-04-03
forum: General Help
---

### Post by MajinSaha on 2012-04-03
I can't install additional software in my Ubuntu (11.10). It says "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?" I click "Repair", but it fails every time.

I read in some forums that I may need to run
```
sudo apt-get install -f
```
but the output it gives is
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libkprintutils4 libavahi-qt3-1 kdelibs4c2a libipc-run-perl libhal-storage1
  libunity4 libnet-ip-perl diffstat libio-stringy-perl
  openoffice.org-officebean libnet-dns-perl gfortran-4.4 gfortran-4.5
  paraview-doc libx264-106 libecal1.2-8 patchutils libboost-python1.40.0
  libboost-signals1.40.0 openoffice.org-l10n-en-gb libgmime-2.0-2a
  libboost-python1.42.0 libboost-signals1.42.0 libpst4 libio-pty-perl
  libavfilter1 libestools2.0 liblualib50 unity-place-applications
  libavdevice52 libunity-misc0 libboost-iostreams1.42.0 gir1.2-vte-0.0
  gir1.2-appindicator-0.1 gnome-panel-bonobo libdvbpsi6 libfolks22
  unity-place-files libx264-98 libindicator3 libpanel-applet-3-0
  libpanel-applet-4-0 libgdata11 openoffice.org-java-common libhal1 hal
  libedata-cal1.2-10 libedata-book1.2-8 libgwibber1 libyaz4 libmatroska2
  libkrossui4 libmatroska3 libboost-thread1.40.0 libedataserverui1.2-11
  libdbusmenu-gtk3 libiptcdata0 kbibtex libboost-thread1.42.0 python2.6-dev
  openoffice.org-filter-mobiledev libpostproc51
  openoffice.org-filter-binfilter libwildmidi0 openoffice.org-l10n-common
  libnet-domain-tld-perl openoffice.org-base libnux-0.9-0 libcamd2.2.0
  libxdot4 libemail-valid-perl smartdimmer libsigsegv0 libcamel1.2-19
  libsoundtouch1c2 libapt-pkg-perl hal-info libqt3-mt kdelibs-data liblua50
  libfolks-telepathy22 lintian libnux-0.9-common libebml2
  gir1.2-panelapplet-4.0 libxcb-render-util0 python-wsgi-intercept
  libdigest-hmac-perl liboverlay-scrollbar-0.1-0 libkutils4 libebook1.2-10
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.0.0-17-generic
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.0.0-17-generic
0 upgraded, 1 newly installed, 0 to remove and 362 not upgraded.
2 not fully installed or removed.
Need to get 0 B/37.0 MB of archives.
After this operation, 153 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 383464 files and directories currently installed.)
Unpacking linux-image-3.0.0-17-generic (from .../linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0.0-17-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm pretty sure the error has something to do with linux-image-blah-blah stuff, but that's as far as I can go with my knowledge.
Can anyone help me with this please?

---

### Post by Dave_L on 2012-04-03
> **MajinSaha said:**
> dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0.0-17-generic': No space left on device
No apport report written because the error message indicates a disk full error

Can you post the output from this command?

```
df -hT
```

---

### Post by HiImTye on 2012-04-03
> failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0.0-17-generic': No space left on device
that's your problem

---

### Post by MajinSaha on 2012-04-03
Dave_L, I had to use sudo for this command. Nevertheless, this is the output:
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4    276G   19G  243G   8% /
udev      devtmpfs    1.9G  4.0K  1.9G   1% /dev
tmpfs        tmpfs    778M  908K  777M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.9G  1.2M  1.9G   1% /run/shm
/dev/sda1     ext4    110M  107M     0 100% /boot
/dev/sda6     ext4    180G  188M  171G   1% /utmp

```
HiImTye, I thought something like that before, but I think I have plenty of space in total. It may be that some partition is full though (boot ?). Any guess how to fix that? It seems to me moving files freely is not safe since they are no ordinary files.

---

### Post by HiImTye on 2012-04-03
```
Filesystem    Type    Size  Used **Avail Use%** Mounted on
/dev/sda1     ext4    110M  107M     **0 100%** /boot
```thats the only device that matters as it's the one being written to
> **MajinSaha said:**
> failed in write on buffer copy for backend dpkg-deb during `.**/boot/**vmlinuz-3.0.0-17-generic': No space left on device

---

### Post by Dave_L on 2012-04-03
Please post the output from this:

```
ls -lh /boot
```

---

### Post by MajinSaha on 2012-04-03
Dave_L:
```
total 97M
-rw-r--r-- 1 root root 714K 2011-12-18 16:57 abi-2.6.38-11-generic
-rw-r--r-- 1 root root 714K 2011-10-07 22:02 abi-3.0.0-12-generic
-rw-r--r-- 1 root root 714K 2011-11-02 19:33 abi-3.0.0-13-generic
-rw-r--r-- 1 root root 714K 2011-11-21 22:29 abi-3.0.0-14-generic
-rw-r--r-- 1 root root 128K 2011-12-18 16:57 config-2.6.38-11-generic
-rw-r--r-- 1 root root 132K 2011-10-07 22:02 config-3.0.0-12-generic
-rw-r--r-- 1 root root 132K 2011-11-02 19:33 config-3.0.0-13-generic
-rw-r--r-- 1 root root 132K 2011-11-21 22:29 config-3.0.0-14-generic
drwxr-xr-x 3 root root 7.0K 2011-12-18 16:50 grub
-rw-r--r-- 1 root root  16M 2011-12-18 16:57 initrd.img-2.6.38-11-generic
-rw-r--r-- 1 root root  19M 2011-10-14 17:29 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root  19M 2011-12-17 14:12 initrd.img-3.0.0-13-generic
-rw-r--r-- 1 root root  19M 2011-12-17 14:13 initrd.img-3.0.0-14-generic
drwx------ 2 root root  12K 2011-02-19 07:15 lost+found
-rw-r--r-- 1 root root 173K 2011-05-03 01:07 memtest86+.bin
-rw-r--r-- 1 root root 175K 2011-05-03 01:07 memtest86+_multiboot.bin
-rw------- 1 root root    0 2011-12-18 16:57 System.map-2.6.38-11-generic
-rw------- 1 root root 2.6M 2011-10-07 22:02 System.map-3.0.0-12-generic
-rw------- 1 root root 2.6M 2011-11-02 19:33 System.map-3.0.0-13-generic
-rw------- 1 root root 2.6M 2011-11-21 22:29 System.map-3.0.0-14-generic
-rw------- 1 root root    0 2011-12-18 16:57 vmcoreinfo-2.6.38-11-generic
-rw------- 1 root root 1.4K 2011-10-07 22:08 vmcoreinfo-3.0.0-12-generic
-rw------- 1 root root 1.4K 2011-11-02 19:39 vmcoreinfo-3.0.0-13-generic
-rw------- 1 root root 1.4K 2011-11-21 22:30 vmcoreinfo-3.0.0-14-generic
-rw------- 1 root root    0 2011-12-18 16:57 vmlinuz-2.6.38-11-generic
-rw------- 1 root root 4.5M 2011-10-07 22:02 vmlinuz-3.0.0-12-generic
-rw------- 1 root root 4.5M 2011-11-02 19:33 vmlinuz-3.0.0-13-generic
-rw------- 1 root root 4.5M 2011-11-21 22:29 vmlinuz-3.0.0-14-generic

```
HiImTye, in my previous post, I said I didn't know what to do even though I could guess that boot folder was full. What should I do in your opinion?

---

### Post by zombifier25 on 2012-04-03
You should remove older kernel entries. [Ubuntu Tweak]("http://ubuntu-tweak.com/")'s Janitor tool should be able to do it without diving through kernel packages yourself.

---

### Post by MajinSaha on 2012-04-03
> **zombifier25 said:**
> You should remove older kernel entries. [Ubuntu Tweak]("http://ubuntu-tweak.com/")'s Janitor tool should be able to do it without diving through kernel packages yourself.

Thanks, but as you know I can't install new software, that's the entity of my problem. I tried and result was the same as with any other software.

---

### Post by Dave_L on 2012-04-03
You could free up a lot of space in /boot by removing some of the older kernels.

This shows you the kernel you're currently using:

```
uname -a
```

Assuming that your current kernel is 3.0.0-14, and it's working ok, you could remove kernels 2.6.38-11, 3.0.0-12 and 3.0.0-13.

Personally I don't like using UbuntuTweak for this.

But it's easy to do with synaptic. For example, to remove kernel 2.6.38-11 using synaptic:

Select Status "Installed" in the left pane.
Search for "2.6.38-11".
Select the packages found; there are typically three or four of them.
Remove them completely (Package >> Mark for Complete Removal).
Click the "Apply" button.

If you're not sure that synaptic is showing you the right packages, post their names here before clicking "Apply".

---

### Post by MajinSaha on 2012-04-03
Thanks. The thread may be closed, I resorted to help of my colleague who knows a lot about Ubuntu. But basically we were doing the same stuff as you described here.
Now my boot folder is 40% free and I've already installed the software I needed.
For the future, I will keep in mind the following. Each time I update my system, I need to check boot folder for new linux-image-version files. If there is newer version, I need to remove previous one from the queue by executing

```
sudo apt-get remove linux-image-version-generic
```

It wasn't easy this time since apt-get did not work by default, but in normal circumstances that must be the right solution. At least that's what my colleague told me.
Thanks to all who replied.

---

