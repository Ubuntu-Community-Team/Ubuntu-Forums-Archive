---
title: "Error while loading shared libraries : /lib/libc.so.6 during startup"
date: 2010-06-03
forum: General Help
---

### Post by tankjer on 2010-06-03
After the upgrades have installed on my installation of Ubuntu 10.4 (there were some kernel upgrades, I don't remember if there was any libc update there) it asked me to do a reboot. So I did and I got that error when Ubuntu was starting:
```
/bin/sh: error while loading shared libraries: /lib/libc.so.6: invalid ELF header
Kernel panic - not syncing: Attempted to kill init!
```And if I run Ubuntu in recovery mode there's what I get after this:
```
Pid: 1, comm: init: Not tainted 2.6.32-22-generic #35-Ubuntu
```There's also Call Trace after this, and a bit of text there, but as I'm rewriting those errors from a photo captured (because I cannot find logs of this in /var/log/) I will skip it unless it's needed to solve the problem.
**EDIT1**: I cannot find anybody who had this problem during startup, there are only guys who had this during compiling or installing software

---

### Post by arrange on 2010-06-03
Can you boot into a LiveCD, mount the Ubuntu partition and post```

ls -l /media/*/var/cache/apt/archives/libc6*
md5sum /media/*/lib/libc.so.6
```

---

### Post by tankjer on 2010-06-03
I was writing that post from Live CD, and I have mounted it already at /mnt
```
ubuntu@ubuntu:/var$ ls -l /mnt/var/cache/apt/archives/libc*
-rw-r--r-- 1 root root 16490158 2010-05-25 20:07 /mnt/var/cache/apt/archives/libc6-dbg_2.11.1-0ubuntu7.1_i386.deb
-rw-r--r-- 1 root root   624014 2010-01-27 02:05 /mnt/var/cache/apt/archives/libcfitsio3_3.230-2_i386.deb
-rw-r--r-- 1 root root   642266 2010-01-27 03:05 /mnt/var/cache/apt/archives/libcln6_1.3.1-2_i386.deb
ubuntu@ubuntu:/var$ md5sum /mnt/lib/libc.so.6
b6f5fd65df31dc75d7850b36acad6931  /mnt/lib/libc.so.6
```

---

### Post by tankjer on 2010-06-03
I have right now upgraded the libc-bin, libc6, and few others with 'libc' in their names package in Live CD. I have checked the libc.so.6 file in /lib/ (in ramdisk of Live CD) and its md5 checksum is 0dd96e3bce070c74c210328a67bef652
In properies it said it's a 'Link to shared library (application/x-sharedlib)' and its link target is 'libc-2.11.1.so'.
I have checked the properties of libc.so.6 file in /mnt/lib/ (in my mounted Ubuntu installation) and it says it's 'Link to program (application/octet-stream)', and its link target is 'libc-2.11.1.so' too. I have no idea what to do now... should I copy the libc.so.6 from Live CD to the Ubuntu install (with backuping first) or should I copy that libc-2.11.1.so? I'm thinking also about why types of files are different (why one is linked to x-sharedlib and other is linked to octet-stream)...

---

### Post by arrange on 2010-06-03
Yes, backup the **libc-2.11.1.so** on your HDD and copy the one from LiveCD over it (if the *md5sum*s do not match).

---

### Post by tankjer on 2010-06-03
I have tried both the non upgraded Livecd version, and version after upgrade. Unfortunately none worked, and I get still the same error. I noticed that there's libc6-dev but no libc6 package in /var/cache/apt/archives, does that mean anything?

---

### Post by arrange on 2010-06-03
[COLOR="Silver"]does that mean anything? [/COLOR]
No.

Are you sure you can't find the error messages in */var/log/syslog*? If so, you can also take a photo or something and upload it somewhere so that we can see all the output.

---

### Post by tankjer on 2010-06-03
> **arrange said:**
> Are you sure you can't find the error messages in */var/log/syslog*? If so, you can also take a photo or something and upload it somewhere so that we can see all the output.
I couldn't find the errors in that log file, photo should be in attachment.

---

### Post by arrange on 2010-06-03
Ahh, now it's clearer. What Grub are you using? Try this:

when you restart and see the Grub options, press **e** to edit the entry. Then delete the line starting with **initrd** and don't touch the other ones, so it will look something like this (of course, yours will be a little different, but note there is no *initrd* line)```
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
   recordfail
   insmod ext2
   set root='(hd1,1)'
   search --no-floppy --fs-uuid --set 6a9e5b6b-b754-43a1-a213-6965349890cc
   linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=6a9e5b6b-b754-43a1-a213-6965349890cc ro   quiet splash
```Then press Ctrl+x to boot. Report if you were successful. :)

---

### Post by tankjer on 2010-06-03
Got another error, this time it's 'VFS: Cannot open root device "UUID=longnamethere" or unknown-block(0,0)"
Starting from the first attachment:
The error after removing initrd line
GRUB version, GRUB menu entry
Recovery mode after removing initrd line

---

### Post by arrange on 2010-06-03
Do you have an older kernel to boot from there (in the Grub menu)? Try it with and (if not successful) without the *initrd* line again.

---

### Post by tankjer on 2010-06-03
> **arrange said:**
> Do you have an older kernel to boot from there (in the Grub menu)? Try it with and (if not successful) without the *initrd* line again.
Sorry for not too fast response, I didn't saw that there was new page during refreshing.
Unfortunately I don't have any other kernels, neither in Grub menu or in /boot/.

---

### Post by arrange on 2010-06-03
Can you check if the disk is OK?
Do you know how to *chroot*?
Can you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by tankjer on 2010-06-03
> **arrange said:**
> Can you check if the disk is OK?
Do you know how to *chroot*?
Can you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)
I have been checking it with e2fsck -f three times now. I can write files, I can read files, no signs of bad sectors.
I don't know (yet) how to chroot, I will search on how to do this.
Boot_info_script:
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8447 MB, 8447459328 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16498944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,498,754    16,498,692  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        583d1afd-6b96-47ca-8a41-1491b80cae69   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/583d1afd-6b96-47ca-8a41-1491b80cae69 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=583d1afd-6b96-47ca-8a41-1491b80cae69 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
    echo    'Wczytywanie systemu Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=583d1afd-6b96-47ca-8a41-1491b80cae69 ro single 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583d1afd-6b96-47ca-8a41-1491b80cae69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=583d1afd-6b96-47ca-8a41-1491b80cae69 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.32-22-generic
   5.2GB: boot/vmlinuz-2.6.32-22-generic
   4.8GB: initrd.img
   5.2GB: vmlinuz
```

---

### Post by tankjer on 2010-06-03
I am running Synaptic in chroot right now. I have mounted /dev/sda1 in /mnt. Should I reinstall libc-bin, libc6 and dependencies?

*also Off-topic, should I edit posts or just post a new one when I want to write some more info, just as right now?*

---

### Post by tankjer on 2010-06-04
When reinstalling libc6 I got that error:
```
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

---

### Post by tankjer on 2010-06-04
... and when trying to remove libc6 through apt-get during chroot I need to remove those too:
```
  acpi-support acpid adduser advancecomp akonadi-server akregator alacarte
  alarm-clock alarm-clock-applet alsa-base alsa-utils amarok amarok-utils
  amaya amor anacron and ant ant-gcj ant-optional ant-optional-gcj
  apache2-utils apparmor apparmor-utils apport apport-gtk apt
  apt-transport-https apt-utils apt-xapian-index aptdaemon aptitude apturl
  apturl-common ark asoundconf-gtk aspell aspell-en at at-spi audacity
  autoconf automake autopano-sift avahi-autoipd avahi-daemon avahi-utils
  avidemux avidemux-plugins-common avidemux-plugins-gtk base-files base-passwd
  bash bash-completion bc beep bind9-host binfmt-support binutils bisonc++
  bittornado bittornado-gui bleachbit bogofilter bogofilter-bdb bomber bovo
  brltty brltty-x11 bsdmainutils bsdutils busybox-initramfs bzip2
  ca-certificates ca-certificates-java cabextract cantor capplets-data catfish
  cdparanoia cervisia checkbox checkbox-gtk cli-common command-not-found
  compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf compizconfig-settings-manager computer-janitor
  computer-janitor-gtk console-setup consolekit coreutils courier-authdaemon
  courier-authlib courier-authlib-userdb courier-base courier-imap courier-pop
  cpio cpp cpp-4.4 cron cryptsetup cups cups-bsd cups-client
  cups-driver-gutenprint cvs cvsservice dash dbconfig-common dbus dbus-x11 dc
  dcraw ddclient debconf debconf-i18n debianutils deborphan default-jdk
  default-jre default-jre-headless defoma desktop-file-utils dhcp3-client
  dhcp3-common dialog dictionaries-common diffutils digikam discus dmidecode
  dmsetup dnsmasq-base dnsutils doc-base docbook-xml dolphin dosfstools dpkg
  dragonplayer dvd+rw-tools dvdauthor dvgrab e2fslibs e2fsprogs ecryptfs-utils
  ed eject empathy-common enblend enfuse eog erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl esound-clients evince evolution-data-server
  evolution-webcal exiv2 expect fancontrol ffmpeg file file-roller filezilla
  findutils finger firefox firefox-branding firefox-gnome-support firestarter
  flashplugin-installer fontconfig fontconfig-config foo2zjs foomatic-db
  foomatic-db-engine foomatic-filters fortune-mod fortunes-min fotoxx
  freeglut3 frei0r-plugins friendly-recovery ftp ftplib3 fuse-utils g++
  g++-4.4 gamin gawk gcalctool gcc gcc-4.4 gcj-4.4-jre-lib
  gconf-defaults-service gconf2 gconf2-common gdb gdebi gdebi-core gdm
  gdm-guest-session gedit genisoimage getdeb-repository gettext gettext-base
  gfire ghostscript ghostscript-cups ghostscript-x gifsicle gimp
  gir1.0-atk-1.0 gir1.0-clutter-1.0 gir1.0-glib-2.0 gir1.0-gtk-2.0
  gir1.0-pango-1.0 gksu gnome-about gnome-accessibility-themes gnome-alsamixer
  gnome-applets gnome-applets-data gnome-codec-install gnome-common
  gnome-control-center gnome-core gnome-desktop-sharp2 gnome-disk-utility
  gnome-doc-utils gnome-icon-theme gnome-keyring gnome-launch-box gnome-media
  gnome-media-common gnome-menus gnome-panel gnome-panel-data
  gnome-photo-printer gnome-power-manager gnome-screensaver gnome-session
  gnome-session-bin gnome-settings-daemon gnome-shell
  gnome-stracciatella-session gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-themes gnome-themes-extras
  gnome-themes-more gnome-themes-selected gnome-user-guide gnome-utils gnugo
  gnupg gnupg-agent gnupg-curl gozerbot gozerbot-plugins gpaint gpgv granatier
  graphviz grep groff-base grub-common grub-pc gsfonts gstreamer0.10-alsa
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin
  gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk2-engines-smooth gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin
  gvfs-fuse gwenview gzip hal hdparm hostname hpijs hplip hplip-data htop
  hugin hugin-tools humanity-icon-theme hunspell-en-ca hunspell-en-us ibus
  ibus-gtk ibus-m17n ibus-table icedtea-6-jre-cacao icoutils ifupdown
  imagemagick indicator-applet indicator-applet-session indicator-application
  indicator-me indicator-messages indicator-session indicator-sound info
  initramfs-tools initramfs-tools-bin initscripts inkscape inputattach insserv
  install-info intel-gpu-tools intltool iproute iptables iputils-arping
  iputils-ping iputils-tracepath ircd-ratbox ircd-ratbox-dbg irqbalance
  javahelp2 jetty jhead jockey-common jpegoptim jruby1.1 jsvc juk junit junit4
  kaddressbook kalarm kalgebra kalzium kamera kanagram kapman kappfinder
  kapptemplate kate katomic kbattleship kbd kblackbox kblocks kbounce
  kbreakout kbruch kbugbuster kcachegrind kcalc kcharselect kcolorchooser
  kcron kde-full kde-l10n-pl kde-minimal kde-window-manager kdeaccessibility
  kdeadmin kdeartwork kdeartwork-style kdebase-apps kdebase-bin
  kdebase-runtime kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins kdeedu kdegames
  kdegraphics kdegraphics-strigi-plugins kdelibs kdelibs-bin kdelibs4c2a
  kdelibs5 kdelirc kdemultimedia kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenlive kdepasswd kdepim kdepim-groupware
  kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards
  kdepimlibs5 kdeplasma-addons kdesdk kdesdk-kio-plugins kdesdk-misc
  kdesdk-scripts kdesdk-strigi-plugins kdetoys kdeutils kdf kdiamond kdm
  kerneloops-daemon keyutils kfilereplace-kde3 kfind kfloppy kfourinline
  kgamma kgeography kget kgoldrunner kgpg khangman kig kigo killbots
  kimagemapeditor kinfocenter kipi-plugins kiriki kjots kjumpingcube klettres
  klines klinkstatus-kde3 klipper kmag kmahjongg kmail kmines kmix kmousetool
  kmouth kmplot kmtrace knetwalk knode knotes kolf kollision kolourpaint4
  kommander-kde3 kompare konqueror konqueror-nsplugins konquest konsole
  konsolekalendar kontact kopete kopete-message-indicator korganizer
  kpartloader kpat kppp krdc kreversi krfb krosspython kruler ksame kscd
  kscreensaver kscreensaver-xsavers kshisen ksirk ksnapshot kspaceduel
  ksquares kstars ksudoku ksysguard ksysguardd ksystemlog kteatime ktimer
  ktimetracker ktouch ktron ktuberling kturtle ktux kubrick kuiviewer kuser
  kwalletmanager kweather kwordquiz kwrite lame language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-pack-kde-pl language-pack-kde-pl-base language-pack-pl
  language-pack-pl-base language-selector language-selector-common
  language-support-en language-support-writing-en laptop-detect
  launchpad-integration less lftp liba52-0.7.4 libaa1 libaccess-bridge-java
  libaccess-bridge-java-jni libacl1 libakonadiprivate1 libanthy0
  libapparmor-perl libapparmor1 libappframework-java libappindicator0 libapr1
  libaprutil1 libarchive1 libart-2.0-2 libart2-ruby libart2-ruby1.8
  libart2.0-cil libart2.0-cil-dev libasound2 libasound2-plugins libaspell15
  libass4 libatasmart4 libatk1-ruby libatk1-ruby1.8 libatk1.0-0 libatk1.0-data
  libatm1 libatspi1.0-0 libattica0 libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common3 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-qt3-1 libavahi-ui0 libavc1394-0 libavcodec52
  libavdevice52 libavfilter0 libavformat52 libavidemux0 libavutil49
  libbabl-0.0-0 libbeagle1 libbeansbinding-java libbind9-60 libblas3gf
  libblkid1 libbluetooth3 libbobcat2 libbonobo2-0 libbonoboui2-0
  libboost-program-options1.40.0 libboost-python1.40.0 libboost-thread1.40.0
  libbrlapi0.5 libbsd0 libburn4 libbz2-1.0 libc-client2007e libc-dev-bin libc6
  libc6-dbg libc6-dev libc6-i686 libcaca0 libcairo-perl libcairo-ruby1.8
  libcairo2 libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcddb2
  libcdio-cdda0 libcdio-paranoia0 libcdio10 libcdparanoia0 libcfitsio3
  libck-connector0 libclass-accessor-perl libcln6 libclucene0ldbl
  libclutter-1.0-0 libclutter-gtk-0.10-0 libcobertura-java libcolamd2.7.1
  libcomerr2 libcommons-beanutils-java libcommons-collections3-java
  libcommons-compress-java libcommons-daemon-java libcommons-digester-java
  libcommons-logging-java libcommons-net-java libcompizconfig0 libcroco3
  libcryptui0 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1
  libcupsppdc1 libcurl3 libcurl3-gnutls libcv-dev libcv4 libcvaux-dev
  libcvaux4 libcwidget3 libdaemon0 libdatrie1 libdb-je-java libdb4.7
  libdb4.7-java libdb4.7-java-gcj libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdbusmenu-glib1 libdbusmenu-gtk1 libdbusmenu-qt2 libdc1394-22 libdca0
  libdecoration0 libdevkit-power-gobject1 libdevmapper1.02.1 libdirectfb-1.2-0
  libdjvulibre21 libdns64 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  libdv4 libdvbpsi5 libdvdnav4 libdvdread4 libebackend1.2-0 libebml0
  libebook1.2-9 libecal1.2-7 libecryptfs0 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libedit2 libeggdbus-1-0
  libegroupwise1.2-13 libelf1 libenca0 libenchant1c2a libept0 libesd0
  libevdocument2 libevent-1.4-2 libevview2 libexchange-storage1.2-3 libexempi3
  libexif12 libexiv2-6 libexpat1 libfaac0 libfaad2 libffi5 libfftw3-3
  libfile-copy-recursive-perl libflac++6 libflac8 libfli1 libflickrnet2.2-cil
  libfont-afm-perl libfontconfig1 libfontenc1 libfreemarker-java libfreetype6
  libfreezethaw-perl libfribidi0 libfs6 libftdi1 libfuse2 libgadu3
  libgail-common libgail18 libgamin0 libgavl1 libgc1c2 libgcc1 libgcj-bc
  libgcj-common libgcj10 libgconf2-4 libgconf2-ruby libgconf2-ruby1.8
  libgconf2.0-cil libgconfmm-2.6-1c2 libgcr0 libgcrypt11 libgd2-xpm
  libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdbm3 libgdict-1.0-6
  libgdiplus libgdk-pixbuf2-ruby libgdk-pixbuf2-ruby1.8 libgdu-gtk0 libgdu0
  libgegl-0.0-0 libgeoip1 libgfortran3 libgif4 libgimp2.0 libgirepository1.0-0
  libgjs0 libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0
  libglade2-ruby libglade2-ruby1.8 libglade2.0-cil libglademm-2.4-1c2a
  libglew1.5 libglib-perl libglib2-ruby1.8 libglib2.0-0 libglib2.0-cil
  libglib2.0-cil-dev libglib2.0-data libglibmm-2.4-1c2a libglitz-glx1
  libglitz1 libglu1-mesa libgmime-2.4-2 libgmime2.4-cil libgmp3c2
  libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-keyring0
  libgnome-keyring1.0-cil libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil
  libgnome-vfs2.0-cil-dev libgnome-window-settings1 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-ruby
  libgnome2-ruby1.8 libgnome2-vfs-perl libgnome2.0-cil-dev libgnome2.24-cil
  libgnomecanvas2-0 libgnomecanvas2-ruby libgnomecanvas2-ruby1.8
  libgnomecups1.0-1 libgnomedesktop2.0-cil-dev libgnomedesktop2.20-cil
  libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil
  libgnomepanel2.24-cil-dev libgnomeprint2.2-0 libgnomeprintui2.2-0
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-ruby
  libgnomevfs2-ruby1.8 libgnutls26 libgomp1 libgoocanvas3 libgp11-0
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpm2
  libgpod-common libgpod4 libgraphite3 libgraphviz4 libgs8 libgsf-1-114
  libgsf-gnome-1-114 libgsl0ldbl libgsm1 libgssapi-krb5-2 libgssdp-1.0-2
  libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk-mozembed-ruby libgtk-mozembed-ruby1.8 libgtk-vnc-1.0-0 libgtk2-perl
  libgtk2-ruby libgtk2-ruby1.8 libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-cil-dev libgtkglext1 libgtkglext1-ruby libgtkglext1-ruby1.8
  libgtkhtml-editor0 libgtkhtml3.14-19 libgtkhtml3.14-cil-dev
  libgtkhtml3.16-cil libgtkmm-2.4-1c2a libgtksourceview2-2.0-cil
  libgtksourceview2-cil-dev libgtksourceview2.0-0 libgtkspell0 libgtop2-7
  libgucharmap7 libgudev-1.0-0 libgupnp-1.0-3 libgupnp-igd-1.0-2
  libgutenprint2 libgvfscommon0 libgweather-common libgweather1
  libhal-storage1 libhal1 libhamcrest-java libhighgui4 libhpmud0
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhunspell-1.2-0 libhyphen0 libibus1 libical0 libice-dev
  libice6 libicu42 libicu4j-java libid3tag0 libidl0 libidn11 libido-0.1-0
  libiec61883-0 libieee1284-3 libijs-0.35 libilmbase6 libimage-exiftool-perl
  libimobiledevice0 libindi0 libindicate-gtk2 libindicate-qt0 libindicate4
  libindicator0 libini4j-java libio-socket-ssl-perl libio-string-perl
  libiodbc2 libisc60 libisccc60 libisccfg60 libiso9660-7 libisofs6 libiw30
  libjack0 libjasper1 libjaxp1.3-java libjetty-java libjline-java libjna-java
  libjpeg-progs libjpeg62 libjsch-java libjson-glib-1.0-0 libjtidy-java
  libjzlib-java libk5crypto3 libkcddb4 libkdcraw8 libkdecorations4 libkdeedu4
  libkdegames5 libkdepim4 libkephal4 libkexiv2-8 libkeyutils1 libkfontinst4
  libkipi7 libkleo4 libkonq5 libkonqsidebarplugin4 libkopete4 libkpathsea5
  libkpgp4 libkrb5-3 libkrb5support0 libksane0 libkscreensaver5 libksgrd4
  libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblancelot0
  liblapack3gf liblastfm0 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 libldap-2.4-2 liblensfun0
  liblircclient0 liblocale-gettext-perl liblockfile1 liblog4j1.2-java
  libloudmouth1-0 liblouis0 liblpint-bonobo0 liblqr-1-0 libltdl-dev libltdl7
  liblua5.1-0 liblua50 liblualib50 liblucene2-java liblwres60 liblzma1
  libm17n-0 libmad0 libmagic1 libmagick++2 libmagickcore2 libmagickcore2-extra
  libmagickwand2 libmailtools-perl libmarble4 libmatroska0 libmcrypt4
  libmeanwhile1 libmetacity-private0 libmilter1.0.1 libmimelib4
  libmjpegtools-1.9 libmldbm-perl libmlt++3 libmlt2 libmng1 libmodplug0c2
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil
  libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-runtime2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono2.0-cil libmp3lame0 libmpcdec3 libmpeg2-4
  libmpfr1ldbl libmpg123-0 libmsn0.3 libmtp8 libmusicbrainz4c2a
  libmutter-private0 libmysqlclient16 libnautilus-extension1
  libnb-apisupport1-java libnb-ide12-java libnb-java3-java
  libnb-javaparser-java libnb-platform-devel-java libnb-platform11-java
  libnb-svnclientadapter-java libncurses5 libncursesw5
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls
  libnet-dbus-perl libnet-libidn-perl libnet-ssleay-perl libnewt0.52 libnice0
  libnih-dbus1 libnih1 libnl1 libnm-glib2 libnm-util1 libnotify-bin libnotify1
  libnova-0.12-2 libnspr4-0d libnss-mdns libnss3-1d libntfs-3g75 libntfs10
  libnunit2.4-cil libofa0 libogg0 liboil0.3 libokularcore1 liboobs-1-4
  libopenal1 libopenbabel3 libopencore-amrnb0 libopencore-amrwb0 libopenexr6
  libopengl-ruby libopengl-ruby1.8 libopenobex1 liborbit2 liboro-java libotf0
  libotr2 libpam-ck-connector libpam-gnome-keyring libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpanel-applet2-ruby
  libpanel-applet2-ruby1.8 libpango-perl libpango1-ruby libpango1-ruby1.8
  libpango1.0-0 libpango1.0-common libpangomm-1.4-1 libpano13-1 libpano13-bin
  libpaper-utils libpaper1 libparse-debianchangelog-perl libparted0debian1
  libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1 libperl5.10
  libphonon4 libpixman-1-0 libplasma-applet-system-monitor4
  libplasma-geolocation-interface4 libplasma3 libplasmaclock4
  libplasmagenericshell4 libplist1 libplot2c2 libplymouth2 libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpolkit-gtk-1-0 libpolkit-qt-1-0 libpoppler-glib4 libpoppler-qt4-3
  libpoppler5 libpopt0 libportaudio2 libpostproc51 libpq5 libprocesscore4
  libprocessui4 libprotobuf5 libprotoc5 libproxy0 libpst4 libpth20
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0
  libpython2.6 libqalculate4 libqca2 libqca2-plugin-ossl libqimageblitz4
  libqt3-mt libqt4-assistant libqt4-dbus libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql
  libqtscript4-uitools libqtscript4-xml libquicktime1 libraptor1 librarian0
  librasqal2 libraw1394-11 librdf0 libreadline6 librecode0 libregexp-java
  librpc-xml-perl librsvg2-2 librsvg2-2.0-cil-dev librsvg2-2.18-cil
  librsvg2-common librsvg2-ruby librsvg2-ruby1.8 libruby1.8 libsamplerate0
  libsane libsasl2-2 libsasl2-modules libschroedinger-1.0-0 libsctp1
  libsdl-image1.2 libsdl1.2debian libsdl1.2debian-pulseaudio libselinux1
  libsensors4 libsepol1 libservlet2.3-java libservlet2.4-java
  libservlet2.5-java libsexy2 libsgutils2-2 libshout3 libsidplay1
  libsigc++-2.0-0c2a libsilc-1.1-2 libsilcclient-1.1-3 libslang2 libslf4j-java
  libslp1 libsm-dev libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp15
  libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libsoundtouch1c2
  libsoup-gnome2.4-1 libsoup2.4-1 libsox-fmt-alsa libsox-fmt-base libsox1a
  libspectre1 libspeechd2 libspeex1 libspeexdsp1 libsqlite0 libsqlite3-0
  libss2 libssh-4 libssl0.9.8 libstartup-notification0 libstdc++6
  libstdc++6-4.4-dev libstlport4.6ldbl libstreamanalyzer0 libstreams0
  libsub-name-perl libsvn-java libsvn1 libswing-layout-java
  libswingworker-java libswingx-java libswscale0 libsysfs2 libt1-5
  libtag-extras1 libtag1-vanilla libtag1c2a libtagc0 libtalloc2 libtar
  libtaskmanager4 libtasn1-3 libtdb1 libtelepathy-farsight0 libtelepathy-glib0
  libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libthai0 libtheora0 libtidy-0.99-0 libtie-ixhash-perl
  libtiff4 libtimedate-perl libtool libtotem-plparser17 libts-0.0-0
  libtunepimp5 libtwolame0 libudev0 libunique-1.0-0 libupnp3 libupower-glib1
  liburi-perl libusb-0.1-4 libusb-1.0-0 libusbmuxd1 libuuid-perl libuuid1
  libv4l-0 libvamp-hostsdk3 libvcdinfo0 libvisual-0.4-0 libvisual-0.4-plugins
  libvlc2 libvlccore2 libvncserver0 libvorbis0a libvorbisenc2 libvorbisfile3
  libvte-ruby libvte-ruby1.8 libvte0.16-cil libvte0.16-cil-dev libvte9
  libwavpack1 libwbclient0 libweather-ion4 libwebkit-1.0-2 libwmf-bin
  libwmf0.2-7 libwmf0.2-7-gtk libwnck1.0-cil-dev libwnck2.20-cil libwnck22
  libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0 libwww-perl libwxbase2.6-0
  libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0 libx11-6 libx11-dev libx264-85
  libx86-1 libxapian15 libxau-dev libxau6 libxaw7 libxcb-atom1 libxcb-aux0
  libxcb-event1 libxcb-keysyms1 libxcb-render-util0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcb1-dev libxcomposite1
  libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxerces2-java libxext6
  libxfixes3 libxfont1 libxft2 libxi6 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x libxinerama1 libxkbfile1 libxklavier16
  libxml-commons-resolver1.1-java libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-twig-perl libxml-xpath-perl libxml2 libxml2-utils
  libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1
  libxss1 libxt-dev libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 libzephyr4 libzvbi0 light-themes linux-generic
  linux-headers-2.6.32-22 linux-headers-2.6.32-22-generic
  linux-headers-generic linux-image-2.6.32-22-generic linux-image-generic
  linux-sound-base lirc lksctp-tools lm-sensors localepurge locales
  lockfile-progs login logrotate lokalize lp-solve lsb-base lsb-release lshw
  lskat lsof ltrace lzma m17n-contrib m17n-db m4 makedev man-db marble mawk
  media-player-info megahal melt menu mesa-utils metacity metacity-common
  min12xxw mjpegtools mlocate mlock modemmanager module-init-tools
  mono-2.0-gac mono-gac mono-runtime mount mountall mousetweaks mscompress
  mtools mtpaint mtr-tiny mutter mutter-common myspell-en-au myspell-en-gb
  myspell-en-za mysql-client-core-5.1 mysql-server-core-5.1 nano nautilus
  nautilus-actions nautilus-data nautilus-filename-repairer nautilus-gksu
  nautilus-image-converter nautilus-open-terminal nautilus-wallpaper
  ncurses-base ncurses-bin net-tools netbase netbeans netcat-openbsd
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon notify-osd ntfs-3g
  ntfs-config ntfsprogs ntpdate nvidia-common obex-data-server okteta okular
  omega-rpg openarena openbsd-inetd openjdk-6-jdk openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openprinting-ppds openssh-client
  openssl optipng os-prober p7zip-full padevchooser palapeli paman paprefs
  parley parted passwd patch pavucontrol pavumeter pciutils pcmciautils perl
  perl-base perl-modules perl-suid perlmagick phonon phonon-backend-xine
  pidgin pidgin-libnotify pidgin-otr pidgin-plugin-pack pinentry-gtk2
  pinentry-qt4 pixelize pkg-config plasma-dataengines-addons
  plasma-dataengines-workspace plasma-desktop plasma-runners-addons
  plasma-scriptengine-javascript plasma-scriptengine-superkaramba
  plasma-wallpapers-addons plasma-widget-folderview plasma-widget-lancelot
  plasma-widgets-addons plasma-widgets-workspace plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11 pm-utils
  pm-utils-powersave-policy pnm2ppa policykit-1 policykit-1-gnome polkit-kde-1
  poppler-utils popularity-contest postfix powermgmt-base poxml ppp pppconfig
  pppoeconf pptp-linux preload printer-applet procps protobuf-compiler
  psfontmgr psmisc pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils pxljr
  python python-appindicator python-apport python-apt python-aptdaemon
  python-aptdaemon-gtk python-avahi python-brlapi python-bugbuddy python-cairo
  python-central python-chardet python-compizconfig python-configglue
  python-crypto python-cups python-cupshelpers python-dateutil python-dbus
  python-debian python-dns python-egenix-mxdatetime python-egenix-mxtools
  python-enchant python-evince python-evolution python-farsight
  python-feedparser python-fstab python-gconf python-gdbm python-glade2
  python-gmenu python-gnome2 python-gnome2-desktop python-gnomeapplet
  python-gnomecanvas python-gnomedesktop python-gnomekeyring python-gnomeprint
  python-gnupginterface python-gobject python-gst0.10 python-gtk2
  python-gtksourceview2 python-gtkspell python-gtop python-httplib2
  python-ibus python-imaging python-indicate python-iniparse python-kde4
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-levenshtein python-libxml2 python-louis python-lxml
  python-mako python-mediaprofiles python-metacity python-minimal python-newt
  python-notify python-numpy python-oauth python-opencv python-openssl
  python-pam python-papyon python-pexpect python-pkg-resources
  python-problem-report python-protobuf python-pyatspi python-pycurl
  python-pygoocanvas python-pyinotify python-pyorbit python-qt4
  python-qt4-dbus python-rdflib python-renderpm python-reportlab
  python-reportlab-accel python-rsvg python-serial python-simplejson
  python-sip python-smbc python-software-properties python-sqlalchemy
  python-support python-telepathy python-totem-plparser python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-tz
  python-uniconvertor python-utidylib python-virtkey python-vobject python-vte
  python-wadllib python-webkit python-wnck python-wxgtk2.6 python-wxversion
  python-xapian python-xdg python-xkit python-zope.interface python2.6
  python2.6-minimal qtpfsgui quanta rarian-compat rdesktop readline-common
  recordmydesktop rocs rsync rsyslog rtkit ruby ruby-gnome2 ruby1.8
  samba-common samba-common-bin sanduhr sane-utils screen
  screensaver-default-images seahorse sed setserial sgml-base sgml-data
  shared-mime-info skype smartdimmer smbclient software-center
  software-properties-gtk soprano-daemon soundconverter splix
  ssh-askpass-gnome ssl-cert step stopmotion strace subversion sudo sweeper
  swh-plugins synaptic syslinux system-config-printer-common
  system-config-printer-gnome system-config-printer-kde
  system-config-printer-udev system-tools-backends systemsettings sysv-rc
  sysvinit-utils tar tasksel tasksel-data tcl tcl8.4 tcl8.5 tcpd tcpdump
  telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle
  telepathy-mission-control-5 telepathy-salut telnet tidy time tk8.4 toshset
  totem-common translate-toolkit transmission-gtk trimage
  ttf-mscorefonts-installer ttf-symbol-replacement ttf-unfonts-core twolame
  tzdata tzdata-java ubufox ubuntu-artwork ubuntu-keyring ubuntu-minimal
  ubuntu-mono ubuntu-standard ubuntu-system-service ubuntu-wallpapers ucf udev
  udisks umbrello unattended-upgrades uno-libs3 unzip update-inetd
  update-manager update-manager-core update-notifier update-notifier-common
  upower upstart ure ureadahead usbmuxd usbutils util-linux uuid-runtime
  valgrind vbetool vgrabbj vim-common vim-tiny vlc vlc-nox vlc-plugin-pulse
  wamerican wbritish wget whiptail whois winbind wine1.2 wine1.2-gecko
  wireless-crda wireless-tools wodim wpasupplicant x-ttcidfont-conf x11-apps
  x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils xauth xbase-clients xchat xchat-common xdg-user-dirs
  xdg-user-dirs-gtk xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings
  xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xml-core xorg xsane
  xscreensaver-data xscreensaver-gl xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-mach64
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-v4l
  xsltproc xtrans-dev xulrunner-1.9.2 yelp zapping zenity zip zlib1g
UWAGA: Zostan&#261; usuni&#281;te nast&#281;puj&#261;ce istotne pakiety.
Nie powinno si&#281; tego robi&#263;, chyba &#380;e dok&#322;adnie wiesz co robisz!
  apt libc6 (z powodu apt) libgcc1 (z powodu apt) libstdc++6 (z powodu apt)
  base-files base-passwd (z powodu base-files) libpam-modules (z powodu
  base-files) bash debianutils (z powodu bash) dash (z powodu bash)
  libncurses5 (z powodu bash) bsdutils coreutils libacl1 (z powodu coreutils)
  libattr1 (z powodu coreutils) libselinux1 (z powodu coreutils) diffutils
  dpkg lzma (z powodu dpkg) e2fsprogs e2fslibs (z powodu e2fsprogs) libblkid1
  (z powodu e2fsprogs) libcomerr2 (z powodu e2fsprogs) libss2 (z powodu
  e2fsprogs) libuuid1 (z powodu e2fsprogs) util-linux (z powodu e2fsprogs)
  findutils grep gzip hostname upstart (z powodu hostname) login libpam0g (z
  powodu login) libpam-runtime (z powodu login) mount libsepol1 (z powodu
  mount) ncurses-base ncurses-bin perl-base python-minimal python2.6-minimal
  (z powodu python-minimal) sed install-info (z powodu sed) tar lsb-base (z
  powodu util-linux) tzdata (z powodu util-linux) libslang2 (z powodu
  util-linux) zlib1g (z powodu util-linux)

```... that means whole system. When I tried to reinstall, or remove some other packages using Synaptic I got also:
```
Error failed to fork pty
``` in an error popup, and ```
vte_terminal_forkpty() failed. Bad file descriptor
``` in the console.
As I use polish version of Live CD, 'Zostan&#261; usuni&#281;te nast&#281;puj&#261;ce istotne pakiety' = 'Those essential packages will be removed'. About the rest, I think that there is no comment needed. :-?

---

### Post by tankjer on 2010-06-04
It couldn't find /etc/pts, so I wrote this in fstab:
```
devpts /dev/pts devpts noexec,nosuid,gid=5,mode=620 0 0
```ran mount -a (still in chroot), and now synaptic seems to work, except that there's ```
Cannot find /proc/version - is /proc mounted?
``` after it will do the work. I could reinstall libc6 though, now I will try to reinstall the rest. Hope there will be soon end of all of this...

---

### Post by tankjer on 2010-06-04
Problem still persists, both in 'normal' startup and in recovery mode, with and without initrd (though when without initrd there's that VFS error instead)

---

### Post by tankjer on 2010-06-04
After restarting of the Live CD I get 'Error failed to fork pty' again while trying to install, reinstall, uninstall etc. anything in synaptic while chrooting...
When typing mount during chroot I get:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
```Are there entries starting with 'none on...' normal?
**EDIT1**: I just needed to mount -a, exit the chroot, and go chroot again. Now there's no 'Error failed to fork pty' but now it cannot find /proc... strangely though, it is mounted.
**EDIT2**: Very strange... though 'mount' said /proc was mounted, it wasn't. I just mounted it now. Tried to reinstall libc6 but I got that error again:
```
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```**EDIT3**: When trying to reinstall grub-pc I get:
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I'm starting to give up, though it would be painful to loss all of the preferences saved for applications, all of the applications installed, etc...
**EDIT4**: I just have reinstalled Ubuntu with backuping all of my files (with hidden files too, so I could restore some program settings)

---

