---
title: "Cannot install any software... Help!"
date: 2010-02-04
forum: General Help
---

### Post by farrooda on 2010-02-04
Hello,

I am trying to install software via synaptic and I get this error

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I tried running the above command , and I get the error:

> dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31.6-some-string-here
Cannot find /lib/modules/2.6.31.6-some-string-here
update-initramfs: failed for /boot/initrd.img-2.6.31.6-some-string-here
dpkg: subprocess installed post-installation script returned error exit status 1


I am unable to update or install any software because of this, please help :(

---

### Post by lotharmat on 2010-02-04
Dumb question but did you prefix dpkg with sudo?

---

### Post by farrooda on 2010-02-04
> **lotharmat said:**
> Dumb question but did you prefix dpkg with sudo?

Yes I did , the above command was executed with sudo

---

### Post by howefield on 2010-02-04
Had you been using a custom kernel ?

---

### Post by farrooda on 2010-02-04
> **howefield said:**
> Had you been using a custom kernel ?

I compiled a custom kernel because I had issues with virtualbox, but I reverted to the default kernel later on. Not sure if this poses problems.

```
uname -a
Linux samer-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

```

---

### Post by howefield on 2010-02-04
> **farrooda said:**
> I compiled a custom kernel because I had issues with virtualbox, but I reverted to the default kernel later on. Not sure if this poses problems.

```
uname -a
Linux samer-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

```

I think that is the problem. (I'm no expert)

Try opening a terminal, type

```
sudo -s
```

then try,

```
update-initramfs -k 2.6.31.6-some-string-here -d
```

And then try running

```
sudo dpkg --configure -a
```

---

### Post by farrooda on 2010-02-04
```
sudo -s
[sudo] password for samer: 
root@samer-laptop:~# update-initramfs -k 2.6.31.6-some-string-here -d
The program 'update-initramfs' is currently not installed.  You can install it by typing:
apt-get install initramfs-tools
update-initramfs: command not found
```

```
root@samer-laptop:~# apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools is already the newest version.
The following extra packages will be installed:
  adduser apt apt-utils base-files base-passwd busybox-initramfs
  ca-certificates consolekit coreutils cpio dbus debconf debconf-i18n
  debianutils dpkg e2fslibs e2fsprogs findutils gawk gcc-4.4-base gnupg gpgv
  ifupdown initscripts insserv klibc-utils libacl1 libattr1 libblkid1
  libbz2-1.0 libc-bin libc6 libck-connector0 libcomerr2 libcurl3-gnutls
  libdb4.7 libdbus-1-3 libdbus-glib-1-2 libeggdbus-1-0 libexpat1 libgcc1
  libgcrypt11 libgdbm3 libglib2.0-0 libglib2.0-data libgnutls26 libgpg-error0
  libgpm2 libgssapi-krb5-2 libidn11 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 libldap-2.4-2 liblocale-gettext-perl libncurses5
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpcre3
  libpng12-0 libpolkit-gobject-1-0 libreadline6 libsasl2-2 libsasl2-modules
  libselinux1 libsepol1 libslang2 libss2 libssl0.9.8 libstdc++6 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0
  libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2
  lsb-base lzma make module-init-tools mount mountall ncurses-bin net-tools
  netbase openssl passwd perl perl-base perl-modules procps psmisc
  readline-common sed sgml-base shared-mime-info sysv-rc sysvinit-utils tzdata
  ubuntu-keyring udev upstart util-linux uuid-runtime xml-core zlib1g
Suggested packages:
  ecryptfs-utils aptitude synaptic gnome-apt wajig dpkg-dev apt-doc bzip2
  python-apt dbus-x11 debconf-doc debconf-utils whiptail dialog gnome-utils
  libterm-readline-gnu-perl libgnome2-perl libqt-perl libnet-ldap-perl gpart
  parted e2fsck-static mlocate locate slocate gnupg-doc xloadimage imagemagick
  eog libpcsclite1 iproute dhcp3-client dhcp-client ppp bootchart glibc-doc
  locales rng-tools gnutls-bin gpm krb5-doc krb5-user libpam-doc
  libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal make-doc
  nfs-common openssl-doc perl-doc sgml-base-doc sysv-rc-conf bum sash
  watershed util-linux-locales kbd console-tools dosfstools debhelper
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd busybox-initramfs
  ca-certificates consolekit coreutils cpio dbus debconf debconf-i18n
  debianutils dpkg e2fslibs e2fsprogs findutils gawk gcc-4.4-base gnupg gpgv
  ifupdown initscripts insserv klibc-utils libacl1 libattr1 libblkid1
  libbz2-1.0 libc-bin libc6 libck-connector0 libcomerr2 libcurl3-gnutls
  libdb4.7 libdbus-1-3 libdbus-glib-1-2 libeggdbus-1-0 libexpat1 libgcc1
  libgcrypt11 libgdbm3 libglib2.0-0 libglib2.0-data libgnutls26 libgpg-error0
  libgpm2 libgssapi-krb5-2 libidn11 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 libldap-2.4-2 liblocale-gettext-perl libncurses5
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpcre3
  libpng12-0 libpolkit-gobject-1-0 libreadline6 libsasl2-2 libsasl2-modules
  libselinux1 libsepol1 libslang2 libss2 libssl0.9.8 libstdc++6 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0
  libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2
  lsb-base lzma make module-init-tools mount mountall ncurses-bin net-tools
  netbase openssl passwd perl perl-base perl-modules procps psmisc
  readline-common sed sgml-base shared-mime-info sysv-rc sysvinit-utils tzdata
  ubuntu-keyring udev upstart util-linux uuid-runtime xml-core zlib1g
0 upgraded, 117 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/43.1MB of archives.
After this operation, 159MB of additional disk space will be used.
Do you want to continue [Y/n]? y
**E: Internal Error, Could not perform immediate configuration (2) on libattr1**

```

update-initramfs was not installed, I tried installing it and I got the above error. Problem persists :(

---

### Post by howefield on 2010-02-04
cd to /boot and then try.

```
sudo -s
```
```
update-initramfs -k 2.6.31.6-some-string-here -d
```
```
sudo dpkg --configure -a
```

---

### Post by farrooda on 2010-02-04
same thing :(

---

### Post by brookiemonsta on 2010-03-16
This issue was solved very helpfully in [this thread]("http://ubuntuforums.org/showthread.php?p=8975428").

---

