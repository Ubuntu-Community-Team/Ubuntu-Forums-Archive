---
title: "Crash During An Update"
date: 2010-11-28
forum: General Help
---

### Post by ubupatzer on 2010-11-28
The computer crashed during an update and

"An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So,

"michael@freegeek:~$ sudo dpkg --configure -a
[sudo] password for michael: 
dpkg: parse error, in file '/var/lib/dpkg/updates/0117' near line 0:
 field name `
michael@freegeek:~$"

What should be done next?

---

### Post by sikander3786 on 2010-11-28
Rename that file and try update again.

```
sudo mv /var/lib/dpkg/updates/0117 /var/lib/dpkg/updates/0117.bad
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ubupatzer on 2010-11-28
After step 2:

michael@freegeek:~$ sudo dpkg --configure -a
[sudo] password for michael: 
Processing triggers for packagekit ...
michael@freegeek:~$ 

And,

" You have 1 broken package on your system.
Use the "Broken" filter to locate it."

How to proceed?

---

### Post by sikander3786 on 2010-11-28
> **ubupatzer said:**
> After step 2:

michael@freegeek:~$ sudo dpkg --configure -a
[sudo] password for michael: 
Processing triggers for packagekit ...
michael@freegeek:~$ 

And,

" You have 1 broken package on your system.
Use the "Broken" filter to locate it."

How to proceed?

Try this,

```
sudo apt-get install -f
```

---

### Post by ubupatzer on 2010-11-28
This is the result:



d-apt': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/share/doc/packagekit-backend-apt/README.apt': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/share/doc/packagekit-backend-apt/TODO.apt': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/share/doc/packagekit-backend-apt/copyright': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/share/PackageKit/helpers/apt/aptBackend.py': Read-only file system
dpkg: error while cleaning up:
 unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
dpkg: error while cleaning up:
 unable to securely remove '/var/lib/dpkg/reassemble.deb': Read-only file system
dpkg: error processing /var/cache/apt/archives/python-packagekit_0.5.7-0ubuntu2.2_all.deb (--unpack):
 error ensuring `/var/lib/dpkg/reassemble.deb' doesn't exist: Read-only file system
Processing triggers for packagekit ...
dpkg: unrecoverable fatal error, aborting:
 unable to flush updated status of `packagekit': Read-only file system
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
sh: cannot create /var/lib/update-notifier/updates-available: Read-only file system
Segmentation fault
michael@freegeek:~$

---

### Post by sikander3786 on 2010-11-28
Try backing up your current /dpkg/status and using an older one by,

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
```

```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
```

---

### Post by ubupatzer on 2010-11-28
After:


michael@freegeek:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad

michael@freegeek:~$ sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

michael@freegeek:~$ sudo apt-get update

  "...W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FBB49579B75FECB0
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." 

michael@freegeek:~$ sudo apt-get install -f

"...The following extra packages will be installed:
  packagekit-backend-apt python-packagekit
The following packages will be upgraded:
  packagekit-backend-apt python-packagekit
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/122kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? "


Continuing then results in the same error output.

---

### Post by sikander3786 on 2010-11-28
That output seems ok...

Please post the complete output for the commands and wrap them with code tags # from post menu. [/code] at the end and ```
 at the beginning.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable the Launchpad PPA Repository. Again try apt-get update and post the complete output this time.

[code]sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ubupatzer on 2010-11-28
Is this the format you suggested?


michael@freegeek:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for michael: 


```
<Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_CA       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,094B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                          
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_CA    
Hit [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 2,638B in 1s (1,688B/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. >
```


michael@freegeek:~$ sudo dpkg --configure -a
Processing triggers for packagekit ...
michael@freegeek:~$

---

### Post by sikander3786 on 2010-11-28
That should be [/code] and ```
 instead of /code#9 :-)

Anyways, now try this one again as being suggested by apt-get,

[code]sudo dpkg --configure -a
```

If errors, again try

```
sudo apt-get install -f
```

If still that returns errors, you'll need to edit /dpkg/status manually and do some house-cleaning. Please post the complete ouptuts.

---

