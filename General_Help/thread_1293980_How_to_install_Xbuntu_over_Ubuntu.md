---
title: "How to install Xbuntu over Ubuntu?"
date: 2009-10-17
forum: General Help
---

### Post by AgentY on 2009-10-17
I have an installation of Ubunto 9.04, but would like to chnage to the Xbuntu release instead for various reasons but WITHOUT losing data held on the Ubuntu file system.

I've searched about and found the following command, which will apparently do this. Can someone confirm that the following command  will actually produce the result I am after; (It looks feasible, but I am fairly new to ubuntu and would like confirmation on scripts/commands that I am advised to run).

> sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktopIf this does work, would any graphic card drivers I have installed be reverted back to the original driver set? (I am using older drivers from release 8.xx)

Ideally I would like to install Xbuntu without formatting and installing from scratch. Any productive feedback is welcome!

---

### Post by mechro on 2009-10-17
Install **xubuntu-desktop** from synaptic. When you reboot and log-in choose the xfce session. You'll still have gnome session available if you want it.

As far as I know your graphic drivers will remain the same but I don't think xfce gives you all the compizy spinning cubey eye candy.

---

### Post by winotree on 2009-10-17
> ....I've searched about and found the following command, which will apparently do this. Can someone confirm that the following command will actually produce the result I am after; (It looks feasible, but I am fairly new to ubuntu and would like confirmation on scripts/commands that I am advised to run).... The command will do what it purports to do -- I've used it before -- however I can not say anything about drivers.  Not a lot of help, I know, but you do seem to be getting your questions answered in bits and pieces.  ;)

---

### Post by wojox on 2009-10-17
If you found that at [psychocats]("http://www.psychocats.net/ubuntu/index.php") website, I concur it works.

---

