---
title: "remove unnecessary packages to the minimum"
date: 2009-09-06
forum: General Help
---

### Post by lb02f962 on 2009-09-06
Hello everybody!

**Goal of this thread**:
I'd like to have a really really minimalistic ubuntu system which is still able to install new packages from CD (see "rules"). 

First round is for a command line system only to keep things simple. In a second round this thread could be extended to create a really really minimalistic gnome installation "tutorial"...

[B]Why:
[/B]I'd like to give hints to the ubuntu maintainers (and everybody) about software being installed by default but rarely used by somebody. e.g. I don't think it is necessary to install "at" on every ubuntu system on the world although only 0.1% are really using it (and can install it with one line if they need).

**Note:**
This thread is not meant to be a tutorial to understand the core of linux. If you want that then I recommend [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
If you want a real mini-distribution have a look at [www.puppylinux.org/]("http://ubuntuforums.org/www.puppylinux.org/") or [www.damnsmalllinux.org]("http://ubuntuforums.org/www.damnsmalllinux.org")
If you want to help improve ubuntu please read on carefully :)

**Rules:**
At least one shell and apt-get must remain (or shall I better say dpkg?)
Removing packages which lead to the waring message "removing this package might render this system unusable" is not allowed.

**Start:**
Start is a ubuntu 9.04 alternate - "minimal command line system" installation.

Here is my **first attempt**. After the installation I issue:
```
sudo apt-get remove aptitude rsync command-not-found command-not-found-data apparmor ufw iptables at bind9-host memtest86+ w3m
sudo apt-get clean
```All these default packages can be removed and the system is still fully usable.

Is there anybody able to remove more?
lorenz

---

### Post by lb02f962 on 2009-09-17
Here is my next attempt:

```
sudo apt-get remove aptitude tasksel apparmor rsync command-not-found-data ufw at bind9-host libbind9 memtest86+ w3m language-pack-en binutils-static bash-completition python update-manager-core update-motd openssh-client

```

can anyone beat that?

lorenz

---

### Post by earthpigg on 2009-09-17
start with a command line install.

```
apt-get install --no-install-recommends xorg gdm openbox gnome-panel gnome-power-manager network-manager-gnome 
```

configure openbox to launch gnome panel at startup.

configure gnome's power manager and network manager to run outside of gnome.

done.

---

### Post by ubongo2008 on 2009-09-17
Has allready been done:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Edit: actually i used that one for my current install of an minimal xfce-ubuntu
Edit: You'll have to beat: > Downloading packages at install time reduces the size of the install CD to approximately 5 to 20MB depending on architecture  

---

### Post by lb02f962 on 2009-09-17
> **earthpigg said:**
> 
```
apt-get install --no-install-recommends xorg gdm openbox gnome-panel gnome-power-manager network-manager-gnome 
```

Nice idea using openbox :-), anyway there have been [other threads]("http://ubuntuforums.org/showthread.php?t=1155961") on this topic. 

My idea is to *remove* as much as possible from the command-line installation, not to install as few as possible (sort of top-bottom, not bottom-top...). 

lorenz

---

### Post by lb02f962 on 2009-09-17
> **ubongo2008 said:**
> Has allready been done:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Edit: actually i used that one for my current install of an minimal xfce-ubuntu
Edit: You'll have to beat:

The mini.iso is just a minimal *installer* but using it will install the same system as an ubuntu alternate "minimal" installation. No?

lorenz

---

### Post by earthpigg on 2009-09-18
> **lb02f962 said:**
> The mini.iso is just a minimal *installer* but using it will install the same system as an ubuntu alternate "minimal" installation. No?

lorenz

the mini.iso will accomplish the same as the alternate installer's 'command line install' option, but mini.iso will download the packages on-the-fly when you install, whereas alternate cd will install them from the CD. hence the 10mb size of mini.iso.

mini.iso will thus also get you the latest packages without you needing to apt-get update && apt-get upgrade.