### Post by ubupatzer on 2010-11-28
```
<michael@freegeek:~$ sudo apt-get install -f
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-9 libfreebob0 libsm-dev libtalloc1 libgtk2.0-0-dbg
  evolution-data-server-dbg libgsf-gnome-1-114 libprocessui4 libtaskmanager4
  linux-headers-2.6.31-21 libqimageblitz4 rhythmbox-dbg libice-dev
  gstreamer0.10-plugins-base-dbg x11proto-xext-dev libatk1.0-dbg
  libdmraid1.0.0.rc15 xulrunner-1.9.1 libkscreensaver5 libsolidcontrolifaces4
  ttf-wqy-zenhei libgda-4.0-common linux-headers-2.6.32-22 libgsf-1-114-dbg
  libdevhelp-1-1 libgoffice-0.8-8-common libicu40
  xulrunner-1.9.1-gnome-support libgda3-common evince-dbg libpango1.0-0-dbg
  libgnomedb3-common libgnomedb3-4 libgnomevfs2-0-dbg libopts25
  x11proto-render-dev libopts25-dev libevview1 evolution-dbg libindicate-gtk1
  latex-xft-fonts autogen libdns53 m4 eog-dbg libatspi-dbg libapr1
  libxrender-dev libknotificationitem1 openoffice.org-hyphenation-en-us
  autoconf python-dbg libcompress-bzip2-perl anjuta-common libcairo2-dev
  libtotem-plparser12 libass3 libservlet2.4-java
  libplasma-geolocation-interface4 kde-icons-oxygen libgdl-1-dbg libexiv2-5
  libsysfs-dev libdirectfb-extra librasqal1 python-gtksourceview libkadm5clnt6
  libxft2-dbg libisccc50 exuberant-ctags gobject-introspection
  python-cairo-dbg libfontconfig1-dbg liblzma0 libfontconfig1-dev
  libgoffice-0.8-8 libdirectfb-dev libsvn1 intltool sdparm libx264-67
  libgoffice-dbg libopal3.6.4 redland-utils libgssdp-1.0-1 anjuta
  libgsf-gnome-1-114-dbg libparted1.8-12 libksgrd4 devhelp-common liblwres50
  libgda3-sqlite anjuta-dbg libkworkspace4 libcelt0
  gstreamer0.10-plugins-ugly-dbg libgda-4.0-4 libprotobuf3
  gstreamer0.10-plugins-good-dbg python-sip4 libplasmagenericshell4 dkms
  libxcb-render-util0-dev libkfontinst4 libgnomedb3-bin libxext-dev
  libloudmouth1-0-dbg libjline-java libbind9-50 openoffice.org-thesaurus-en-au
  openoffice.org-hyphenation linux-headers-2.6.31-21-generic gnome-panel-dbg
  libevdocument1 python2.6-dbg libffado1 libgnomecanvas2-dbg
  x11proto-fixes-dev libgnomedb3-4-dbg libpt2.6.4-plugins libiso9660-5









  libxcb-render0-dev libgnome2-dbg libgmime2.2a-cil libxfixes-dev
  python-nautilusburn libisc50 watershed libplasma-applet-system-monitor4
  libvala0 libprocesscore4 gnome-blackjack raptor-utils libaprutil1
  libgail-gnome-dbg libsensors-dev libgdl-1-3 gimp-dbg python-gobject-dbg
  libgstreamer0.10-0-dbg python-gtk2-dbg libgdl-1-common libgoffice-0-8-common
  libntfs-3g54 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  packagekit-backend-apt python-packagekit
The following packages will be upgraded:
  packagekit-backend-apt python-packagekit
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/122kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 311140 files and directories currently installed.)
Preparing to replace packagekit-backend-apt 0.5.7-0ubuntu2.1 (using .../packagekit-backend-apt_0.5.7-0ubuntu2.2_i386.deb) ...
Unpacking replacement packagekit-backend-apt ...
dpkg: error processing /var/cache/apt/archives/packagekit-backend-apt_0.5.7-0ubuntu2.2_i386.deb (--unpack):
 unable to securely remove '/usr/lib/packagekit-backend/libpk_backend_apt.so.dpkg-new': Input/output error
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
sh: cannot create /var/lib/update-notifier/updates-available: Read-only file system
Segmentation fault
michael@freegeek:~$ >
```

```
<michael@freegeek:~$ edit /dpkg/status manually
Warning: unknown mime-type for "/dpkg/status" -- using "application/octet-stream"
Warning: unknown mime-type for "manually" -- using "application/octet-stream"
Error: no write permission for file "/dpkg/status"
Error: no write permission for file "manually"
michael@freegeek:~$>
```

---

