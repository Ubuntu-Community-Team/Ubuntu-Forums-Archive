---
title: "Urgent help needed for gcc-4.0-base issue!!!"
date: 2006-03-20
forum: General Help
---

### Post by Svip on 2006-03-20
It seems I have somehow installed a version of gcc-4.0-base that does not work with some packages on Ubuntu - this means that my entire system has basically failed.

And I cannot get this file installed because it complains that it is already the newest version - and it annoys extremely much!

How do I get my old and correct version back?  And I need help soon - as my applications currently only work by running in the RAM.

---

### Post by bravobritto on 2006-03-20
Hi Svip

Here's one example of how overflow can be detected via x86-32/64 inline
assembly: [http://article.gmane.org/gmane.comp.gcc.help/10677]("http://article.gmane.org/gmane.comp.gcc.help/10677") Is your machine AMD ? 

Regards,
Britto     :rolleyes:

---

### Post by claes on 2006-03-20
You can reinstall the version you already have with:

sudo aptitude reinstall *program*

Claes

---

### Post by Svip on 2006-03-20
I tried your proposal:

```
$ sudo aptitude reinstall gcc-4.0-base
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages will be REINSTALLED:
  gcc-4.0-base
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the gcc-4.0-base package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
```

It seems to need 0B of archives - which will expand to 0B when unpacked.  I assume this could be a problem.

I also tried *apt-get install --reinstall*:
```
$ sudo apt-get install --reinstall gcc-4.0-base
Reading package lists... Done
Building dependency tree... Done
Reinstallation of gcc-4.0-base is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Should be noted that I found gcc-4.0-base using *apt-cache search gcc-4.0*

:(

**EDIT:** No I do not use an AMD CPU, I am on a simple Intel Mobile unit thingie - i386.  It is a laptop.

---

### Post by Ramses de Norre on 2006-03-20
The first thing doesn't really sound unlogical to me, the .deb is probably still stored in the apt archive and the reinstall shouldn't grow larger then the previous install.

For the second: I have got this kind of things when I didn't ran sudo apt-get update every now and then. Are you able do download other packages?

---

### Post by Svip on 2006-03-20
[QUOTE=Ramses de Norre]The first thing doesn't really sound unlogical to me, the .deb is probably still stored in the apt archive and the reinstall shouldn't grow larger then the previous install.

For the second: I have got this kind of things when I didn't ran sudo apt-get update every now and then. Are you able do download other packages?[/QUOTE]
I just did a clean *apt-get update* (that means an update without errors).  Tried again and same result.

I think I am not able to install anything as all packages in some way lead to the problem of the gcc-4.0-base package, if this one is not fixed - none will install, and my system is rendered utterly "helpless".  But then again, I have no idea what package to test.  All the others just return depencies errors.

---

### Post by claes on 2006-03-20
Check in /var/cache/apt/archives/

Do you have the gcc-4.0-base deb there. Then try and install it from there.
sudo dpkg -i gcc-4.0-base......

If that don't work. Try sudo aptitude clean and then sudo aptitude reinstall again.

Claes

---

### Post by Svip on 2006-03-20
Okay, I went here:
[http://archive.ubuntu.com/ubuntu/pool/]("http://archive.ubuntu.com/ubuntu/pool/")

And found the 4.0.1-4ubuntu9 version.  Which I used to have - I assumed at least.

But two other packages are now complaining. :<

```
The following packages have unmet dependencies:
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.3-1ubuntu2 is installed.  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.3-1ubuntu2 is installed.
```

**Edit:** Another thing, when I try to install ubuntu-desktop (which I have somehow removed), it replies with all it depends on - I thought it would automaticly install the things it depended on.

Would it not?

---

### Post by claes on 2006-03-20
Not if you have a deb from debian or anything like that, that are newer then the deb in ubuntu.

Claes

---

### Post by Svip on 2006-03-20
[QUOTE=claes]Not if you have a deb from debian or anything like that, that are newer then the deb in ubuntu.

Claes[/QUOTE]
Exactly what I did wrong - I realise now I have versions of libgcc1 and libstdc++6 in deb files from Debian.  Anyway to get those files back from the Ubuntu repos?

---

### Post by claes on 2006-03-20
First check that you don't have any debian deb sources in your /etc/apt/source.list

Then try to reinstall libgcc1 and libtdc++ from the ubuntu sources.

Claes

---

### Post by Svip on 2006-03-20
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main
restricted
#deb cdrom:/ breezy main restricted

deb http://dk.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb ftp://dk.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src ftp://dk.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb-src http://security.ubuntu.com/ubuntu breezy-security restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

#deb http://soulmachine.net/breezy unstable/

#deb ftp://ftp.nerim.net/debian-marillat/ sarge main
#deb ftp://ftp.nerim.net/debian-marillat etch main
#deb ftp://ftp.nerim.net/debian-marillat sid main
```
This is my /etc/apt/sources.list

```
$ sudo apt-get install --reinstall libgcc1 libstdc++6
Reading package lists... Done
Building dependency tree... Done
Reinstallation of libgcc1 is not possible, it cannot be downloaded.
Reinstallation of libstdc++6 is not possible, it cannot be downloaded.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is to be installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
$ sudo aptitude reinstall libgcc1 libstdc++6
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is installed.
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is installed.
```

If I install the other version of *gcc-4.0-base*, *cpp-4.0* complains, and I don't have cpp-4.0 from Debian.org.

When I try to remove them, they complain about packages depending on them (which seems logical).

---

### Post by Ramses de Norre on 2006-03-20
Can you run this: ```
sudo apt-get update && sudo apt-get -f install
```

---

### Post by claes on 2006-03-20
What does:
dpkg --get-selections | grep hold

Gives you?

Claes

---

### Post by Svip on 2006-03-20
@R de N:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acpi-support apache2 apache2-common apache2-mpm-prefork apt apt-utils
  aptitude aspell aspell-en audacity base-config bluez-cups cedega cupsys
  cupsys-driver-gimpprint cupsys-driver-gimpprint-data dia-libs dselect
  dvd+rw-tools fluxbox foomatic-db-gimp-print foomatic-db-hpijs freeciv
  freeciv-client-gtk freeglut3 gaim gcc-3.4 gksu gpsd groff-base gs-common
  gs-esp hpijs hplip-base hplip-data html2text ijsgimpprint inkscape
  language-selector language-support-en lftp libapache2-mod-php5 libaspell15
  libavcodeccvs libavutilcvs0 libdjvulibre15 libenchant1c2 libfaac0 libgc1c2
  libgcc1 libgksu1.2-0 libgksuui1.0-0 libgl1-mesa libgl1-mesa-dev
  libgl1-mesa-dri libgle3 libglibmm-2.4-1c2 libglu1-mesa libglu1-mesa-dev
  libglut3 libgtkmm-2.4-1c2 libgtkspell0 libid3-3.8.3c2 libmodplug0c2
  libmp4v2-0 libmusicbrainz2c2 libmusicbrainz4c2 libmyspell3c2 libopenal0
  libopenh323-1.15.3c2 libpoppler0c2 libpoppler0c2-glib libpt-1.8.3c2
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqt3-mt
  libsdl-mixer1.2 libsigc++-1.2-5c2 libsigc++-2.0-0c2 libsmpeg0c2 libstdc++5
  libstdc++6 libstlport4.6c2 libwpd8c2 libwvstreams4.0c2-base
  libwvstreams4.0c2-extras libwxgtk2.4-1 libxine1c2 libxplc0.3.11c2 lshw
  man-db menu mesa-utils mozilla-firefox-locale-en-gb mplayer-586 mplayer-686
  mysql-client mysql-server notification-daemon nvidia-glx
  openoffice.org2-l10n-en-us php5 php5-mysql phpmyadmin pnm2ppa
  powermanagement-interface python-apt python-musicbrainz python2.4-apt
  python2.4-musicbrainz rar rss-glx scorched3d scribus supertux synaptic
  telnet toshset ubuntu-minimal ubuntu-standard unrar-nonfree w3m wvdial
  xbase-clients xdriinfo xgl xine-ui xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-driver-apm xserver-xorg-driver-ark
  xserver-xorg-driver-ati xserver-xorg-driver-chips xserver-xorg-driver-cirrus
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glide
  xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740
  xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport
  xserver-xorg-driver-nsc xserver-xorg-driver-nv xserver-xorg-driver-rendition
  xserver-xorg-driver-s3 xserver-xorg-driver-s3virge
  xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion
  xserver-xorg-driver-sis xserver-xorg-driver-tdfx xserver-xorg-driver-tga
  xserver-xorg-driver-trident xserver-xorg-driver-tseng
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad
  xserver-xorg-input-aiptek xserver-xorg-input-calcomp
  xserver-xorg-input-citron xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro
  xserver-xorg-input-elographics xserver-xorg-input-fpit
  xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xvncviewer yudit
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libgcc1 (due to apt) libstdc++6 (due to apt)
0 upgraded, 0 newly installed, 189 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 515MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] n
```

@claes: None at all.

---

### Post by claes on 2006-03-20
Have you run:
sudo aptitude clean 
sudo aptitude update
sudo aptitude install gcc or sudo aptitude reinstall gcc

Claes

---

### Post by Svip on 2006-03-20
¬¬ gcc was not installed.  (since it was removed due to an -f install before this topic)

So I tried to install it, it depends on gcc-4.0, which depends on libgcc1, which depends on the wrong version of gcc-4.0-base.  Thus making libgcc1 the wrong version of that package. :(

---

### Post by claes on 2006-03-20
And this:

apt-cache policy gcc-4.0-base

Claes

---

### Post by Svip on 2006-03-20
Output (with libgcc1 and libstdc++6 added):
```
$ sudo apt-cache policy gcc-4.0-base libgcc1 libstdc++6
gcc-4.0-base:
  Installed: 4.0.1-4ubuntu9
  Candidate: 4.0.1-4ubuntu9
  Version table:
 *** 4.0.1-4ubuntu9 0
        500 http://dk.archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status
