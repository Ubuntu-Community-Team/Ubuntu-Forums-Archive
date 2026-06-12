---
title: "No candidate ver"
date: 2010-05-10
forum: General Help
---

### Post by theo.ew on 2010-05-10
I have a major problem with my ubuntu installation. Somehow, I'm not sure what I did, ubuntu will not start up anymore. It shows the bootup animation but will not go to the login screen. I booted up in the recovery mode, and ran dpkg: repair packages and I got this result:
----------------------------------------------------------------
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory

Reading Cache
Reading Package lists: Done
Reading State Information: Done
Reading State Information: Done
Reading State Information: Done
No candidate ver: libisc44
No candidate ver: readahead
No candidate ver: libdirectfb-1.0-0
No candidate ver: upstart-logd
No candidate ver: libparted1.8-10
No candidate ver: libflickrnet2.1.5-cil
No candidate ver: libicu38
No candidate ver: fast-user-switch-applet
No candidate ver: linux-restricted-modules-2.6.28-11-generic
No candidate ver: libnm-util0
No candidate ver: libwebkit-1.0-1
No candidate ver: libopal3.6.1
No candidate ver: libbind9-40
No candidate ver: linux-restricted-modules-common
No candidate ver: upstart-compat-sysv
No candidate ver: linux-restricted-modules-2.6.28-13-generic
No candidate ver: chromium-browser
No candidate ver: libisc45
No candidate ver: belocs-locales-bin
No candidate ver: libxcb-xlib0
No candidate ver: libpoppler4
No candidate ver: libpulsecore9
No candidate ver: libpulsecore5
No candidate ver: linux-image-2.6.28-15-generic
No candidate ver: libntfs-3g49
No candidate ver: libisccfg40
No candidate ver: libavahi-core5
No candidate ver: linux-restricted-modules-2.6.27-7-generic
No candidate ver: libparted1.8-9
No candidate ver: libmagickwand1
No candidate ver: libwvstreams4.4-base
No candidate ver: linux-image-2.6.28-14-generic
No candidate ver: libraw1394-8
No candidate ver: libdatrie0
No candidate ver: libboost-program-options1.35.0
No candidate ver: libgnomekbdui3
No candidate ver: libsgutils1
No candidate ver: libass1
No candidate ver: linux-restricted-modules-2.6.28-15-generic
No candidate ver: libindicate1
No candidate ver: libgnomekbd3
No candidate ver: system-services
No candidate ver: linux-image-2.6.28-13-generic
No candidate ver: libmagick10
No candidate ver: libcolamd-3.2.0
No candidate ver: desktop-effects-kde
No candidate ver: picasa
No candidate ver: libgnome-desktop-2-7
No candidate ver: libntfs-3g28
No candidate ver: libxklavier12
No candidate ver: libgpod3
No candidate ver: libmagickcore1
No candidate ver: libffado0
No candidate ver: libzephyr3
No candidate ver: libuniconf4.4
No candidate ver: libmbca0
No candidate ver: liblwres40
No candidate ver: hotkey-setup
No candidate ver: libkrb53
No candidate ver: ttf-bitstream-vera
No candidate ver: libee12-2
No candidate ver: libopal-2.2
No candidate ver: songbird
No candidate ver: plib1.8.4c2
No candidate ver: linux-image-2.6.27-7-generic
No candidate ver: libpoppler3
No candidate ver: google-chrome-unstable
No candidate ver: linux-image-2.6.28-11-generic
No candidate ver: linux-restricted-modules-2.6.28-14-generic
No candidate ver: simgear1.0.0
No candidate ver: libpoppler-glib3
No candidate ver: mono-common
No candidate ver: libx264-65
No candidate ver: libwvstreams4.4-extras
No candidate ver: libdns43
No candidate ver: libnm-glib0
No candidate ver: libpt2.6.1
No candidate ver: libisccc40
No candidate ver: libdns45
No candidate ver: libisc44
No candidate ver: readahead
No candidate ver: libdirectfb-1.0-0
No candidate ver: upstart-logd
No candidate ver: libparted1.8-10
No candidate ver: libflickrnet2.1.5-cil
No candidate ver: libicu38
No candidate ver: fast-user-switch-applet
No candidate ver: linux-restricted-modules-2.6.28-11-generic
No candidate ver: libnm-util0
No candidate ver: libwebkit-1.0-1
No candidate ver: libopal3.6.1
No candidate ver: libbind9-40
No candidate ver: linux-restricted-modules-common
No candidate ver: upstart-compat-sysv
No candidate ver: linux-restricted-modules-2.6.28-13-generic
No candidate ver: chromium-browser
No candidate ver: libisc45
No candidate ver: belocs-locales-bin
No candidate ver: libxcb-xlib0
No candidate ver: libpoppler4
No candidate ver: libpulsecore9
No candidate ver: lipulsecore5
No candidate ver: linux-image-2.6.28-15-generic
No candidate ver: libntfs-3g49
No candidate ver: libisccfg40
No candidate ver: libavahi-core5
No candidate ver: linux-restricted-modules-2.6.27-7-generic
No candidate ver: libparted1.8-9
No candidate ver: libmagickwand1
No candidate ver: linux-image-2.6.28-14-generic
No candidate ver: libraw1394-8
No candidate ver: libdatrie0
No candidate ver: libboost-program-options1.35.0
No candidate ver: libgnomekbdui3
No candidate ver: libsgutils1
No candidate ver: libass1
No candidate ver: linux-restricted-modules-2.6.28-15-generic
No candidate ver: libindicate1
No candidate ver: libgnomekbd3
No candidate ver: system-services
No candidate ver: linux-image-2.6.28-13-generic
No candidate ver: libmagick10
No candidate ver: libcolamd-3.2.0
No candidate ver: desktop-effects-kde
No candidate ver: picasa
No candidate ver: libgnome-desktop-2-7
No candidate ver: libntfs-3g28
No candidate ver: libxklavier12
No candidate ver: libgpod3
No candidate ver: libmagickcore1
No candidate ver: libffado0
No candidate ver: libzephyr3
No candidate ver: libuniconf4.4
No candidate ver: libmbca0
No candidate ver: liblwres40
No candidate ver: hotkey-setup
No candidate ver: libkrb53
No candidate ver: ttf-bitstream-vera
No candidate ver: libeel2-2
No candidate ver: libopal-2.2
No candidate ver: songbird
No candidate ver: plib1.8.4c2
No candidate ver: linux-image-2.6.27-7-generic
No candidate ver: libpoppler3
No candidate ver: google-chrome-unstable
No candidate ver: linux-image-2.6.28-11-generic
No candidate ver: linux-restricted-modules-2.6.28-14-generic
No candidate ver: simgear1.0.0
No candidate ver: libpoppler-glib3
No candidate ver: mono-common
No candidate ver: libx264-65
No candidate ver: libwvstreams4.4-extras
No candidate ver: libdns43
No candidate ver: libnm-glib0
No candidate ver: libpt2.6.1
No candidate ver: libisccc40
No candidate ver: libdns45

Your system is up-to-date

There are no upgrades available for your system. The upgrade will now be canceled. 

Do you want to start the upgrdae?

Continue [yN] 	Details [d]


------------------------------------------------------------

Also whenever I try to install a package I get a warning that there is  "no canditate ver". I am using Ubuntu 9.10. I thought about trying to upgrade to 10.04 and seeing if that will fix the problem but have yet to do so. 

I know that I could just reinstall Ubuntu, but the thing is, I have it dual booted with Windows Vista, and I can't risk erasing the Vista partition. 

HELP!

---