### Post by sikander3786 on 2010-11-28
Move back your original /dpkg/status

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-old
```

```
sudo mv /var/lib/dpkg/status-bad /var/lib/dpkg/status
```

Edit /dpkg/status by,

```
gksudo gedit /var/lib/dpkg/status
```

Find packagekit-backend and delete the entire section for that. Save and close and try update again.

```
sudo apt-get update && sudo apt-get upgrade
```

Good Luck!

---

### Post by ubupatzer on 2010-11-28
```
<michael@freegeek:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Get:2 http://dl.google.com stable Release [1,347B]                             
Get:3 http://dl.google.com stable/main Packages [1,094B]                       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Hit http://deb.opera.com stable Release.gpg                          
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_CA    
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Hit http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA
Hit http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com lucid-security Release                
Hit http://deb.opera.com stable Release                              
Hit http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Ign http://deb.opera.com stable/non-free Packages                    
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://deb.opera.com stable/non-free Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 2,638B in 1s (1,692B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  packagekit: Depends: libapt-pkg-libc6.10-6-4.8
              Depends: libc6 (>= 2.7) but it is not installed
              Depends: libdbus-1-3 (>= 1.0.2) but it is not installed
              Depends: libdbus-glib-1-2 (>= 0.78) but it is not installed
              Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
              Depends: libnm-glib2 (>= 0.8~a~git.20090826t185111.79489be) but it is not installed
              Depends: libpackagekit-glib2-12 (= 0.5.7-0ubuntu2.1) but it is not installed
              Depends: libpolkit-backend-1-0 (>= 0.94) but it is not installed
              Depends: libpolkit-gobject-1-0 (>= 0.94) but it is not installed
              Depends: libsqlite3-0 (>= 3.6.22) but it is not installed
              Depends: dbus but it is not installed
  packagekit-backend-apt: Depends: libapt-pkg-libc6.10-6-4.8
                          Depends: libc6 (>= 2.3.6-6~) but it is not installed
                          Depends: libdbus-1-3 (>= 1.0.2) but it is not installed
                          Depends: libdbus-glib-1-2 (>= 0.78) but it is not installed
                          Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                          Depends: python but it is not installed
                          Depends: python-central (>= 0.6.11) but it is not installed
                          Depends: python-packagekit (= 0.5.7-0ubuntu2.1) but it is not installed
                          Depends: app-install-data but it is not installed
                          Depends: python-apt (>= 0.7.13.2) but it is not installed
                          Depends: python-gdbm but it is not installed
                          Depends: update-manager-core but it is not installed
                          Depends: python-software-properties but it is not installed
                          Recommends: apt-xapian-index but it is not installed
E: Unmet dependencies. Try using -f.
michael@freegeek:~$>
``````
<michael@freegeek:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@freegeek:~$ sudo apt-get -f install
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  adduser app-install-data apt apt-utils base-files base-passwd
  busybox-initramfs ca-certificates consolekit coreutils cpio dbus debconf
  debconf-i18n debianutils dpkg e2fslibs e2fsprogs file findutils gawk
  gcc-4.4-base gnupg gnupg-curl gpgv ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv iso-codes klibc-utils libacl1
  libattr1 libblkid1 libbz2-1.0 libc-bin libc6 libc6-i686 libck-connector0
  libcomerr2 libcurl3-gnutls libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libeggdbus-1-0
  libexpat1 libffi5 libgcc1 libgcrypt11 libgdbm3 libglib2.0-0 libglib2.0-data
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgudev-1.0-0 libidn11
  libk5crypto3 libkeyutils1 libklibc libkrb5-3 libkrb5support0 libldap-2.4-2
  liblocale-gettext-perl libmagic1 libncurses5 libncursesw5 libnih-dbus1
  libnih1 libnm-glib2 libnm-util1 libnspr4-0d libnss3-1d
  libpackagekit-glib2-12 libpam-ck-connector libpam-modules libpam-runtime
  libpam0g libpcre3 libplymouth2 libpng12-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libreadline6 libsasl2-2 libsasl2-modules libselinux1
  libsepol1 libslang2 libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0
  libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2
  lsb-base lsb-release lzma make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase openssl packagekit
  packagekit-backend-apt passwd perl perl-base perl-modules plymouth
  plymouth-theme-ubuntu-text procps psmisc python python-apt python-central
  python-dbus python-gdbm python-gnupginterface python-gobject python-minimal
  python-packagekit python-software-properties python-support python2.6
  python2.6-minimal readline-common sed sensible-utils sgml-base
  shared-mime-info sysv-rc sysvinit-utils tzdata ubuntu-keyring ucf udev
  unattended-upgrades update-manager-core upstart util-linux uuid-runtime
  xml-core zlib1g