right now, it has been 5 months since 9.04 was released... that means 5 months of updates you will have to catch up on if you use the alternate installer cd.

---

### Post by lb02f962 on 2009-09-18
> **earthpigg said:**
> the mini.iso will accomplish the same as the alternate installer's 'command line install' option

right now, it has been 5 months since 9.04 was released... that means 5 months of updates you will have to catch up on if you use the alternate installer cd.

Perhaps I need to clarify this: I do not need a minimal *installer*, I want a minimal *installation.* A fully functional system on my hard drive. Fully functional I define above as "a shell and apt-get".
So I install a "command line system" with whatever installer and try to remove as much packages as possible from there.

---

### Post by wojox on 2009-09-18
So download the mini.iso it installs command line and apt. Then you add what ever you want as far as tools, utlities, whatever. If you get bored with that install a window manager and then maybe a desktop.

---

### Post by lb02f962 on 2009-09-18
> **wojox said:**
> So download the mini.iso it installs command line and apt. Then you add what ever you want as far as tools, utlities, whatever. If you get bored with that install a window manager and then maybe a desktop.

My idea here is to *remove* stuff before adding anything. For example the package "bind9-host" is installed on every ubuntu machine worldwide, even with a minimal install, and I claim 99% of all users do not need it. So my question is how many packages are there which are installed by default but are not necessary for the system to run. So far I found 18 packages for a CLI system (see post above).
Are there more?

lorenz

---

### Post by earthpigg on 2009-09-18
ah, ***now*** i see what you are trying to do.

maybe do a command line *debian* install and see what *debian* thinks the minimum packages are, and then try removing the extra ones Ubuntu has?

---

### Post by lb02f962 on 2009-09-19
> **earthpigg said:**
> 
maybe do a command line *debian* install and see what *debian* thinks the minimum packages are, and then try removing the extra ones Ubuntu has?

Smart idea, thanks a lot! Quickly installed a debian5 netinst, then issued
```
dpkg --get-selection
```on debian and ubuntu and removed the duplicates. 157 packages were left over in the list:
```
apparmor apparmor-utils apt-transport-https at bash-completion bind9-host binutils-static busybox-initramfs bzip2 ca-certificates command-not-found-data command-not-found console-setup console-terminus cpp-4.3 cpp dash dmsetup dnsutils dosfstools file friendly-recovery ftp fuse-utils hdparm iputils-arping iputils-tracepath iso-codes kbd klogd language-pack-en-base language-pack-en less libapparmor1 libapparmor-perl libatm1 libbind9-40 libcap2 libclass-accessor-perl libcompress-raw-zlib-perl libcompress-zlib-perl libcurl3-gnutls libdb4.7 libdns45 libelf1 libexpat1 libfont-afm-perl libfribidi0 libfuse2 libgc1c2 libgmp3c2 libgpm2 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidn11 libio-compress-base-perl libio-compress-zlib-perl libio-string-perl libisc45 libisccc40 libisccfg40 libldap-2.4-2 liblockfile1 liblwres40 libmagic1 libmailtools-perl libmpfr1ldbl libntfs-3g49 libparse-debianchangelog-perl libparted1.8-10 libpcap0.8 libpcre3 librpc-xml-perl libsasl2-modules libsqlite3-0 libterm-readkey-perl libtimedate-perl liburi-perl libvolume-id1 libwww-perl libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxml2 libxml-parser-perl libxmuu1 linux-firmware linux-generic linux-image-2.6.28-11-generic linux-image-generic linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-common linux-restricted-modules-generic lockfile-progs lsb-release lshw lsof ltrace memtest86+ mime-support mlocate mtr-tiny netcat ntfs-3g ntpdate openssl parted pciutils perl perl-modules popularity-contest pppconfig ppp pppoeconf psmisc python2.6 python2.6-minimal python-apt python-central python-gdbm python-gnupginterface python python-minimal python-support reiserfsprogs rsync sgml-base startup-tasks strace sudo sysklogd system-services tcpdump telnet time ubuntu-keyring ubuntu-minimal ubuntu-standard ucf ufw update-manager-core update-motd upstart-compat-sysv upstart upstart-logd uuid-runtime w3m wireless-crda x11-common xauth xkb-data xml-core 
```Now I have to sort out the elementary ones (linux-image, dash...). I'll write an update as soon as I know more...

