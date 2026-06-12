---
title: "Cannot find /proc/version when installing 32-bit deb in chroot on 64-bit OS"
date: 2012-02-07
forum: General Help
---

### Post by Kissell on 2012-02-07
I'm running Ubuntu 11.10 64-bit, but I have a 32-bit only .deb file.  So I tried to run 32-bit OS files inside of 64-bit using chroot.

But everytime I try to install the deb file inside chroot, I get an error.
root:/# dpkg -i boxee*.deb

> 
Selecting previously deselected package boxee.
(Reading database ... 53133 files and directories currently installed.)
Unpacking boxee (from boxee-1.5.0.23596-2bcda77.i486.deb) ...
Setting up boxee (1.5.0.23596-2bcda77) ...
Cannot find /proc/version - is /proc mounted?


---

### Post by Kissell on 2012-02-07
This is what I did to setup the chroot environment.
> 
USER1="me"
sudo apt-get install -y debootstrap
sudo mkdir /home/$USER1/.boxee-installer -p
sudo debootstrap --variant=minbase --arch i386 oneiric /home/$USER1/.boxee-installer [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
cp /home/kissell/Dropbox/Linux/Programs/boxee/boxee-1.5.0.23596-2bcda77.i486.deb /home/kissell/.boxee-installer
cd /home/$USER1/.boxee-installer

mkdir /home/kissell/.boxee-installer/etc/.root -p
mkdir /home/kissell/.boxee-installer/etc -p
mkdir /home/kissell/.boxee-installer/var/lib/locales/supported.d -p
cp -f /etc/passwd /home/kissell/.boxee-installer/etc/
cp -f /etc/shadow /home/kissell/.boxee-installer/etc/
cp -f /etc/group /home/kissell/.boxee-installer/etc/
cp -f /etc/sudoers /home/kissell/.boxee-installer/etc/
cp -f /etc/hosts /home/kissell/.boxee-installer/etc/
cp -f /etc/apt/sources.list /home/kissell/.boxee-installer/etc/apt
cp /var/lib/locales/supported.d/* /home/kissell/.boxee-installer/var/lib/locales/supported.d/

echo "##chroot
/home /home/kissell/.boxee-installer/home none rbind 0 0
/dev /home/kissell/.boxee-installer/dev none rbind 0 0
/etc /home/kissell/.boxee-installer/etc/.root none bind 0 0
/proc /home/kissell/.boxee-installer/proc none rbind 0 0
/media /home/kissell/.boxee-installer/media none rbind 0 0
/mnt /home/kissell/.boxee-installer/mnt none rbind 0 0
/tmp /home/kissell/.boxee-installer/tmp none rbind 0 0" >> /home/kissell/.boxee-installer/etc/fstab
sudo mount -a

sudo chroot /home/kissell/.boxee-installer
sudo chmod +x boxee-1.5.0.23596-2bcda77.i486.deb
sudo dpkg-reconfigure locales

apt-get install -y acpid adduser apt apt-utils apt-xapian-index aptitude avahi-daemon base-files base-passwd bash bash-completion bind9-host binutils bsdutils build-essential busybox-initramfs bzip2 ca-certificates consolekit coreutils cpio cpp cpp-4.6 cron dash dbus dbus-x11 debconf debconf-i18n debianutils defoma diffutils dkms dmsetup dpkg dpkg-dev e2fslibs e2fsprogs eject fakeroot file findutils fontconfig fontconfig-config freeglut3 freeglut3-dev g++ g++-4.6 gcc gcc-4.6 gcc-4.6-base gir1.2-glib-2.0 gnupg gpgv grep grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common gstreamer0.10-pulseaudio gzip hdparm hicolor-icon-theme hostname ifupdown initramfs-tools initramfs-tools-bin initscripts insserv iproute iputils-ping isc-dhcp-client isc-dhcp-common iso-codes kbd keyboard-configuration klibc-utils less libacl1 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-inst1.3 libapt-pkg4.11 libasound2 libasound2-plugins libasyncns0 libatk1.0-0 libatk1.0-data libattr1 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libbind9-60 libblkid1 libboost-iostreams1.46.1 libbsd-dev libbsd0 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libcairo2 libcap2 libck-connector0 libclass-accessor-perl libclass-isa-perl libcomerr2 libcups2 libcurl3 libcurl3-gnutls libcwidget3 libdaemon0 libdatrie1 libdb4.8 libdb5.1 libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1 libdns69 libdpkg-perl libdrm-dev libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libenca0 libept1 libexpat1 libffi-dev libffi6 libflac8 libfontconfig1 libfontenc1 libfreetype6 libfribidi0 libfuse2 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0 libgeoip1 libgirepository-1.0-1 libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglew1.5 libglib2.0-0 libglu1-mesa libglu1-mesa-dev libgmp-dev libgmp10 libgmpxx4ldbl libgnutls26 libgomp1 libgpg-error0 libgpm2 libgssapi-krb5-2 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libice-dev libice6 libidn11 libio-string-perl libisc62 libisccc60 libisccfg62 libjack-jackd2-0 libjasper1 libjpeg62 libjson0 libk5crypto3 libkeyutils1 libklibc libkms1 libkrb5-3 libkrb5support0 libldap-2.4-2 libllvm2.9 liblocale-gettext-perl liblockfile1 libltdl7 liblwres60 liblzma2 liblzo2-2 libmad0 libmagic1 libmount1 libmpc2 libmpfr4 libmysqlclient16 libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1 libnspr4 libnss-mdns libnss3 libnss3-1d libogg0 libpam-ck-connector libpam-modules libpam-modules-bin libpam-runtime libpam0g libpango1.0-0 libparse-debianchangelog-perl libpci3 libpciaccess0 libpcre3 libpixman-1-0 libplymouth2 libpng12-0 libpod-plainer-perl libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpopt0 libpthread-stubs0 libpthread-stubs0-dev libpulse0 libpython2.7 libquadmath0 libreadline6 librtmp0 libsamplerate0 libsasl2-2 libsasl2-modules libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsigc++-2.0-0c2a libslang2 libsm-dev libsm6 libsmbclient libsndfile1 libspeexdsp1 libsqlite3-0 libss2 libssl1.0.0 libstdc++6 libstdc++6-4.6-dev libsub-name-perl libswitch-perl libtalloc2 libtasn1-3 libtdb1 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtiff4 libtimedate-perl libtinfo5 libudev0 libusb-0.1-4 libusb-1.0-0 libutempter0 libuuid1 libvdpau1 libvorbis0a libvorbisenc2 libvorbisfile3 libwbclient0 libwrap0 libx11-6 libx11-data libx11-dev libx11-xcb1 libx86-1 libxapian22 libxau-dev libxau6 libxaw7 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxext-dev libxext6 libxfixes3 libxfont1 libxft2 libxi-dev libxi6 libxinerama1 libxkbfile1 libxml2 libxmu-dev libxmu-headers libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxt-dev libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 linux-firmware linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic linux-headers-generic linux-image linux-image-3.0.0-12-generic linux-image-generic linux-libc-dev locales lockfile-progs login logrotate lsb-base lsb-release make makedev manpages manpages-dev mawk mesa-common-dev mime-support module-init-tools mount mountall multiarch-support mysql-common ncurses-base ncurses-bin net-tools netbase netcat-openbsd ntpdate openssl os-prober passwd patch pciutils perl perl-base perl-modules pkg-config plymouth pm-utils policykit-1 policykit-desktop-privileges powermgmt-base procps pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils python python-apt python-apt-common python-cairo python-central python-chardet python-debian python-gnupginterface python-gobject python-gobject-2 python-gobject-cairo python-gtk2 python-minimal python-software-properties python-xapian python-xkit python2.7 python2.7-minimal readline-common rsyslog rtkit screen-resolution-extra sed sensible-utils sgml-base shared-mime-info sudo sysv-rc sysvinit-utils tar tcpd ttf-dejavu-core tzdata ubuntu-keyring ubuntu-minimal ucf udev unattended-upgrades upstart ureadahead usbutils util-linux vbetool vim vim-common vim-runtime vim-tiny wget whiptail wireless-crda x-ttcidfont-conf x11-common x11-utils x11-xkb-utils x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xauth xbitmaps xfonts-base xfonts-encodings xfonts-utils xkb-data xml-core xorg-sgml-doctools xserver-common xserver-xorg-core xterm xtrans-dev xz-utils zlib1g zlib1g-dev zsh

sudo wget [http://mirror.pnl.gov/ubuntu//pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.10-2.1_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.10-2.1_i386.deb)
sudo wget [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-downloader_11.1.102.55ubuntu0.11.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-downloader_11.1.102.55ubuntu0.11.10.1_i386.deb)
sudo wget [http://mirror.pnl.gov/ubuntu//pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu3_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu3_i386.deb)
sudo wget [http://mirror.pnl.gov/ubuntu//pool/universe/libm/libmms/libmms0_0.6.2-2_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/libm/libmms/libmms0_0.6.2-2_i386.deb)
sudo wget [http://mirror.pnl.gov/ubuntu//pool/universe/h/hal/libhal-storage1_0.5.14-6_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/h/hal/libhal-storage1_0.5.14-6_i386.deb)
sudo wget [http://mirror.pnl.gov/ubuntu//pool/universe/h/hal/libhal1_0.5.14-6_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/h/hal/libhal1_0.5.14-6_i386.deb)
sudo dpkg -i *_i386.deb
sudo dpkg -i boxee-1.5.0.23596-2bcda77.i486.deb



---