Suggested packages:
  ecryptfs-utils aptitude synaptic wajig dpkg-dev apt-doc bzip2 dbus-x11
  debconf-doc debconf-utils whiptail dialog gnome-utils
  libterm-readline-gnu-perl libgnome2-perl libnet-ldap-perl gpart parted
  e2fsck-static mlocate locate slocate gnupg-doc xloadimage imagemagick eog
  libpcsclite1 iproute dhcp3-client dhcp-client ppp bootchart isoquery
  glibc-doc locales rng-tools gnutls-bin gpm krb5-doc krb5-user libpam-doc
  libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal lsb make-doc
  nfs-common openssl-doc perl-doc python-doc python-tk python-profiler
  python-apt-dbg python-gtk2 python-vte python-apt-doc python-dbus-doc
  python-dbus-dbg python-gdbm-dbg python-gobject-dbg python2.6-doc
  python2.6-profiler binutils binfmt-support sgml-base-doc sysv-rc-conf bum
  sash watershed bsd-mailx util-linux-locales kbd console-tools dosfstools
  debhelper
Recommended packages:
  apt-xapian-index
The following NEW packages will be installed:
  adduser app-install-data apt apt-utils base-files base-passwd
  busybox-initramfs ca-certificates consolekit coreutils cpio dbus debconf
  debconf-i18n debianutils dpkg e2fslibs e2fsprogs file findutils gawk
  gcc-4.4-base gnupg gnupg-curl gpgv ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv iso-codes klibc-utils libacl1
  libattr1 libblkid1 libbz2-1.0 libc-bin libc6 libc6-i686 libck-connector0
  libcomerr2 libcurl3-gnutls libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libeggdbus-1-0
  libexpat1 libffi5 libgcc1 libgcrypt11 libgdbm3 libglib2.0-0 libglib2.0-data
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgudev-1.0-0 libidn11
  libk5crypto3 libkeyutils1 libklibc libkrb5-3 libkrb5support0 libldap-2.4-2
  liblocale-gettext-perl libmagic1 libncurses5 libncursesw5 libnih-dbus1
  libnih1 libnm-glib2 libnm-util1 libnspr4-0d libnss3-1d
  libpackagekit-glib2-12 libpam-ck-connector libpam-modules libpam-runtime
  libpam0g libpcre3 libplymouth2 libpng12-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libreadline6 libsasl2-2 libsasl2-modules libselinux1
  libsepol1 libslang2 libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0
  libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2
  lsb-base lsb-release lzma make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase openssl passwd perl perl-base
  perl-modules plymouth plymouth-theme-ubuntu-text procps psmisc python
  python-apt python-central python-dbus python-gdbm python-gnupginterface
  python-gobject python-minimal python-packagekit python-software-properties
  python-support python2.6 python2.6-minimal readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils tzdata
  ubuntu-keyring ucf udev unattended-upgrades update-manager-core upstart
  util-linux uuid-runtime xml-core zlib1g
The following packages will be upgraded:
  packagekit packagekit-backend-apt