lorenz

---

### Post by lb02f962 on 2009-09-27
I sorted the packages out. The following packages are (in my opinion) not necessary for a default command line install:
```

 apparmor apparmor-utils apt-transport-https at bind9-host binutils-static bzip2 command-not-found-data command-not-found dmsetup dnsutils dosfstools file friendly-recovery ftp hdparm iputils-arping iputils-tracepath iso-codes language-pack-en-base language-pack-en libapparmor1 libapparmor-perl libatm1 libbind9-40 libcap2 libclass-accessor-perl libcompress-raw-zlib-perl libcompress-zlib-perl libcurl3-gnutls libdb4.7 libdns45 libelf1 libexpat1 libfont-afm-perl libfribidi0 libfuse2 libgc1c2 libgmp3c2 libgpm2 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidn11 libio-compress-base-perl libio-compress-zlib-perl libio-string-perl libisc45 libisccc40 libisccfg40 libldap-2.4-2 liblockfile1 liblwres40 libmagic1 libmailtools-perl libmpfr1ldbl libntfs-3g49 libparse-debianchangelog-perl libparted1.8-10 libpcap0.8 libpcre3 librpc-xml-perl libsasl2-modules libsqlite3-0 libterm-readkey-perl libtimedate-perl liburi-perl libvolume-id1 libwww-perl libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxml2 libxml-parser-perl libxmuu1 lockfile-progs lsb-release lshw lsof ltrace memtest86+ mime-support mlocate mtr-tiny netcat ntpdate parted pciutils perl perl-modules popularity-contest pppconfig ppp pppoeconf psmisc python2.6 python2.6-minimal python-apt python-central python-gdbm python-gnupginterface python-support rsync sgml-base strace tcpdump telnet time ucf ufw update-manager-core update-motd w3m wireless-crda x11-common xauth xml-core

```