libgcc1:
  Installed: 1:4.0.3-1
  Candidate: 1:4.0.3-1
  Version table:
 *** 1:4.0.3-1 0
        100 /var/lib/dpkg/status
     1:4.0.1-4ubuntu9 0
        500 http://dk.archive.ubuntu.com breezy/main Packages
libstdc++6:
  Installed: 4.0.3-1
  Candidate: 4.0.3-1
  Version table:
 *** 4.0.3-1 0
        100 /var/lib/dpkg/status
     4.0.1-4ubuntu9 0
        500 http://dk.archive.ubuntu.com breezy/main Packages
```

---

### Post by claes on 2006-03-20
Do you notice the problem?

libgcc1:
Installed: 1:4.0.3-1
But the ubuntu version is 1:4.0.1-4ubuntu9

libstdc++6:
Installed: 4.0.3-1
But the ubuntu version is 4.0.1-4ubuntu9

So you have to install the ubuntu version of these debs.

Try:
sudo aptitude reinstall libstdc++6 libgcc1

Claes

---

### Post by Svip on 2006-03-20
!!!

Yes!  I finally managed to get my system to work again!  I found packages.ubuntu.com, where all the versions of the packages I had wrong could be found.  Thus I installed them, and now everything works again.

I thank you very much for all the help you tried, claes.  But it seems I was able to do it myself.  I just had to look the right places.

Remember this next time, kids. ;)

---

### Post by claes on 2006-03-20
Glad it works for you.

Claes

---