2 upgraded, 164 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 55.5MB/63.9MB of archives.
After this operation, 235MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libc-bin 2.11.1-0ubuntu7.5 [723kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main libattr1 1:2.4.44-1 [11.9kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main libacl1 2.2.49-2 [27.1kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main coreutils 7.4-2ubuntu3 [2,435kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/main gcc-4.4-base 4.4.3-4ubuntu5 [118kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgcc1 1:4.4.3-4ubuntu5 [55.2kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid/main libstdc++6 4.4.3-4ubuntu5 [348kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid/main lzma 4.43-14ubuntu2 [59.7kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid/main perl-base 5.10.1-8ubuntu2 [1000kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid/main liblocale-gettext-perl 1.05-6 [21.7kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid/main libtext-iconv-perl 1.7-2 [18.3kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid/main libtext-charwidth-perl 0.04-6 [11.8kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid/main libtext-wrapi18n-perl 0.06-7 [9,010B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid/main debconf-i18n 1.5.28ubuntu4 [178kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid/main debconf 1.5.28ubuntu4 [148kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid/main findutils 4.4.2-1ubuntu1 [391kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6 2.11.1-0ubuntu7.5 [3,779kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ lucid/main libselinux1 2.0.89-4 [81.4kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main apt 0.7.25.3ubuntu9.3 [1,815kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdbus-1-3 1.2.16-2ubuntu4 [128kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ lucid/main libpcre3 7.8-3build1 [213kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ lucid/main zlib1g 1:1.2.3.3.dfsg-15ubuntu1 [75.9kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libglib2.0-0 2.24.1-0ubuntu1 [1,029kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdbus-glib-1-2 0.84-1 [158kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdbus-glib-1-2 0.84-1 [158kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ lucid/main python2.6-minimal 2.6.5-1ubuntu6 [1,354kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ lucid/main mime-support 3.48-1ubuntu1 [34.6kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libbz2-1.0 1.0.5-4ubuntu0.1 [45.5kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdb4.8 4.8.24-1ubuntu1 [674kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ lucid/main libncursesw5 5.7+20090803-2ubuntu3 [214kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ lucid/main readline-common 6.1-1 [54.0kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ lucid/main libncurses5 5.7+20090803-2ubuntu3 [189kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ lucid/main libreadline6 6.1-1 [143kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsqlite3-0 3.6.22-1 [294kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ lucid/main python2.6 2.6.5-1ubuntu6 [2,463kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-minimal 2.6.5-0ubuntu1 [21.3kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ lucid/main python 2.6.5-0ubuntu1 [148kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-central 0.6.15ubuntu1 [47.6kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-support 1.0.4ubuntu1 [32.0kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ lucid/main libffi5 3.0.9-1 [16.1kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-gobject 2.21.1-0ubuntu3 [210kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-dbus 0.83.0-1ubuntu3 [180kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ lucid/main app-install-data 0.10.04.7 [7,263kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main apt-utils 0.7.25.3ubuntu9.3 [239kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ lucid/main lsb-release 4.0-0ubuntu8 [26.8kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-apt 0.7.94.2ubuntu6.2 [180kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgdbm3 1.8.3-9 [45.2kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-gdbm 2.6.5-0ubuntu2 [13.4kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libusb-0.1-4 2:0.1.12-14ubuntu0.2 [20.5kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ lucid/main gpgv 1.4.10-2ubuntu1 [206kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ lucid/main gnupg 1.4.10-2ubuntu1 [1,069kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-gnupginterface 0.3.2-9.1 [19.1kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.11 [200kB]
Get:54 http://us.archive.ubuntu.com/ubuntu/ lucid/main ucf 3.0025 [68.1kB]     
Get:55 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main unattended-upgrades 0.55ubuntu4 [20.5kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ lucid/main iso-codes 3.12.1-1 [2,642kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-software-properties 0.75.10.1 [30.8kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ lucid/main base-passwd 3.5.22 [40.5kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam0g 1.1.1-2ubuntu5 [123kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ lucid/main gawk 1:3.1.6.dfsg-4build1 [512kB]
Get:61 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main base-files 5.0.0ubuntu20.10.04.2 [70.2kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam-modules 1.1.1-2ubuntu5 [358kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ lucid/main sensible-utils 0.0.1ubuntu3 [6,436B]
Get:64 http://us.archive.ubuntu.com/ubuntu/ lucid/main debianutils 3.2.2 [49.0kB]
Get:65 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main e2fslibs 1.41.11-1ubuntu2.1 [140kB]
Get:66 http://us.archive.ubuntu.com/ubuntu/ lucid/main passwd 1:4.1.4.2-1ubuntu2 [881kB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ lucid/main libuuid1 2.17.2-0ubuntu1 [61.3kB]
Get:68 http://us.archive.ubuntu.com/ubuntu/ lucid/main libblkid1 2.17.2-0ubuntu1 [110kB]
Get:69 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcomerr2 1.41.11-1ubuntu2.1 [50.7kB]
Get:70 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libss2 1.41.11-1ubuntu2.1 [55.7kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnih1 1.0.1-1 [127kB] 
Get:72 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnih-dbus1 1.0.1-1 [13.8kB]
Get:73 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsepol1 2.0.40-2 [120kB]
Get:74 http://us.archive.ubuntu.com/ubuntu/ lucid/main sysvinit-utils 2.87dsf-4ubuntu17 [111kB]
Get:75 http://us.archive.ubuntu.com/ubuntu/ lucid/main insserv 1.12.0-14 [68.2kB]
Get:76 http://us.archive.ubuntu.com/ubuntu/ lucid/main sysv-rc 2.87dsf-4ubuntu17 [79.1kB]
Get:77 http://us.archive.ubuntu.com/ubuntu/ lucid/main mount 2.17.2-0ubuntu1 [174kB]
Get:78 http://us.archive.ubuntu.com/ubuntu/ lucid/main sed 4.2.1-6 [176kB]     
Get:79 http://us.archive.ubuntu.com/ubuntu/ lucid/main ncurses-bin 5.7+20090803-2ubuntu3 [310kB]
Get:80 http://us.archive.ubuntu.com/ubuntu/ lucid/main lsb-base 4.0-0ubuntu8 [25.6kB]
Get:81 http://us.archive.ubuntu.com/ubuntu/ lucid/main initscripts 2.87dsf-4ubuntu17 [73.4kB]
Get:82 http://us.archive.ubuntu.com/ubuntu/ lucid/main makedev 2.3.1-89ubuntu1 [42.5kB]
Get:83 http://us.archive.ubuntu.com/ubuntu/ lucid/main module-init-tools 3.11.1-2ubuntu1 [94.1kB]
Get:84 http://us.archive.ubuntu.com/ubuntu/ lucid/main initramfs-tools-bin 0.92bubuntu78 [52.0kB]
Get:85 http://us.archive.ubuntu.com/ubuntu/ lucid/main libklibc 1.5.17-4ubuntu1 [46.7kB]
Get:86 http://us.archive.ubuntu.com/ubuntu/ lucid/main klibc-utils 1.5.17-4ubuntu1 [146kB]
Get:87 http://us.archive.ubuntu.com/ubuntu/ lucid/main busybox-initramfs 1:1.13.3-1ubuntu11 [155kB]
Get:88 http://us.archive.ubuntu.com/ubuntu/ lucid/main cpio 2.10-1ubuntu2 [112kB]
Get:89 http://us.archive.ubuntu.com/ubuntu/ lucid/main initramfs-tools 0.92bubuntu78 [88.5kB]
Get:90 http://us.archive.ubuntu.com/ubuntu/ lucid/main procps 1:3.2.8-1ubuntu4 [230kB]
Get:91 http://us.archive.ubuntu.com/ubuntu/ lucid/main adduser 3.112ubuntu1 [120kB]
Get:92 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdrm2 2.4.18-1ubuntu3 [410kB]
Get:93 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdrm-intel1 2.4.18-1ubuntu3 [409kB]
Get:94 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdrm-nouveau1 2.4.18-1ubuntu3 [401kB]
Get:95 http://us.archive.ubuntu.com/ubuntu/ lucid/main libdrm-radeon1 2.4.18-1ubuntu3 [399kB]
Get:96 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpng12-0 1.2.42-1ubuntu2.1 [177kB]
Get:97 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mountall 2.15.3 [52.5kB]
Get:98 http://us.archive.ubuntu.com/ubuntu/ lucid/main net-tools 1.60-23ubuntu2 [237kB]
Get:99 http://us.archive.ubuntu.com/ubuntu/ lucid/main netbase 4.35ubuntu3 [21.5kB]
Get:100 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ifupdown 0.6.8ubuntu29.1 [60.3kB]
Get:101 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main upstart 0.6.5-7 [289kB]
Get:102 http://us.archive.ubuntu.com/ubuntu/ lucid/main libslang2 2.2.2-2ubuntu1 [506kB]
Get:103 http://us.archive.ubuntu.com/ubuntu/ lucid/main util-linux 2.17.2-0ubuntu1 [532kB]
Get:104 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main e2fsprogs 1.41.11-1ubuntu2.1 [792kB]
Get:105 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6-i686 2.11.1-0ubuntu7.5 [1,228kB]
Get:106 http://us.archive.ubuntu.com/ubuntu/ lucid/main ca-certificates 20090814 [147kB]
Get:107 http://us.archive.ubuntu.com/ubuntu/ lucid/main libmagic1 5.03-5ubuntu1 [392kB]
Get:108 http://us.archive.ubuntu.com/ubuntu/ lucid/main file 5.03-5ubuntu1 [47.4kB]
Get:109 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgpg-error0 1.6-1ubuntu2 [18.4kB]
Get:110 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgcrypt11 1.4.4-5ubuntu2 [254kB]
Get:111 http://us.archive.ubuntu.com/ubuntu/ lucid/main libtasn1-3 2.4-1 [45.7kB]
Get:112 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgnutls26 2.8.5-2 [383kB]
Get:113 http://us.archive.ubuntu.com/ubuntu/ lucid/main libkeyutils1 1.2-12 [6,220B]
Get:114 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5support0 1.8.1+dfsg-2ubuntu0.3 [42.4kB]
Get:115 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libk5crypto3 1.8.1+dfsg-2ubuntu0.3 [96.3kB]
Get:116 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5-3 1.8.1+dfsg-2ubuntu0.3 [350kB]
Get:117 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.3 [120kB]
Get:118 http://us.archive.ubuntu.com/ubuntu/ lucid/main libidn11 1.15-2 [156kB]
Get:119 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsasl2-2 2.1.23.dfsg1-5ubuntu1 [109kB]
Get:120 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap-2.4-2 2.4.21-0ubuntu5.3 [202kB]
Get:121 http://us.archive.ubuntu.com/ubuntu/ lucid/main libcurl3-gnutls 7.19.7-1ubuntu1 [216kB]
Get:122 http://us.archive.ubuntu.com/ubuntu/ lucid/main gnupg-curl 1.4.10-2ubuntu1 [75.4kB]
Get:123 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgpm2 1.20.4-3.2ubuntu2 [34.3kB]
Get:124 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsasl2-modules 2.1.23.dfsg1-5ubuntu1 [159kB]
Get:125 http://us.archive.ubuntu.com/ubuntu/ lucid/main make 3.81-7ubuntu1 [156kB]
Get:126 http://us.archive.ubuntu.com/ubuntu/ lucid/main perl-modules 5.10.1-8ubuntu2 [3,479kB]
Get:127 http://us.archive.ubuntu.com/ubuntu/ lucid/main perl 5.10.1-8ubuntu2 [3,709kB]
Get:128 http://us.archive.ubuntu.com/ubuntu/ lucid/main ubuntu-keyring 2010.11.09 [11.0kB]
Get:129 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam-runtime 1.1.1-2ubuntu5 [115kB]
Get:130 http://us.archive.ubuntu.com/ubuntu/ lucid/main libexpat1 2.0.1-7ubuntu1 [139kB]
Get:131 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxau6 1:1.0.5-1 [13.9kB]
Get:132 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxdmcp6 1:1.0.3-1 [18.2kB]
Get:133 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb1 1.5-2 [39.4kB] 
Get:134 http://us.archive.ubuntu.com/ubuntu/ lucid/main libx11-data 2:1.3.2-1ubuntu3 [220kB]
Get:135 http://us.archive.ubuntu.com/ubuntu/ lucid/main libx11-6 2:1.3.2-1ubuntu3 [816kB]
Get:136 http://us.archive.ubuntu.com/ubuntu/ lucid/main psmisc 22.10-1 [58.0kB]
Get:137 http://us.archive.ubuntu.com/ubuntu/ lucid/main sgml-base 1.26 [11.7kB]
Get:138 http://us.archive.ubuntu.com/ubuntu/ lucid/main uuid-runtime 2.17.2-0ubuntu1 [63.4kB]
Get:139 http://us.archive.ubuntu.com/ubuntu/ lucid/main xml-core 0.13 [23.4kB] 
Get:140 http://us.archive.ubuntu.com/ubuntu/ lucid/main libck-connector0 0.4.1-3ubuntu1 [56.9kB]
Get:141 http://us.archive.ubuntu.com/ubuntu/ lucid/main libeggdbus-1-0 0.6-1 [90.3kB]
Get:142 http://us.archive.ubuntu.com/ubuntu/ lucid/main libpolkit-gobject-1-0 0.96-2 [47.9kB]
Get:143 http://us.archive.ubuntu.com/ubuntu/ lucid/main dbus 1.2.16-2ubuntu4 [189kB]
Get:144 http://us.archive.ubuntu.com/ubuntu/ lucid/main consolekit 0.4.1-3ubuntu1 [97.5kB]
Get:145 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libglib2.0-data 2.24.1-0ubuntu1 [982B]
Get:146 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libnspr4-0d 4.8.6-0ubuntu0.10.04.2 [125kB]
Get:147 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libnss3-1d 3.12.8-0ubuntu0.10.04.1 [1,122kB]
Get:148 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnm-util1 0.8-0ubuntu3 [119kB]
Get:149 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnm-glib2 0.8-0ubuntu3 [64.3kB]
Get:150 http://us.archive.ubuntu.com/ubuntu/ lucid/main libpam-ck-connector 0.4.1-3ubuntu1 [8,042B]
Get:151 http://us.archive.ubuntu.com/ubuntu/ lucid/main libpolkit-backend-1-0 0.96-2 [76.7kB]
Get:152 http://us.archive.ubuntu.com/ubuntu/ lucid/main shared-mime-info 0.71-1ubuntu2 [428kB]
Fetched 55.5MB in 14min 29s (63.8kB/s)                                         
E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
michael@freegeek:~$>
```At this point I am in over my head.
I think I'll take a break and pull the rest of my hair out.

---

### Post by ubupatzer on 2010-11-29
This is where I am now:

"You have 2 broken packages on your system!
Use the "Broken" filter to locate it."

Broken packages found: Synaptic Package Manager>Custom Filters>Broken

So: Edit>Fix Broken Packages>Apply Marked Changes

But error message:

```
E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```Is there anything left but reinstall?

---

### Post by sikander3786 on 2010-11-29
Re-install may be a choice and most the time, if there is not a lot of settings/configuartion involved, it is less time consuming to re-install the OS instead of trying to repair it.

Try these as the last resort.

```
sudo apt-get dist-upgrade
```

Or if aptitude is installed,

```
sudo aptitude safe-upgrade
```

---

### Post by ubupatzer on 2010-11-29
```
michael@freegeek:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  packagekit: Depends: libapt-pkg-libc6.10-6-4.8
              Depends: libc6 (>= 2.7) but it is not installed
              Depends: libdbus-1-3 (>= 1.0.2) but it is not installed
              Depends: libdbus-glib-1-2 (>= 0.78) but it is not installed
              Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
              Depends: libnm-glib2 (>= 0.8~a~git.20090826t185111.79489be) but it is not installed
              Depends: libpackagekit-glib2-12 (= 0.5.7-0ubuntu2.1) but it is not installed
              Depends: libpolkit-backend-1-0 (>= 0.94) but it is not installed
              Depends: libpolkit-gobject-1-0 (>= 0.94) but it is not installed
              Depends: libsqlite3-0 (>= 3.6.22) but it is not installed
              Depends: dbus but it is not installed
  packagekit-backend-apt: Depends: libapt-pkg-libc6.10-6-4.8
                          Depends: libc6 (>= 2.3.6-6~) but it is not installed
                          Depends: libdbus-1-3 (>= 1.0.2) but it is not installed
                          Depends: libdbus-glib-1-2 (>= 0.78) but it is not installed
                          Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                          Depends: python but it is not installed
                          Depends: python-central (>= 0.6.11) but it is not installed
                          Depends: python-packagekit (= 0.5.7-0ubuntu2.1) but it is not installed
                          Depends: app-install-data but it is not installed
                          Depends: python-apt (>= 0.7.13.2) but it is not installed
                          Depends: python-gdbm but it is not installed
                          Depends: update-manager-core but it is not installed
                          Depends: python-software-properties but it is not installed
                          Recommends: apt-xapian-index but it is not installed
E: Unmet dependencies. Try using -f.
michael@freegeek:~$ 


``````
michael@freegeek:~$ sudo aptitude safe-upgrade
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
open: 180; closed: 4941; defer: 5695; conflict: 2                              oThe following packages have unmet dependencies:
  packagekit: Depends: libapt-pkg-libc6.10-6-4.8 which is a virtual package.
              Depends: libc6 (>= 2.7) but it is not installable
              Depends: libdbus-1-3 (>= 1.0.2) but it is not installable
              Depends: libdbus-glib-1-2 (>= 0.78) but it is not installable
              Depends: libglib2.0-0 (>= 2.23.5) but it is not installable
              Depends: libnm-glib2 (>= 0.8~a~git.20090826t185111.79489be) but it is not installable
              Depends: libpackagekit-glib2-12 (= 0.5.7-0ubuntu2.1) but it is not installable
              Depends: libpolkit-backend-1-0 (>= 0.94) but it is not installable
              Depends: libpolkit-gobject-1-0 (>= 0.94) but it is not installable
              Depends: libsqlite3-0 (>= 3.6.22) but it is not installable
              Depends: dbus but it is not installable
  packagekit-backend-apt: Depends: libapt-pkg-libc6.10-6-4.8 which is a virtual package.
                          Depends: libc6 (>= 2.3.6-6~) but it is not installable
                          Depends: libdbus-1-3 (>= 1.0.2) but it is not installable
                          Depends: libdbus-glib-1-2 (>= 0.78) but it is not installable
                          Depends: libglib2.0-0 (>= 2.12.0) but it is not installable
                          Depends: python but it is not installable
                          Depends: python-central (>= 0.6.11) but it is not installable
                          Depends: python-packagekit (= 0.5.7-0ubuntu2.1) but it is not installable
                          Depends: app-install-data but it is not installable
                          Depends: python-apt (>= 0.7.13.2) but it is not installable
                          Depends: python-gdbm but it is not installable
                          Depends: update-manager-core but it is not installable
                          Depends: python-software-properties but it is not installable
michael@freegeek:~$ 

```And now...?

---