I posted a new idea on ubuntu brainstorm to shrink the default installation. Please help me to come through with it:
[http://brainstorm.ubuntu.com/idea/21519/](http://brainstorm.ubuntu.com/idea/21519/)

lorenz

---

### Post by credobyte on 2009-09-27
What's the point of removing everything to the minimum, if you can install just the minimum and don't remove anything ( MinimalCD ) ?

---

### Post by lb02f962 on 2009-09-29
> **credobyte said:**
> What's the point of removing everything to the minimum, if you can install just the minimum and don't remove anything ( MinimalCD ) ?

This would be greate but the very minimal CD mini.iso is just an *installer*. You cannot install a running system with that (or can you?!?)
The ubuntu alternate command line installation is already not minimal any more, so I'd like to shrink that.

lorenz

---

### Post by credobyte on 2009-09-30
> **lb02f962 said:**
> This would be greate but the very minimal CD mini.iso is just an *installer*. You cannot install a running system with that (or can you?!?)
The ubuntu alternate command line installation is already not minimal any more, so I'd like to shrink that.

lorenz

No, you'll get a basic command line system ( Ubuntu of course ), tough, you can start installing whatever you need right after finishing installation.


Ubuntu Gnome - Minimal ( login manager + gnome DE ):
```
sudo apt-get install xorg gdm gnome-core xterm
```

---

### Post by lb02f962 on 2009-09-30
> **credobyte said:**
> No, you'll get a basic command line system ( Ubuntu of course ), tough, you can start installing whatever you need right after finishing installation.

I am not sure if we are at cross-purposes...
I think if you do an installation with the mini.iso you'll get the same as with the alternate CD and a CLI-system installation, except the stuff will be downloaded from the net instead from the CD. This is ~400MB and already too large for me.
Or: Did you manage to get a** full system** installation with the mini.iso **and no internet connection**? Can you tell me how you did that and how much hard disk this uses? 

lorenz

---

### Post by Jack005 on 2009-10-06
Thanks for the guide! I was looking for this to install a minimal system and then a window manager. The goal is to install vmware workstation on top (workstation require gui) and then I can install different guest os for testing purposes.

---

### Post by anonymous_user on 2009-10-07
@lb02f962 - Would you consider it safe to remove "essential packages"?
```
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  base-files libpam-modules (due to base-files) bash e2fsprogs libblkid1 (due
  to e2fsprogs) libuuid1 (due to e2fsprogs) grep libpcre3 (due to grep) login
  mount libvolume-id1 (due to mount) python-minimal python2.6-minimal (due to
  python-minimal) util-linux
```

---

### Post by rippin on 2009-10-07
> **lb02f962 said:**
> This would be greate but the very minimal CD mini.iso is just an *installer*. You cannot install a running system with that (or can you?!?)
The ubuntu alternate command line installation is already not minimal any more, so I'd like to shrink that.

lorenz

You're wanting to go about it backwards. Why remove after adding when not installing at first is sensible? Abandon the MS mentality. Plus, don't box yourself in with it being only an "alt"  CD. A mini-installer is intended to make a miniature install  (A.K.A. a small system with few files and little 'cruft').

This thread is more about a 'straw man' and chatter than reality, IMO. What's the system specs for such a demand? A Gameboy?

Here. This beats your 400MB barrier:
**Absolute minimum requirements**
 
[LIST]
[*]Intel 486 processor
[*]32 MB of system memory (RAM)
[*]300 MB of disk space
[/LIST]
I just mini'ed a system, choosing no pre-configured desktop/server, and had but a 154 packages installed, with 28 processes only running, in a CLI-only environment. Can't see it being trimmer and still maintaining eth0. Otherwise, maybe you'll want to look into Gentoo, LFS or Arch. Better yet, if you're at all genuine, install DSL ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)).

I doubt you'll see much value-to-time-spent ratio trimming an ATX tower down to a system only intended for embedded devices. If you can build a better system yourself than Ubuntu's mini-CD with 154 packages, 28 processes while logged in, with eth0, plus a fully functioning CLI-OS, more power to you. Maybe you should be working at DSL's shop. But, given your proclivity to argue any suggestion, no doubt you will find these instructions unacceptable.

---

### Post by lb02f962 on 2009-10-09
> **anonymous_user said:**
> @lb02f962 - Would you consider it safe to remove "essential packages"?


No.
One one hand there are only few packages marked as "very essential" and even I see that they are absolutely necessary (e.g. mount, bash).
On the other hand someone (human) set them like this, so at least someone is aware of these packages. I rather target to highlight the "forgotten bloat" :)

Or do you think that one of the packages you mentioned are not really necessary?

lorenz

---

### Post by lb02f962 on 2009-10-09
> **rippin said:**
> You're wanting to go about it backwards. Why remove after adding when not installing at first is sensible?

For me even the most basic ubuntu installation I can do is not really basic, it contains many packages I don't consider essential. This is the reason why I start with removing packages after the installation procedure. That is (I totally agree) really stupid and the reason I created this thread.

> **rippin said:**
> 
This thread is more about a 'straw man' and chatter than reality, IMO. 

Every sucessful story started with an idea and some discussion before it went real, IMO.

> **rippin said:**
> 
I just mini'ed a system, choosing no pre-configured desktop/server, and had but a 154 packages installed, with 28 processes only running, in a CLI-only environment. Can't see it being trimmer and still maintaining eth0.

This sound **great**! Please tell me more detailed how you did that.

> **rippin said:**
> 
I doubt you'll see much value-to-time-spent ratio trimming an ATX tower down to a system only intended for embedded devices.

No this is not the point, otherwise I would already be with DSL. I just want to remove some bloat from ubuntu. I'll update the original post to make things more clear.

> **rippin said:**
> But, given your proclivity to argue any suggestion, no doubt you will find these instructions unacceptable.
:confused:

lorenz

---

### Post by anonymous_user on 2009-10-09
> **lb02f962 said:**
> No.
One one hand there are only few packages marked as "very essential" and even I see that they are absolutely necessary (e.g. mount, bash).
On the other hand someone (human) set them like this, so at least someone is aware of these packages. I rather target to highlight the "forgotten bloat" :)

Or do you think that one of the packages you mentioned are not really necessary?

lorenz
Im asking because I ran one of the commands you posted, and apt-get asked me about those "essential" packages.

---

### Post by lb02f962 on 2009-10-09
> **anonymous_user said:**
> Im asking because I ran one of the commands you posted, and apt-get asked me about those "essential" packages.

Oops this should not happen. Was it "binutils-static"?

lorenz

---

### Post by anonymous_user on 2009-10-09
I do not remember; I will check later.

---

### Post by cariboo on 2009-10-09
Just out of curiosity, have you tried the mini.iso in expert mode?

---

### Post by lb02f962 on 2009-10-10
> **cariboo907 said:**
> Just out of curiosity, have you tried the mini.iso in expert mode?

Just tried it out. The same 288 packages are installed, so no differece there. But what is highly interesting: If you choose install "targeted kernel for this system" instead of "generic kernel" it uses after installation 90MB HD less and the RAM usage **shrinks to 46MB** (instead of 150MB). I don't know if this is hardware specific but it makes me :shock:, :-o and :-k. Is this option also available for non-expert users?

lorenz

---

### Post by anonymous_user on 2009-10-13
> **lb02f962 said:**
> Oops this should not happen. Was it "binutils-static"?

lorenz
No but I discovered the following essential packages in your last list (Post #13):

libvolume-id1
libpcre3
libdb4.7

---

### Post by lb02f962 on 2009-10-15
> **anonymous_user said:**
> No but I discovered the following essential packages in your last list (Post #13):

libvolume-id1
libpcre3
libdb4.7

You are right, I messed something up. Sorry :oops: Anyway have a look at my next post!

lorenz

---

### Post by benj1 on 2009-10-15
replace most of the utilities with busybox, it should nearly everything you need outside of the kernel.

[http://www.busybox.net/downloads/BusyBox.html]("http://www.busybox.net/downloads/BusyBox.html")

---

### Post by lb02f962 on 2009-10-15
Hi all

I did an extremely dull job. I installed a CLI system and went through all packages step by step to see whether I can remove them or not.
```
for i in $(cat orig)
do
clear
echo "=================== $i ====================="
apt-get remove $i
done
```I managed to remove the following 201 packages and still had a working system :D (details see below):
```
apt-get remove acpid apparmor apparmor-utils aptitude apt-transport-https apt-utils at bash-completion bind9-host bsdmainutils bzip2 ca-certificates command-not-found-data command-not-found console-setup console-terminus cpp-4.3 cpp cron dhcp3-client dhcp3-common dmidecode dmsetup dnsutils dosfstools ed eject file friendly-recovery ftp fuse-utils gettext-base gnupg groff-base hdparm ifupdown info installation-report iproute iptables iputils-arping iputils-ping iputils-tracepath iso-codes kbd klogd language-pack-en-base language-pack-en laptop-detect less libapparmor1 libapparmor-perl libatm1 libbind9-40 libbz2-1.0 libc6-i686 libcap2 libclass-accessor-perl libcompress-raw-zlib-perl libcompress-zlib-perl libcurl3-gnutls libcwidget3 libdb4.6 libdevmapper1.02.1 libdns45 libedit2 libelf1 libept0 libexpat1 libfont-afm-perl libfribidi0 libfuse2 libgc1c2 libgcrypt11 libgdbm3 libgmp3c2 libgnutls26 libgpg-error0 libgpm2 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidn11 libio-compress-base-perl libio-compress-zlib-perl libio-string-perl libisc45 libisccc40 libisccfg40 libkeyutils1 libkrb53 libldap-2.4-2 liblockfile1 liblwres40 libmagic1 libmailtools-perl libmpfr1ldbl libncursesw5 libnewt0.52 libntfs-3g49 libparse-debianchangelog-perl libparted1.8-10 libpcap0.8 libpci3 libpopt0 libreadline5 librpc-xml-perl libsasl2-2 libsasl2-modules libsigc++-2.0-0c2a libsqlite3-0 libssl0.9.8 libsysfs2 libtasn1-3 libterm-readkey-perl libtimedate-perl liburi-perl libusb-0.1-4 libwww-perl libx11-6 libx11-data libxapian15 libxau6 libxcb1 libxdmcp6 libxext6 libxml2 libxml-parser-perl libxmuu1 locales lockfile-progs logrotate lsb-release lshw lsof ltrace makedev man-db manpages memtest86+ mime-support mlocate mtr-tiny nano netbase netcat netcat-traditional net-tools ntfs-3g ntpdate openssh-client openssl parted pciutils pcmciautils perl perl-modules popularity-contest pppconfig ppp pppoeconf psmisc python2.6 python-apt python-central python-gdbm python-gnupginterface python python-support readline-common reiserfsprogs rsync sgml-base startup-tasks strace sysklogd system-services tasksel-data tasksel tcpdump telnet time ubuntu-keyring ubuntu-minimal ubuntu-standard ufw update-manager-core update-motd upstart-logd usbutils uuid-runtime vim-common vim-tiny w3m wget whiptail x11-common xauth xkb-data xml-core 
```So what is more interesting is which 87 packages I left on my computer:
```
adduser apt base-files base-passwd bash binutils-static bsdutils busybox-initramfs coreutils cpio dash debconf-i18n debconf debianutils diff dpkg e2fslibs e2fsprogs findutils gcc-4.3-base gpgv grep grub-common grub gzip hostname initramfs-tools initscripts klibc-utils libacl1 libattr1 libblkid1 libc6 libcomerr2 libdb4.7 libgcc1 libklibc liblocale-gettext-perl libncurses5 libpam0g libpam-modules libpam-runtime libpcre3 libselinux1 libsepol1 libslang2 libss2 libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libuuid1 libvolume-id1 linux-firmware linux-generic linux-image-2.6.28-11-generic linux-image-generic linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-common linux-restricted-modules-generic login lsb-base lzma mawk mktemp module-init-tools mount ncurses-base ncurses-bin passwd perl-base procps python2.6-minimal python-minimal sed sudo sysvinit-utils sysv-rc tar tzdata ucf udev upstart-compat-sysv upstart util-linux wireless-crda zlib1g 
```To summarize in words: I didn't dare to touch "You are about to do something potentially harmful" packages, grub & kernel stuff. I had to keep upstart and to keep apt-get working you need gpgv. Such a system needs 337MB hard drive and ~36MB RAM.

Since many useful tools have been removed (especially network stuff) I don't think such a system is directly usuable but it shows in an impressive way that there is a lot installed even in the smallest ubuntu edition.

lorenz

---

### Post by dirtylobster on 2009-11-03
> **lb02f962 said:**
> Just tried it out. The same 288 packages are installed, so no differece there. But what is highly interesting: If you choose install "targeted kernel for this system" instead of "generic kernel" it uses after installation 90MB HD less and the RAM usage **shrinks to 46MB** (instead of 150MB). I don't know if this is hardware specific but it makes me :shock:, :-o and :-k. Is this option also available for non-expert users?

Did you find out whether or not this is available to non-expert users?

---

### Post by lb02f962 on 2009-11-09
> **dirtylobster said:**
> Did you find out whether or not this is available to non-expert users?

I have not yet found that option in the "normal" command line installer for that. I know that self compiled kernels can lead to lots of trouble. SuSE for example denies support for system with non-default kernels... So this is probably with reason that non-experts don't have easy access to this.
What would be nice is a is a separate tool that one could install after the installation for those people which want to. On their own risk of course.

lorenz

---

