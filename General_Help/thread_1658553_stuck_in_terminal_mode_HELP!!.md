---
title: "stuck in terminal mode HELP!!"
date: 2011-01-02
forum: General Help
---

### Post by zwobott80 on 2011-01-02
hello

I did rather a stupid thing
I've been using ubuntu for almost two years now, but I am rather a newbie, it is my first choice os, but don't really know much about programming etc.

today, when trying to fix some problems with openoffice (finally did it - recovery mode used to turn on), I did want to re-install Tor, which didn't want to work, so I did type in:

sudo apt-get remove tor*.*
and then.... I don't know what happened, but the system took its time for this operation, hence I decided to quickly reboot the computer; I knew something went wrong...
when turned the computer back on, I can only know access terminal mode and that's it!

I tried several possibilities, such as recovery mode or trying to upgrade the system, none worked for me...

---

### Post by nice_like_rice on 2011-01-02
This might not be much help, but apt-cache search tor*.* returns what looks like every single package available. You might have deleted all of your packages, including gnome, the desktop.

Be really, really careful when removing stuff with wildcards..

Reinstall gnome maybe.. at least your data won't be gone.

---

### Post by zwobott80 on 2011-01-02
all my data seems to be ok
I did check via: cd dir and was able to see full list of files available on my desktop

could you just tell me what command I should type in to reinstall gnome, thank you

---

### Post by nice_like_rice on 2011-01-02
Try

```
sudo apt-get install gnome gnome-desktop gdm
```

Then when it's installed try

```
startx
```

or

```
gdm
```

I can't remember whether it's gnome or gnome-desktop, but if you type that command in it should install whatever it needs :)

---

### Post by libssd on 2011-01-02
> **zwobott80 said:**
> all my data seems to be ok
I did check via: cd dir and was able to see full list of files available on my desktop

could you just tell me what command I should type in to reinstall gnome, thank you
Try this: sudo apt-get install --reinstall ubuntu-desktop

Assuming you are able to recover from your disaster, install **_[remastersys]("http://geekconnection.org/remastersys/")_** and make yourself an image restore disk. After 30 years of mucking about with computers, I cannot tell you how many times I have shot myself in the foot. The ability to restore your system to its state as of the last backup is priceless. And, the knowledge that you can do so is liberating, allowing you to experiment with things in the knowledge that if something goes irreparably wrong, you can be back in business in 15-20 minutes.

---

### Post by zwobott80 on 2011-01-02
well, thanks but it doesn't work

when I reboot the system, I am able to get to the mode where I am choosing user (window with list of users), then type in password, and.... the terminal opens up....

I have just done what you said could help, unfortunately....didn't help... ;(

---

### Post by NT4usB on 2011-01-02
yikes...
hmmm... wonder what would happen if you apt-get install tor*.*?
A simulation shows a bunch of unmet dependencies but may be a start.
Might start by trying to install gnome desktop or ubuntu desktop or something again, see if it gets you back to a GUI.
I'm guessing it will be a long, painful process to get your system back to where it was. If you have /home on a separate partition, reinstalling might be the easiest way.

I just simulated your command and got a list of a couple thousand packages removed.

Of concern are the following:```
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
9 upgraded, 0 newly installed, 938 to remove and 53 not upgraded.
Remv acpi-support [0.136.1]
Remv acpid [1.0.10-5ubuntu2.1]
Remv aisleriot [1:2.30.0-0ubuntu6]
Remv ubuntu-desktop [1.197]
Remv alacarte [0.13.1-0ubuntu1]
Remv alsa-base [1.0.22.1+dfsg-0ubuntu3]
Remv alsa-utils [1.0.22-0ubuntu5]
Remv amarok [2:2.3.0-0ubuntu4]
Remv ubuntu-standard [1.197]
Remv logrotate [3.7.8-4ubuntu2]
Remv anacron [2.3-13.1ubuntu11]
Remv mythweb [2:0.23.1+fixes25902-0ubuntu2]
Remv phpmyadmin [4:3.3.2-1]
Remv php5 [5.3.2-1ubuntu4.5]
Remv php5-mysql [5.3.2-1ubuntu4.5]
Remv php5-gd [5.3.2-1ubuntu4.5]
Remv php5-mcrypt [5.3.2-0ubuntu1]
Remv libapache2-mod-php5 [5.3.2-1ubuntu4.5]
Remv apache2-mpm-prefork [2.2.14-5ubuntu8.2]
Remv apache2.2-common [2.2.14-5ubuntu8.2]
Remv apache2.2-bin [2.2.14-5ubuntu8.2]
Remv apparmor-utils [2.5-0ubuntu3]
Remv apparmor [2.5-0ubuntu3]
Remv apport-hooks-medibuntu [1medibuntu1]
Remv apport-gtk [1.13.3-0ubuntu2]
Remv apport [1.13.3-0ubuntu2]
Remv apport-symptoms [0.9]
Remv apt-transport-https [0.7.25.3ubuntu9.3]
Remv software-center [2.0.7]
Remv aptdaemon [0.11+bzr345-0ubuntu4.1]
Remv ubufox [0.9~rc2-0ubuntu2.1]
Remv apturl [0.4.1ubuntu4]
Remv at [3.1.11-1ubuntu5]
Remv gnome-orca [2.30.2-0ubuntu1]
Remv python-pyatspi [1.30.1-0ubuntu1]
Remv at-spi [1.30.1-0ubuntu1]
Remv audacious [2.3-1ubuntu4]
Remv audacious-plugins [2.3-1ubuntu4]
Remv audacity [1.3.12-2]
Remv avahi-autoipd [0.6.25-1ubuntu6.1]
Remv avahi-utils [0.6.25-1ubuntu6.1]
Remv padevchooser [0.9.3-2ubuntu4]
Remv telepathy-salut [0.3.11-1]
Remv libnss-mdns [0.10-3ubuntu4]
Remv avahi-daemon [0.6.25-1ubuntu6.1]
Remv avidemux [1:2.5.2-0ubuntu3]
Remv avidemux-plugins-cli [1:2.5.2-0ubuntu3]
Remv avidemux-plugins-gtk [1:2.5.2-0ubuntu3]
Remv avidemux-plugins-common [1:2.5.2-0ubuntu3]
Remv gnome-nettool [2.30.0-0ubuntu1]
Remv dnsutils [1:9.7.0.dfsg.P1-1]
Remv bind9-host [1:9.7.0.dfsg.P1-1]
Remv binfmt-support [1.2.18]
Remv gnome-user-share [2.30.0-0ubuntu2]
Remv gnome-bluetooth [2.30.0-0ubuntu3]
Remv bluez [4.60-0ubuntu8]
Remv bluez-alsa [4.60-0ubuntu8]
Remv bluez-cups [4.60-0ubuntu8]
Remv bluez-gstreamer [4.60-0ubuntu8]
Remv brasero [2.30.2-0ubuntu1]
Remv rhythmbox-plugin-cdrecorder [0.12.8-0ubuntu7]
Remv sound-juicer [2.28.1-2]
Remv libbrasero-media0 [2.30.2-0ubuntu1]
Remv brasero-common [2.30.2-0ubuntu1]
Remv brltty-x11 [4.1-2ubuntu6]
Remv brltty [4.1-2ubuntu6]
Remv dkms [2.1.1.2-2fakesync1]
Remv build-essential [11.4build1]
Remv byobu [2.68-0ubuntu1.1]
Remv icedtea-6-jre-cacao [6b18-1.8.1-0ubuntu1]
Remv rmconverter [3.0-0medibuntu1]
Remv libaccess-bridge-java-jni [1.26.2-3] [openjdk-6-jre ]
Remv libaccess-bridge-java [1.26.2-3] [openjdk-6-jre ]
Remv liblog4j1.2-java [1.2.15-9ubuntu2] [openjdk-6-jre ]
Remv openjdk-6-jre [6b18-1.8.1-0ubuntu1]
Remv ca-certificates-java [20100406ubuntu1] [openjdk-6-jre-headless ]
Remv openjdk-6-jre-headless [6b18-1.8.1-0ubuntu1] [openjdk-6-jre-lib ]
Remv openjdk-6-jre-lib [6b18-1.8.1-0ubuntu1]
Remv indicator-me [0.2.6-0ubuntu1]
Remv indicator-applet-session [0.3.7-0ubuntu1]
Remv indicator-applet [0.3.7-0ubuntu1]
Remv gnome-session [2.30.0-0ubuntu1]
Remv gnome-applets [2.30.0-0ubuntu2]
Remv gnome-panel [1:2.30.2-0ubuntu0.2]
Remv gnome-control-center [1:2.30.1-0ubuntu1]
Remv capplets-data [1:2.30.1-0ubuntu1]
Remv checkbox-gtk [0.9.1]
Remv checkbox [0.9.1]
Remv checkinstall [1.6.1-10]
Remv chmsee [1.0.7-1.2ubuntu1]
Remv f-spot [0.6.1.5-2ubuntu7]
Remv libnunit2.4-cil [2.4.7+dfsg-5]
Remv tomboy [1.2.1-0ubuntu1]
Remv libndesk-dbus-glib1.0-cil [0.4.1-3]
Remv libndesk-dbus1.0-cil [0.6.0-4]
Remv gbrainy [1.41-1ubuntu1]
Remv libmono-addins-gui0.2-cil [0.4-6]
Remv libmono-addins0.2-cil [0.4-6]
Remv liblaunchpad-integration1.0-cil [0.1.35]
Remv libgnomepanel2.24-cil [2.26.0-2ubuntu1]
Remv libgnome2.24-cil [2.24.1-6ubuntu1]
Remv libglade2.0-cil [2.12.9-4]
Remv libgtk2.0-cil [2.12.9-4]
Remv libgnome-vfs2.0-cil [2.24.1-6ubuntu1]
Remv libgnome-keyring1.0-cil [1.0.0-3]
Remv libgmime2.4-cil-dev [2.4.14-1+nmu1]
Remv libgmime2.4-cil [2.4.14-1+nmu1]
Remv libglib2.0-cil-dev [2.12.9-4]
Remv libgconf2.0-cil [2.24.1-6ubuntu1]
Remv libart2.0-cil [2.24.1-6ubuntu1]
Remv libglib2.0-cil [2.12.9-4]
Remv libflickrnet2.2-cil [1:2.2.0-3]
Remv cli-common [0.7]
Remv compiz [1:0.8.4-0ubuntu15]
Remv compiz-gnome [1:0.8.4-0ubuntu15]
Remv compizconfig-backend-gconf [0.8.4-0ubuntu2]
Remv libcompizconfig0 [0.8.4-0ubuntu2]
Remv compiz-plugins [1:0.8.4-0ubuntu15]
Remv compiz-fusion-plugins-main [0.8.4-0ubuntu3]
Remv compiz-core [1:0.8.4-0ubuntu15]
Remv computer-janitor-gtk [1.14.1-0ubuntu2]
Remv computer-janitor [1.14.1-0ubuntu2]
Remv xserver-xorg-video-voodoo [1:1.2.3-1]
Remv xserver-xorg-video-vmware [1:10.16.9-1]
Remv xserver-xorg-video-vesa [1:2.3.0-1ubuntu1]
Remv xserver-xorg-video-v4l [1:0.2.0-4]
Remv xserver-xorg-video-tseng [1:1.2.3-1]
Remv xserver-xorg-video-trident [1:1.3.3-1]
Remv xserver-xorg-video-tdfx [1:1.4.3-1]
Remv xserver-xorg-video-sisusb [1:0.9.3-1]
Remv xserver-xorg-video-sis [1:0.10.2-2]
Remv xserver-xorg-video-siliconmotion [1:1.7.3-1]
Remv xserver-xorg-video-savage [1:2.3.1-1ubuntu1]
Remv xserver-xorg-video-s3virge [1:1.10.4-1]
Remv xserver-xorg-video-s3 [1:0.6.3-1]
Remv xserver-xorg-video-rendition [1:4.2.3-1]
Remv xserver-xorg-video-ati [1:6.13.0-1ubuntu5]
Remv xserver-xorg-video-radeon [1:6.13.0-1ubuntu5]
Remv xserver-xorg-video-r128 [6.8.1-2ubuntu1]
Remv xserver-xorg-video-openchrome [1:0.2.904+svn827-1]
Remv xserver-xorg-video-nv [1:2.1.15-1ubuntu3]
Remv xserver-xorg-video-neomagic [1:1.2.4-2]
Remv xserver-xorg-video-mga [1:1.4.11.dfsg-2ubuntu1]
Remv xserver-xorg-video-mach64 [6.8.2-2]
Remv xserver-xorg-video-intel [2:2.9.1-3ubuntu5]
Remv xserver-xorg-video-i740 [1:1.3.2-1]
Remv xserver-xorg-video-i128 [1:1.3.3-1]
Remv xserver-xorg-video-geode [2.11.8-4]
Remv xserver-xorg-video-fbdev [1:0.4.1-1ubuntu1]
Remv xserver-xorg-video-cirrus [1:1.3.2-1ubuntu1]
Remv xserver-xorg-video-chips [1:1.2.2-1]
Remv xserver-xorg-video-ark [1:0.7.2-1]
Remv xserver-xorg-input-all [1:7.5+5ubuntu1]
Remv xserver-xorg-input-wacom [1:0.10.5-0ubuntu4]
Remv xserver-xorg-input-vmmouse [1:12.6.5-4ubuntu2]
Remv xserver-xorg-input-synaptics [1.2.2-1ubuntu4]
Remv xserver-xorg-input-mouse [1:1.5.0-1]
Remv xserver-xorg-input-evdev [1:2.3.2-5ubuntu1] [xserver-xorg ]
Remv xserver-xorg-core [2:1.7.6-2ubuntu7.3] [xserver-xorg xserver-xorg-video-apm ]
Remv xorg [1:7.5+5ubuntu1] [xserver-xorg xserver-xorg-video-apm ]
Remv xserver-xorg [1:7.5+5ubuntu1] [xserver-xorg-video-apm ]
Remv xserver-xorg-video-apm [1:1.2.2-1]
Remv ubuntu-minimal [1.197]
Remv pm-utils-powersave-policy [0.3.1]
Remv pm-utils [1.3.0-1ubuntu2]
Remv gdm-guest-session [0.15]
Remv gdm [2.30.2.is.2.30.0-0ubuntu4]
Remv console-setup [1.34ubuntu15] [kbd ]
Remv kbd [1.15-1ubuntu3]
Remv indicator-sound [0.2.3-0ubuntu1]
Remv paprefs [0.9.9-2ubuntu1]
Remv pulseaudio-module-zeroconf [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv pulseaudio-module-x11 [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv pulseaudio-module-gconf [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv pulseaudio-module-bluetooth [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv pulseaudio-esound-compat [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv libcanberra-pulse [0.22-1ubuntu2]
Remv pulseaudio [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14]
Remv ubuntu-system-service [0.1.20.1]
Remv rhythmbox-ubuntuone-music-store [0.0.9-0ubuntu1]
Remv python-aptdaemon-gtk [0.11+bzr345-0ubuntu4.1]
Remv python-aptdaemon [0.11+bzr345-0ubuntu4.1]
Remv jockey-gtk [0.5.8-0ubuntu8.1]
Remv jockey-common [0.5.8-0ubuntu8.1]
Remv hplip [3.10.2-2ubuntu2.1]
Remv screen-resolution-extra [0.13]
Remv kubuntu-debug-installer [10.04ubuntu4]
Remv kpackagekit [0.5.4-0ubuntu4.3]
Remv polkit-kde-1 [0.95.1-2ubuntu1]
Remv nautilus-share [0.7.2-12build1]
Remv nautilus [1:2.30.1-0ubuntu1.1]
Remv gvfs-fuse [1.6.1-0ubuntu1build1]
Remv gvfs-bin [1.6.1-0ubuntu1build1]
Remv gvfs-backends [1.6.1-0ubuntu1build1]
Remv vinagre [2.30.2-0ubuntu1]
Remv evolution-plugins [2.28.3-0ubuntu10]
Remv evolution-indicator [0.2.8-0ubuntu1]
Remv evolution-exchange [2.28.3-0ubuntu1]
Remv evolution-couchdb [0.4.5-0ubuntu1]
Remv evolution [2.28.3-0ubuntu10]
Remv gnome-mag [1:0.16.1-0ubuntu1]
Remv python-gnomeapplet [2.30.0-0ubuntu1]
Remv usb-creator-gtk [0.2.22.1]
Remv system-config-printer-gnome [1.2.0+20100408-0ubuntu5.2]
Remv rhythmbox-plugins [0.12.8-0ubuntu7]
Remv rhythmbox [0.12.8-0ubuntu7]
Remv gnome-about [1:2.30.2-0ubuntu1]
Remv soundconverter [1.4.4-2]
Remv python-gnome2 [2.28.0-1ubuntu1]
Remv mousetweaks [2.30.0-0ubuntu1]
Remv tsclient [0.150-3ubuntu1]
Remv libgnome2-perl [1.042-2build1]
Remv libgnome-pilot2 [2.0.17-0ubuntu5]
Remv libgnomeui-0 [2.24.3-1]
Remv libgail-gnome-module [1.20.1-2]
Remv gnome-utils [2.30.0-0ubuntu1]
Remv gnome-power-manager [2.30.0-0ubuntu1]
Remv libpanel-applet2-0 [1:2.30.2-0ubuntu0.2]
Remv liblpint-bonobo0 [0.1.35]
Remv libbonoboui2-0 [2.24.3-0ubuntu1]
Remv libgnome2-0 [2.30.0-0ubuntu1]
Remv gvfs [1.6.1-0ubuntu1build1]
Remv gnome-system-tools [2.30.0-0ubuntu2]
Remv libpolkit-gtk-1-0 [0.96-2ubuntu2]
Remv gnome-session-bin [2.30.0-0ubuntu1]
Remv gconf-editor [2.30.0-0ubuntu1]
Remv policykit-1-gnome [0.96-2ubuntu2]
Remv policykit-1 [0.96-2]
Remv consolekit [0.4.1-3ubuntu1]
Remv gwibber [2.30.2-0ubuntu3]
Remv gwibber-service [2.30.2-0ubuntu3]
Remv python-desktopcouch [0.6.4-0ubuntu3] [python-desktopcouch-records desktopcouch ]
Remv desktopcouch [0.6.4-0ubuntu3] [python-desktopcouch-records ]
Remv python-desktopcouch-records [0.6.4-0ubuntu3]
Remv couchdb-bin [0.10.0-1ubuntu2]
Remv cron [3.0pl1-106ubuntu5]
Remv csladspa [1:5.10.1~dfsg1-3ubuntu3]
Remv csound-utils [1:5.10.1~dfsg1-3ubuntu3]
Remv csound-gui [1:5.10.1~dfsg1-3ubuntu3]
Remv csound [1:5.10.1~dfsg1-3ubuntu3]
Remv cups-driver-gutenprint [5.2.5-0ubuntu1.1]
Remv splix [2.0.0-2ubuntu3]
Remv ghostscript-cups [8.71.dfsg.1-0ubuntu5.3]
Remv pxljr [1.1-0ubuntu7]
Remv openprinting-ppds [20100216-0ubuntu3]
Remv foomatic-db-engine [4.0.4-0ubuntu1] [foomatic-db ]
Remv foomatic-db [20100216-0ubuntu3]
Remv foo2zjs [20100210-0ubuntu4]
Remv cups [1.4.3-1ubuntu1.2]
Remv cups-bsd [1.4.3-1ubuntu1.2]
Remv cups-client [1.4.3-1ubuntu1.2]
Remv curl [7.19.7-1ubuntu1]
Remv cvs [1:1.12.13-12ubuntu1]
Remv packagekit [0.5.7-0ubuntu2.1]
Remv usb-creator-common [0.2.22.1]
Remv update-notifier [0.99.3]
Remv gnome-disk-utility [2.30.1-1]
Remv libgdu0 [2.30.1-1]
Remv udisks [1.0.1-1ubuntu1]
Remv hal [0.5.14-0ubuntu6]
Remv indicator-session [0.2.8-0ubuntu2]
Remv upower [0.9.1-1]
Remv liboobs-1-4 [2.30.0-0ubuntu1]
Remv system-tools-backends [2.9.4-0ubuntu1]
Remv firefox-gnome-support [3.6.10+build1+nobinonly-0ubuntu0.10.04.1]
Remv libgnomevfs2-extra [1:2.24.2-1ubuntu2]
Remv libgnome2-vfs-perl [1.081-1build1]
Remv libgnomevfs2-0 [1:2.24.2-1ubuntu2]
Remv nautilus-sendto-empathy [2.30.2-0ubuntu1]
Remv empathy [2.30.2-0ubuntu1]
Remv mkvtoolnix-gui [3.0.0-0ubuntu1]
Remv gpac [0.4.5-0.3ubuntu6]
Remv libwxgtk2.8-0 [2.8.10.1-0ubuntu1.2]
Remv python-ubuntuone [0.3.1-0ubuntu1]
Remv libubuntuone-1.0-1 [0.3.1-0ubuntu1]
Remv ubuntuone-client-gnome [1.2.2-0ubuntu2]
Remv transmission-gtk [1.93-0ubuntu0.10.04.1]
Remv totem-plugins [2.30.2-0ubuntu1]
Remv totem-mozilla [2.30.2-0ubuntu1]
Remv totem [2.30.2-0ubuntu1]
Remv simple-scan [1.0.3-0ubuntu1]
Remv openoffice.org-gnome [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-gtk [1:3.2.0-7ubuntu4.1]
Remv libgdata6 [0.5.2-0ubuntu1]
Remv libdesktopcouch-glib-1.0-2 [0.6.3-0ubuntu2]
Remv libcouchdb-glib-1.0-2 [0.6.3-0ubuntu2]
Remv telepathy-butterfly [0.5.11-0ubuntu1]
Remv python-papyon [0.4.8-0ubuntu1]
Remv python-farsight [0.0.17-2ubuntu2]
Remv libtelepathy-farsight0 [0.0.13-1]
Remv telepathy-haze [0.3.4-1]
Remv libpurple0 [1:2.6.6-1ubuntu4]
Remv libgstfarsight0.10-0 [0.0.17-2ubuntu2]
Remv pitivi [0.13.4-0ubuntu3]
Remv gnome-media [2.30.0-0ubuntu1]
Remv gstreamer0.10-plugins-good [0.10.21-1ubuntu3]
Remv evolution-data-server [2.28.3.1-0ubuntu5]
Remv libgweather1 [2.30.0-0ubuntu1]
Remv libsoup-gnome2.4-1 [2.30.2-0ubuntu0.1]
Remv gnome-settings-daemon [2.30.1-0ubuntu1]
Remv gnome-screensaver [2.30.0-0ubuntu2]
Remv libgnomekbd4 [2.30.2-0ubuntu0.1]
Remv libgnome-window-settings1 [1:2.30.1-0ubuntu1]
Remv eog [2.30.0-0ubuntu1]
Remv libgnome-desktop-2-17 [1:2.30.2-0ubuntu1]
Remv update-manager [1:0.134.10]
Remv mythnetvision [2:0.23.1+fixes25902-0ubuntu2]
Remv mythvideo [2:0.23.1+fixes25902-0ubuntu2]
Remv mythnews [2:0.23.1+fixes25902-0ubuntu2]
Remv mythmusic [2:0.23.1+fixes25902-0ubuntu2]
Remv mythweather [2:0.23.1+fixes25902-0ubuntu2]
Remv mythgallery [2:0.23.1+fixes25902-0ubuntu2]
Remv mythbrowser [2:0.23.1+fixes25902-0ubuntu2]
Remv mythmovies [2:0.23.1+fixes25902-0ubuntu2]
Remv mythgame [2:0.23.1+fixes25902-0ubuntu2]
Remv mythtv-frontend [2:0.23.1+fixes26231-0ubuntu2]
Remv software-properties-gtk [0.75.10.1]
Remv language-selector [0.5.8]
Remv gdebi [0.6.0ubuntu2]
Remv gnome-codec-install [0.4.2ubuntu2]
Remv gksu [2.0.2-2ubuntu2]
Remv libgksu2-0 [2.0.13~pre1-1ubuntu4.1]
Remv libexchange-storage1.2-3 [2.28.3.1-0ubuntu5]
Remv libegroupwise1.2-13 [2.28.3.1-0ubuntu5]
Remv libedataserverui1.2-8 [2.28.3.1-0ubuntu5]
Remv libedata-cal1.2-6 [2.28.3.1-0ubuntu5]
Remv libedata-book1.2-2 [2.28.3.1-0ubuntu5]
Remv libecal1.2-7 [2.28.3.1-0ubuntu5]
Remv libebook1.2-9 [2.28.3.1-0ubuntu5]
Remv libebackend1.2-0 [2.28.3.1-0ubuntu5]
Remv libcamel1.2-14 [2.28.3.1-0ubuntu5]
Remv evolution-webcal [2.28.0-1]
Remv libedataserver1.2-11 [2.28.3.1-0ubuntu5]
Remv libatspi1.0-0 [1.30.1-0ubuntu1]
Remv gnome-terminal [2.30.2-0ubuntu1]
Remv gedit [2.30.3-0ubuntu0.1]
Remv file-roller [2.30.1.1-0ubuntu2]
Remv evince [2.30.3-0ubuntu1.1]
Remv ubuntu-docs [10.04.3]
Remv gnome-user-guide-en [2.30.0+git20100403ubuntu2]
Remv gnome-user-guide [2.30.0+git20100403ubuntu2]
Remv yelp [2.30.0-0ubuntu2]
Remv vino [2.28.2-0ubuntu2]
Remv seahorse [2.30.0-0ubuntu2]
Remv quadrapassel [1:2.30.0-0ubuntu6]
Remv onboard [0.93.0-0ubuntu4]
Remv python-gconf [2.28.0-1ubuntu1]
Remv notify-osd [0.9.29-0ubuntu2]
Remv network-manager-pptp-gnome [0.8-0ubuntu3]
Remv nautilus-sendto [2.28.4-0ubuntu1]
Remv metacity [1:2.30.1-0ubuntu1]
Remv libmetacity-private0 [1:2.30.1-0ubuntu1]
Remv libgtkhtml-editor0 [1:3.29.6.is.3.28.3-0ubuntu2]
Remv libgtkhtml3.14-19 [1:3.29.6.is.3.28.3-0ubuntu2]
Remv libgnome-media0 [2.30.0-0ubuntu1]
Remv libgconfmm-2.6-1c2 [2.28.0-1]
Remv libcryptui0 [2.30.0-0ubuntu2]
Remv ibus-table [1.2.0.20100111-1]
Remv ibus-m17n [1.2.0.20091217-1]
Remv ibus [1.2.0.20091215-1ubuntu4]
Remv gucharmap [1:2.30.0-0ubuntu1]
Remv gnomine [1:2.30.0-0ubuntu6]
Remv gnome-system-monitor [2.28.0-1ubuntu2]
Remv gnome-mahjongg [1:2.30.0-0ubuntu6]
Remv gnome-sudoku [1:2.30.0-0ubuntu6]
Remv gnome-games-common [1:2.30.0-0ubuntu6]
Remv empathy-common [2.30.2-0ubuntu1]
Remv totem-common [2.30.2-0ubuntu1]
Remv nautilus-data [1:2.30.1-0ubuntu1.1]
Remv ubuntu-artwork [53.5]
Remv light-themes [0.1.6.6]
Remv libgnomekbd-common [2.30.2-0ubuntu0.1]
Remv gnome-terminal-data [2.30.2-0ubuntu1]
Remv gnome-panel-data [1:2.30.2-0ubuntu0.2]
Remv gnome-keyring [2.92.92.is.2.30.3-0ubuntu1.1]
Remv ubuntu-wallpapers [0.31.3]
Remv metacity-common [1:2.30.1-0ubuntu1]
Remv libgweather-common [2.30.0-0ubuntu1]
Remv libgnomevfs2-common [1:2.24.2-1ubuntu2]
Remv libgnome2-common [2.30.0-0ubuntu1]
Remv gnome-session-canberra [0.22-1ubuntu2]
Remv gnome-media-common [2.30.0-0ubuntu1]
Remv gnome-applets-data [2.30.0-0ubuntu2]
Remv gcalctool [5.30.0.is.5.28.2-0ubuntu2]
Remv gconf2 [2.28.1-0ubuntu1]
Remv gconf-defaults-service [2.28.1-0ubuntu1]
Remv libgconf2-4 [2.28.1-0ubuntu1]
Remv gconf2-common [2.28.1-0ubuntu1]
Remv update-manager-kde [1:0.134.10]
Remv software-properties-kde [0.75.10.1]
Remv install-package [0.5.2]
Remv gdebi-kde [0.6.0ubuntu2]
Remv python-kde4 [4:4.4.2-0ubuntu2]
Remv kreversi [4:4.4.2-0ubuntu1]
Remv libkdegames5 [4:4.4.2-0ubuntu1]
Remv kdemultimedia-kio-plugins [4:4.4.2-0ubuntu3]
Remv libkcddb4 [4:4.4.2-0ubuntu3]
Remv kdesudo [3.4.2.3-0ubuntu1]
Remv plasma-scriptengine-javascript [4:4.4.2-0ubuntu4.1] [kdebase-runtime ]
Remv kdebase-runtime [4:4.4.2-0ubuntu4.1]
Remv kdepimlibs5 [4:4.4.2-0ubuntu2.1]
Remv libplasma3 [4:4.4.2-0ubuntu4]
Remv kdelibs5 [4:4.4.2-0ubuntu4] [kdelibs-bin ]
Remv kdelibs-bin [4:4.4.2-0ubuntu4]
Remv dbus-x11 [1.2.16-2ubuntu4]
Remv dbus [1.2.16-2ubuntu4]
Remv debhelper [7.4.15ubuntu1]
Remv pnm2ppa [1.13-0ubuntu1]
Remv ghostscript-x [8.71.dfsg.1-0ubuntu5.3]
Remv ghostscript [8.71.dfsg.1-0ubuntu5.3]
Remv mythtv-themes [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-metallurgy [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-graphite [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-blootube-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-titivillus-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-transcode-utils [2:0.23.1+fixes26231-0ubuntu2]
Remv mythtv-theme-projectgrayhem-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-childish [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-blueosd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-mono-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-arclight [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-mythbuntu [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-iulius-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-theme-retro-osd [2:0.23.0+fixes25253-0ubuntu2]
Remv mythtv-common [2:0.23.1+fixes26231-0ubuntu2]
Remv ttf-droid [1.00~b112+dfsg+1-0ubuntu1]
Remv latex-xft-fonts [0.1-8]
Remv x-ttcidfont-conf [32]
Remv ttf-unfonts-core [1.0.1-7ubuntu1]
Remv psfontmgr [0.11.10-4ubuntu1]
Remv gimp-gutenprint [5.2.5-0ubuntu1.1]
Remv gimp-resynthesizer [0.16-1.1]
Remv gimp-plugin-registry [2.3-1]
Remv gimp-gap [2.6.0+dfsg-1build1]
Remv gimp [2.6.8-2ubuntu1.1]
Remv libwmf0.2-7-gtk [0.2.8.4-6.1ubuntu2]
Remv libmagickcore2-extra [7:6.5.7.8-1ubuntu1]
Remv libwmf0.2-7 [0.2.8.4-6.1ubuntu2]
Remv firefox [3.6.10+build1+nobinonly-0ubuntu0.10.04.1] [firefox-branding ]
Remv firefox-branding [3.6.10+build1+nobinonly-0ubuntu0.10.04.1]
Remv gyachi-plugins-extra [1.2.6-0.1~baudm5~lucid1]
Remv gyachi [1.2.6-0.1~baudm5~lucid1]
Remv libpoppler-glib4 [0.12.4-0ubuntu5]
Remv flashplugin-installer [10.1.85.3ubuntu0.10.04.1]
Remv xulrunner-1.9.2 [1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1]
Remv gyachi-plugins [1.2.6-0.1~baudm5~lucid1]
Remv mplayer [2:1.0-svn31059-0ubuntu2]
Remv synaptic [0.63.1ubuntu7]
Remv python-vte [1:0.23.5-0ubuntu1.1]
Remv python-gtksourceview2 [2.10.1-0ubuntu1]
Remv libvte9 [1:0.23.5-0ubuntu1.1]
Remv gnome-themes-selected [2.30.0-0ubuntu1]
Remv ubuntu-mono [0.0.18]
Remv gnome-themes-ubuntu [0.6.1]
Remv humanity-icon-theme [0.5.2.1]
Remv pavumeter [0.9.3-1ubuntu1]
Remv paman [0.9.4-1ubuntu2]
Remv gnome-icon-theme [2.28.0-1ubuntu1]
Remv gnome-accessibility-themes [2.30.0-0ubuntu1]
Remv librsvg2-common [2.26.3-0ubuntu1]
Remv gstreamer0.10-plugins-bad [0.10.18-1ubuntu1]
Remv libgegl-0.0-0 [0.0.22-0ubuntu4]
Remv librsvg2-2 [2.26.3-0ubuntu1]
Remv gparted [0.5.1-1ubuntu3]
Remv pavucontrol [0.9.9-1]
Remv libglademm-2.4-1c2a [2.6.7-2build1]
Remv libgtkmm-2.4-1c2a [1:2.20.3-0ubuntu1]
Remv libpangomm-1.4-1 [2.26.2-0ubuntu1]
Remv libido-0.1-0 [0.1.6-0ubuntu1]
Remv libgutenprintui2-1 [5.2.5-0ubuntu1.1]
Remv libgtksourceview2.0-0 [2.10.4-0ubuntu1]
Remv mozilla-plugin-vlc [1.0.6-1ubuntu1.2]
Remv vlc [1.0.6-1ubuntu1.2]
Remv ssh-askpass-gnome [1:5.3p1-3ubuntu4]
Remv openoffice.org-emailmerge [1:3.2.0-7ubuntu4.1]
Remv python-uno [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-help-en-us [1:3.2.0-7ubuntu1]
Remv openoffice.org-help-en-gb [1:3.2.0-7ubuntu1]
Remv openoffice.org-writer [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-math [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-impress [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-draw [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-calc [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-base-core [1:3.2.0-7ubuntu4.1]
Remv openoffice.org-core [1:3.2.0-7ubuntu4.1]
Remv zenity [2.30.0-0ubuntu1]
Remv ubuntuone-client [1.2.2-0ubuntu2]
Remv python-ubuntuone-client [1.2.2-0ubuntu2]
Remv python-notify [0.1.1-2build3]
Remv libnotify1 [0.4.5-1ubuntu4]
Remv libnautilus-extension1 [1:2.30.1-0ubuntu1.1]
Remv libgtkspell-dev [2.0.16-1]
Remv libgtk2.0-dev [2.20.1-0ubuntu2]
Remv libgtk2.0-bin [2.20.1-0ubuntu2]
Remv libgimp2.0 [2.6.8-2ubuntu1.1]
Remv libgcr0 [2.92.92.is.2.30.3-0ubuntu1.1]
Remv libgail-common [2.20.1-0ubuntu2]
Remv libgtkhtml2-0 [2.11.1-2ubuntu3]
Remv python-webkit [1.1.7-1]
Remv libwebkit-1.0-2 [1.2.0-1]
Remv python-gnomecanvas [2.28.0-1ubuntu1]
Remv libgnome2-canvas-perl [1.002-2build1]
Remv libgnomecanvas2-0 [2.30.1-0ubuntu1]
Remv libgail18 [2.20.1-0ubuntu2]
Remv libevview2 [2.30.3-0ubuntu1.1]
Remv libevdocument2 [2.30.3-0ubuntu1.1]
Remv python-appindicator [0.0.19-0ubuntu4]
Remv libappindicator0 [0.0.19-0ubuntu4]
Remv indicator-messages [0.3.6-0ubuntu2]
Remv indicator-application [0.0.19-0ubuntu4]
Remv libdbusmenu-gtk1 [0.2.9-0ubuntu3.1]
Remv libgdu-gtk0 [2.30.1-1]
Remv libavahi-ui0 [0.6.25-1ubuntu6.1]
Remv gtk2-engines-pixbuf [2.20.1-0ubuntu2]
Remv mjpegtools [1:1.9.0-0.5ubuntu3]
Remv libgtkglext1 [1.2.0-1ubuntu1]
Remv libdv-bin [1.0.0-2ubuntu2]
Remv libaudcore1 [2.3-1ubuntu4]
Remv kino [1.3.4-1ubuntu1]
Remv gvncviewer [0.3.10-2ubuntu2]
Remv xscreensaver-gl [5.10-3ubuntu4]
Remv screensaver-default-images [0.2-1]
Remv xscreensaver-data [5.10-3ubuntu4]
Remv xdg-user-dirs-gtk [0.8-1ubuntu1]
Remv python-wnck [2.30.0-0ubuntu1]
Remv python-virtkey [0.50ubuntu3]
Remv python-pygoocanvas [0.14.1-0ubuntu1]
Remv python-indicate [0.3.0-0ubuntu1]
Remv python-gtkspell [2.25.3-4.1ubuntu4]
Remv python-ibus [1.2.0.20091215-1ubuntu4]
Remv python-gnomekeyring [2.30.0-0ubuntu1]
Remv gnome-menus [2.30.0-0ubuntu4]
Remv python-gmenu [2.30.0-0ubuntu4]
Remv python-glade2 [2.17.0-0ubuntu2]
Remv python-gtk2 [2.17.0-0ubuntu2]
Remv plymouth-x11 [0.8.2-2ubuntu2]
Remv gnupg2 [2.0.14-1ubuntu1.2]
Remv gnupg-agent [2.0.14-1ubuntu1.2]
Remv pinentry-gtk2 [0.7.6-1]
Remv libwnck22 [1:2.30.0-0ubuntu1]
Remv libunique-1.0-0 [1.1.6-1ubuntu2]
Remv python-launchpad-integration [0.1.35]
Remv libgucharmap7 [1:2.30.0-0ubuntu1]
Remv libgdict-1.0-6 [2.30.0-0ubuntu1]
Remv liblaunchpad-integration1 [0.1.35]
Remv libindicator0 [0.3.8-0ubuntu1]
Remv libindicate-gtk2 [0.3.6-0ubuntu1]
Remv libgtkspell0 [2.0.16-1]
Remv libgtk2-perl [1:1.221-4ubuntu2]
Remv libgtk-vnc-1.0-0 [0.3.10-2ubuntu2]
Remv libgpod-common [0.7.93-0ubuntu1]
Remv libgpod4 [0.7.93-0ubuntu1]
Remv libgoocanvas3 [0.15-0ubuntu2]
Remv libgnome-bluetooth7 [2.30.0-0ubuntu3]
Remv libglade2-0 [1:2.6.4-1build1]
Remv libclutter-gtk-0.10-0 [0.10.4-0ubuntu1]
Remv libclutter-1.0-0 [1.2.4-0ubuntu1]
Remv libcanberra-gtk-module [0.22-1ubuntu2]
Remv libcanberra-gtk0 [0.22-1ubuntu2]
Remv ibus-gtk [1.2.0.20091215-1ubuntu4]
Remv gtk2-engines-murrine [0.90.3+git20100323-0ubuntu3]
Remv gtk2-engines [1:2.20.0-0ubuntu1]
Remv libgtk2.0-0 [2.20.1-0ubuntu2]
Remv plymouth-theme-ubuntu-logo [0.8.2-2ubuntu2]
Remv plymouth-label [0.8.2-2ubuntu2]
Remv libpango1.0-dev [1.28.0-0ubuntu2]
Remv libpango-perl [1.221-2]
Remv libgraphviz4 [2.20.2-8ubuntu3]
Remv gstreamer0.10-x [0.10.28-1]
Remv libpango1.0-0 [1.28.0-0ubuntu2]
Remv libpango1.0-common [1.28.0-0ubuntu2]
Remv gsfonts [1:8.11+urwcyr1.0.7~pre44-4]
Remv defoma [0.11.10-4ubuntu1]
Remv desktop-file-utils [0.16-0ubuntu2]
Remv dmsetup [2:1.02.39-1ubuntu4.1]
Remv libglibmm-2.4-doc [2.24.2-0ubuntu1]
Remv doc-base [0.9.5]
Remv rarian-compat [0.8.1-4ubuntu1]
Remv docbook-xml [4.5-7]
Remv docbook-xsl [1.75.2+dfsg-3]
Remv dosfstools [3.0.7-1]
Remv dpkg-dev [1.15.5.6ubuntu4.3]
Remv dvd+rw-tools [7.1-6]
Remv dvdauthor [0.6.14-3ubuntu4]
Remv e2fsprogs [1.41.11-1ubuntu2]
Remv erlang-xmerl [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-syntax-tools [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-inets [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-ssl [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-runtime-tools [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-public-key [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-mnesia [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-crypto [1:13.b.3-dfsg-2ubuntu2.1]
Remv erlang-base [1:13.b.3-dfsg-2ubuntu2.1]
Remv foomatic-filters [4.0.4-0ubuntu1]
Remv friendly-recovery [0.2.10]
Remv ftp [0.17-19build1]
Remv git-core [1:1.7.0.4-1]
Remv gnome-desktop-data [1:2.30.2-0ubuntu1]
Remv gnupg-curl [1.4.10-2ubuntu1]
Remv googleearth [5.1.3533.1731-0medibuntu1]
Remv gstreamer0.10-plugins-base-apps [0.10.28-1]
Remv gstreamer0.10-pulseaudio [0.10.21-1ubuntu3]
Remv gstreamer0.10-tools [0.10.28-1]
Remv hostname [3.03ubuntu1]
Remv htop [0.8.3-1ubuntu1]
Remv icoutils [0.26.0-4ubuntu1]
Remv ureadahead [0.100.0-4.1.3]
Remv plymouth-theme-ubuntu-text [0.8.2-2ubuntu2]
Remv plymouth [0.8.2-2ubuntu2] [mountall ]
Remv mountall [2.15.2] [upstart ]
Remv linux-image-generic-pae [2.6.32.25.27] [upstart ]
Remv linux-image-2.6.32-25-generic-pae [2.6.32-25.44] [upstart ]
Remv linux-generic [2.6.32.25.27] [upstart ]
Remv linux-image-generic [2.6.32.25.27] [upstart ]
Remv linux-image-2.6.32-25-generic [2.6.32-25.44] [upstart ]
Remv linux-image-2.6.32-24-generic-pae [2.6.32-24.43] [upstart ]
Remv linux-image-2.6.32-24-generic [2.6.32-24.43] [upstart ]
Remv wireless-crda [1.12] [upstart ]
Remv powermgmt-base [1.31] [upstart ]
Remv pcmciautils [014-4ubuntu4] [upstart ]
Remv media-player-info [6-1] [upstart ]
Remv sane-utils [1.0.20-13ubuntu2] [upstart ]
Remv libsane [1.0.20-13ubuntu2] [upstart ]
Remv ntfs-3g [1:2010.3.6-1ubuntu1] [upstart ]
Remv initramfs-tools [0.92bubuntu78] [udev upstart ]
Remv udev [151-12.1] [upstart ]
Remv screen [4.0.3-14ubuntu1.2] [upstart ]
Remv samba [2:3.4.7~dfsg-1ubuntu3.2] [upstart ]
Remv ifupdown [0.6.8ubuntu29.1] [upstart ]
Remv vnc4server [4.1.1+xorg4.3.0-37ubuntu2] [upstart ]
Remv xserver-common [2:1.7.6-2ubuntu7.3] [upstart ]
Remv libsdl1.2-dev [1.2.14-4ubuntu1.1] [upstart ]
Remv libglu1-mesa-dev [7.7.1-1ubuntu3] [upstart ]
Remv libgl1-mesa-dev [7.7.1-1ubuntu3] [upstart ]
Remv mesa-common-dev [7.7.1-1ubuntu3] [upstart ]
Remv libpulse-dev [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14] [upstart ]
Remv libxt-dev [1:1.0.7-1] [upstart ]
Remv libxrandr-dev [2:1.3.0-3] [upstart ]
Remv libxft-dev [2.1.14-1ubuntu1] [upstart ]
Remv libxcursor-dev [1:1.1.10-1] [upstart ]
Remv libcairo2-dev [1.8.10-2ubuntu1] [upstart ]
Remv libxrender-dev [1:0.9.5-1] [upstart ]
Remv libxinerama-dev [2:1.1-2] [upstart ]
Remv libxi-dev [2:1.3-3] [upstart ]
Remv libxdamage-dev [1:1.1.2-1] [upstart ]
Remv libxcomposite-dev [1:0.4.1-1] [upstart ]
Remv libxfixes-dev [1:4.0.4-1] [upstart ]
Remv libdirectfb-dev [1.2.8-5ubuntu2] [upstart ]
Remv libxext-dev [2:1.1.1-2] [upstart ]
Remv libaa1-dev [1.4p5-38build1] [upstart ]
Remv libx11-dev [2:1.3.2-1ubuntu3] [upstart ]
Remv xtrans-dev [1.2.5-1] [upstart ]
Remv xbase-clients [1:7.5+5ubuntu1] [upstart ]
Remv xinit [1.2.0-1] [upstart ]
Remv xfonts-scalable [1:1.0.1-1] [upstart ]
Remv xfonts-mathml [4ubuntu1] [upstart ]
Remv xfonts-base [1:1.0.1] [upstart ]
Remv xfonts-75dpi [1:1.0.1] [upstart ]
Remv xfonts-100dpi [1:1.0.1] [upstart ]
Remv xfonts-utils [1:7.5+2] [upstart ]
Remv xfonts-encodings [1:1.0.3-1] [upstart ]
Remv x11-xserver-utils [7.5+1ubuntu2] [upstart ]
Remv libxklavier16 [5.0-0ubuntu1] [upstart ]
Remv x11-xkb-utils [7.5+1] [upstart ]
Remv x11-xfs-utils [7.4+1build2] [upstart ]
Remv x11-utils [7.5+3] [upstart ]
Remv x11-session-utils [7.5+1] [upstart ]
Remv x11-apps [7.5+1ubuntu2] [upstart ]
Remv libggi-target-x [1:2.2.2-5ubuntu1] [upstart ]
Remv libggi2 [1:2.2.2-5ubuntu1] [upstart ]
Remv libxxf86dga1 [2:1.1.1-2] [upstart ]
Remv libmyth-0.23-0 [2:0.23.1+fixes26231-0ubuntu2] [upstart ]
Remv phonon [4:4.6.2-0ubuntu5.1] [upstart ]
Remv phonon-backend-xine [4:4.4.0-0ubuntu2] [upstart ]
Remv libxine1 [1.1.17-1ubuntu3] [upstart ]
Remv libxine1-x [1.1.17-1ubuntu3] [upstart ]
Remv libxvmc1 [2:1.0.5-1ubuntu1] [upstart ]
Remv pulseaudio-utils [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14] [upstart ]
Remv vlc-plugin-pulse [1.0.6-1ubuntu1.2] [upstart ]
Remv transcode [3:1.1.5-0ubuntu6] [upstart ]
Remv libmjpegtools-1.9 [1:1.9.0-0.5ubuntu3] [upstart ]
Remv libsdl-image1.2 [1.2.10-1] [upstart ]
Remv libsdl1.2debian [1.2.14-4ubuntu1.1] [upstart ]
Remv libsdl1.2debian-pulseaudio [1.2.14-4ubuntu1.1] [upstart ]
Remv libcsound64-5.2 [1:5.10.1~dfsg1-3ubuntu3] [upstart ]
Remv libfluidsynth1 [1.1.1-2build1] [upstart ]
Remv python-speechd [0.6.8~unofficial~rc2-0ubuntu3] [upstart ]
Remv speech-dispatcher [0.6.8~unofficial~rc2-0ubuntu3] [upstart ]
Remv libxine1-misc-plugins [1.1.17-1ubuntu3] [upstart ]
Remv libpulse-mainloop-glib0 [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14] [upstart ]
Remv libpulse-browse0 [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14] [upstart ]
Remv libasound2-plugins [1.0.22-0ubuntu6] [upstart ]
Remv libpulse0 [1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14] [upstart ]
Remv libxtst6 [2:1.1.0-2] [upstart ]
Remv skype [2.1.0.81-1] [upstart ]
Remv libxss1 [1:1.2.0-2] [upstart ]
Remv libxres1 [2:1.0.4-1] [upstart ]
Remv x11proto-damage-dev [1:1.2.0-1] [upstart ]
Remv x11proto-composite-dev [1:0.4.1-1] [upstart ]
Remv x11proto-fixes-dev [1:4.1.1-2] [upstart ]
Remv x11proto-xext-dev [7.1.1-2] [upstart ]
Remv libxcb-render-util0-dev [0.3.6-1build1] [upstart ]
Remv libxcb-render0-dev [1.5-2] [upstart ]
Remv libxcb1-dev [1.5-2] [upstart ]
Remv libxau-dev [1:1.0.5-1] [upstart ]
Remv python-qt4 [4.7.2-0ubuntu1] [upstart ]
Remv libqt4-webkit [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-svg [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-scripttools [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-qt3support [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-opengl [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-help [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libphonon4 [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqt4-designer [4:4.6.2-0ubuntu5.1] [upstart ]
Remv libqtscript4-uitools [0.1.0-3build1] [upstart ]
Remv libqtscript4-gui [0.1.0-3build1] [upstart ]
Remv libpolkit-qt-1-0 [0.95.1-1fakesync1] [upstart ]
Remv libdbusmenu-qt2 [0.3.2-0ubuntu1] [upstart ]
Remv libqtgui4 [4:4.6.2-0ubuntu5.1] [upstart ]
Remv wmctrl [1.07-6] [upstart ]
Remv mtink [1.0.16-2] [upstart ]
Remv lesstif2 [1:0.95.2-1] [upstart ]
Remv xterm [256-1ubuntu1] [upstart ]
Remv libglew1.5 [1.5.2-0ubuntu1] [upstart ]
Remv libxaw7 [2:1.0.7-1] [upstart ]
Remv libxmu6 [2:1.0.5-1] [upstart ]
Remv obex-data-server [0.4.5-1] [upstart ]
Remv imagemagick [7:6.5.7.8-1ubuntu1] [upstart ]
Remv libmagickwand2 [7:6.5.7.8-1ubuntu1] [upstart ]
Remv perlmagick [7:6.5.7.8-1ubuntu1] [upstart ]
Remv libmagickcore2 [7:6.5.7.8-1ubuntu1] [upstart ]
Remv m17n-contrib [1.1.10-1] [upstart ]
Remv m17n-db [1.5.5-1] [upstart ]
Remv libm17n-0 [1.5.5-1] [upstart ]
Remv libaudio-dev [1.9.2-3] [upstart ]
Remv libaudio2 [1.9.2-3] [upstart ]
Remv libxt6 [1:1.0.7-1] [upstart ]
Remv libstartup-notification0 [0.10-1build1] [upstart ]
Remv libsm-dev [2:1.1.1-1] [upstart ]
Remv libsm6 [2:1.1.1-1] [upstart ]
Remv libice-dev [2:1.0.6-1] [upstart ]
Remv libice6 [2:1.0.6-1] [upstart ]
Remv x11-common [1:7.5+5ubuntu1] [upstart ]
Remv util-linux [2.17.2-0ubuntu1] [upstart ]
Remv ufw [0.30pre1-0ubuntu2] [upstart ]
Remv rsyslog [4.2.0-2ubuntu8] [upstart ]
Remv openssh-server [1:5.3p1-3ubuntu4] [upstart ]
Remv network-manager-pptp [0.8-0ubuntu3] [upstart ]
Remv pptp-linux [1.7.2-4] [upstart ]
Remv pppoeconf [1.19ubuntu1] [upstart ]
Remv pppconfig [2.3.18ubuntu2] [upstart ]
Remv ppp [2.4.5~git20081126t100229-0ubuntu3] [upstart ]
Remv procps [1:3.2.8-1ubuntu4] [upstart ]
Remv libsoap-lite-perl [0.710.10-1] [upstart ]
Remv libxml-xpath-perl [1.13-7] [upstart ]
Remv libnet-dbus-perl [0.33.6-1build3] [upstart ]
Remv libxml-twig-perl [1:3.32-3ubuntu1] [upstart ]
Remv libxml-simple-perl [2.18-3] [upstart ]
Remv libxml-sax-expat-perl [0.40-1] [upstart ]
Remv librpc-xml-perl [0.72-1] [upstart ]
Remv libxml-parser-perl [2.36-1.1build3] [upstart ]
Remv libwww-perl [5.834-1ubuntu0.1] [upstart ]
Remv lftp [4.0.2-1ubuntu0.1] [upstart ]
Remv libio-socket-ssl-perl [1.31-1] [upstart ]
Remv telnet [0.17-36build1] [upstart ]
Remv ntpdate [1:4.2.4p8+dfsg-1ubuntu2] [upstart ]
Remv ntp [1:4.2.4p8+dfsg-1ubuntu2] [upstart ]
Remv netbase [4.35ubuntu3] [upstart ]
Remv linux-sound-base [1.0.22.1+dfsg-0ubuntu3] [upstart ]
Remv module-init-tools [3.11.1-2ubuntu1] [upstart ]
Remv irqbalance [0.55+20091017-3ubuntu2] [upstart ]
Remv upstart [0.6.5-7] [initscripts ]
Remv initscripts [2.87dsf-4ubuntu17]
Remv initramfs-tools-bin [0.92bubuntu78]
Remv intel-gpu-tools [1.0.2+git20100324-0ubuntu1]
Remv po-debconf [1.0.16]
Remv intltool-debian [0.35.0+20060710.1]
Remv kerneloops-daemon [0.12+git20090217-1ubuntu7]
Remv language-selector-common [0.5.8]
Remv laptop-detect [0.13.7ubuntu2]
Remv libakonadiprivate1 [1.3.1-0ubuntu3]
Remv libapparmor-perl [2.5-0ubuntu3]
Remv libaprutil1-ldap [1.3.9+dfsg-3build1]
Remv libbind9-60 [1:9.7.0.dfsg.P1-1]
Remv obexd-client [0.22-0ubuntu2]
Remv libpisync1 [0.12.4-7ubuntu1]
Remv libpisock9 [0.12.4-7ubuntu1]
Remv libbluetooth3 [4.60-0ubuntu8]
Remv libcairo-perl [1.061-1build1]
Remv libcarp-clan-perl [6.02-1]
Remv libpam-ck-connector [0.4.1-3ubuntu1]
Remv libck-connector0 [0.4.1-3ubuntu1]
Remv libparse-debianchangelog-perl [1.1.1-2ubuntu2]
Remv libclass-accessor-perl [0.34-1]
Remv libmime-tools-perl [5.427-2]
Remv libconvert-binhex-perl [1.119+pristine-3]
Remv libcrypt-ssleay-perl [0.57-2]
Remv libspectre1 [0.2.3-2]
Remv libgs8 [8.71.dfsg.1-0ubuntu5.3]
Remv libcupsimage2 [1.4.3-1ubuntu1.2]
Remv libcupsppdc1 [1.4.3-1ubuntu1.2]
Remv libcupscgi1 [1.4.3-1ubuntu1.2]
Remv libcupsdriver1 [1.4.3-1ubuntu1.2]
Remv libcupsmime1 [1.4.3-1ubuntu1.2]
Remv system-config-printer-udev [1.2.0+20100408-0ubuntu5.2]
Remv system-config-printer-common [1.2.0+20100408-0ubuntu5.2]
Remv python-cups [1.9.49-0ubuntu1]
Remv libcups2 [1.4.3-1ubuntu1.2]
Remv libcurl3 [7.19.7-1ubuntu1]
Remv python-pycurl [7.19.0-3]
Remv libsoprano4 [2.4.2+dfsg.1-0ubuntu1.1]
Remv soprano-daemon [2.4.2+dfsg.1-0ubuntu1.1]
Remv librdf0 [1.0.10-1ubuntu1]
Remv librasqal2 [0.9.17-1]
Remv libraptor1 [1.4.21-1ubuntu1]
Remv libcurl3-gnutls [7.19.7-1ubuntu1]
Remv libdate-manip-perl [6.05-1]
Remv mysql-client [5.1.41-3ubuntu12.6]
Remv mysql-client-5.1 [5.1.41-3ubuntu12.6]
Remv libdbd-mysql-perl [4.012-1ubuntu1]
Remv libdbi-perl [1.609-1build1]
Remv libdigest-sha1-perl [2.12-1build1]
Remv libisccfg60 [1:9.7.0.dfsg.P1-1]
Remv libdns64 [1:9.7.0.dfsg.P1-1]
Remv liberror-perl [0.17-1]
Remv libfcgi-perl [0.68-1]
Remv update-inetd [4.35]
Remv libfile-copy-recursive-perl [0.38-1]
Remv libhtml-format-perl [2.04-2]
Remv libfont-afm-perl [1.20-1]
Remv libfreezethaw-perl [0.45-1]
Remv libglib-perl [1:1.222-1]
Remv libgphoto2-2 [2.4.8-0ubuntu2]
Remv libgphoto2-port0 [2.4.8-0ubuntu2]
Remv smbclient [2:3.4.7~dfsg-1ubuntu3.2]
Remv samba-common-bin [2:3.4.7~dfsg-1ubuntu3.2]
Remv openssh-client [1:5.3p1-3ubuntu4]
Remv mencoder [2:1.0-svn31059-0ubuntu2]
Remv vlc-nox [1.0.6-1ubuntu1.2]
Remv python-smbc [1.0.6-0ubuntu3]
Remv libsmbclient [2:3.4.7~dfsg-1ubuntu3.2]
Remv libqt4-sql-psql [4:4.6.2-0ubuntu5.1]
Remv libpq5 [8.4.5-0ubuntu10.04]
Remv libpam-smbpass [2:3.4.7~dfsg-1ubuntu3.2]
Remv subversion [1.6.6dfsg-2ubuntu1]
Remv libsvn1 [1.6.6dfsg-2ubuntu1]
Remv libldap-2.4-2 [2.4.21-0ubuntu5.3]
Remv libneon27-gnutls [0.29.0-1]
Remv libgssapi-krb5-2 [1.8.1+dfsg-2ubuntu0.3]
Remv libgtkhtml-editor-common [1:3.29.6.is.3.28.3-0ubuntu2]
Remv libgtop2-7 [2.26.1-0ubuntu2]
Remv libgtop2-common [2.26.1-0ubuntu2]
Remv libhal-storage1 [0.5.14-0ubuntu6]
Remv libhtml-tree-perl [3.23-1]
Remv libhtml-parser-perl [3.64-1]
Remv libhtml-tagset-perl [3.20-2]
Remv libimage-size-perl [3.220-1]
Remv libio-string-perl [1.08-2]
Remv libio-stringy-perl [2.110-4]
Remv libjs-mootools [1.2.4.0~debian1-1]
Remv libkrb5-3 [1.8.1+dfsg-2ubuntu0.3]
Remv libk5crypto3 [1.8.1+dfsg-2ubuntu0.3]
Remv libmail-sendmail-perl [0.79.16-1]
Remv libmailtools-perl [2.05-1]
Remv libmath-round-perl [0.06-3]
Remv libmldbm-perl [2.01-3]
Remv libmono-cairo2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-system-runtime2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono2.0-cil [2.4.4~svn151842-1ubuntu4] [libmono-system-web2.0-cil ]
Remv libmono-system-web2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-sqlite2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-system-data2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-sharpzip2.84-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-data-tds2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-posix2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libmono-system2.0-cil [2.4.4~svn151842-1ubuntu4] [libmono-security2.0-cil ]
Remv libmono-i18n-west2.0-cil [2.4.4~svn151842-1ubuntu4] [libmono-security2.0-cil ]
Remv libmono-corlib2.0-cil [2.4.4~svn151842-1ubuntu4] [mono-2.0-gac libmono-security2.0-cil ]
Remv mono-runtime [2.4.4~svn151842-1ubuntu4] [mono-2.0-gac libmono-security2.0-cil ]
Remv mono-gac [2.4.4~svn151842-1ubuntu4] [mono-2.0-gac libmono-security2.0-cil ]
Remv mono-2.0-gac [2.4.4~svn151842-1ubuntu4] [libmono-security2.0-cil ]
Remv libmono-security2.0-cil [2.4.4~svn151842-1ubuntu4]
Remv libplrpc-perl [0.2020-2]
Remv libnet-daemon-perl [0.43-1]
Remv libnet-libidn-perl [0.12.ds-1]
Remv libnet-ssleay-perl [1.35-2ubuntu1]
Remv libossp-uuid-perl [1.6.2-1ubuntu1]
Remv protobuf-compiler [2.2.0a-0.1ubuntu1]
Remv libprotoc5 [2.2.0a-0.1ubuntu1]
Remv libprotobuf5 [2.2.0a-0.1ubuntu1]
Remv libsoundtouch1c2 [1.3.1-2]
Remv libsub-name-perl [0.04-1build1]
Remv libsys-hostname-long-perl [1.4-2]
Remv libtask-weaken-perl [1.03-1]
Remv libterm-readkey-perl [2.30-4build1]
Remv libtie-ixhash-perl [1.21-2]
Remv libtiff-tools [3.9.2-2ubuntu0.3]
Remv libtimedate-perl [1.1900-1]
Remv libtotem-plparser17 [2.30.0git201000413-0ubuntu1]
Remv liburi-perl [1.52-1]
Remv libuuid-perl [0.02-3build2]
Remv libxcb-atom1 [0.3.6-1build1]
Remv libxdmcp-dev [1:1.0.3-1]
Remv libxml-libxml-perl [1.70.ds-1]
Remv libxml-sax-perl [0.96+dfsg-2]
Remv libxml-namespacesupport-perl [1.09-3]
Remv libyaml-syck-perl [1.07-1build1]
Remv lksctp-tools [1.0.11+dfsg-1]
Remv lm-sensors [1:3.1.2-2]
Remv mkvtoolnix [3.0.0-0ubuntu1]
Remv mtools [4.0.10-1ubuntu1]
Remv net-tools [1.60-23ubuntu2]
Remv texi2html [1.82-1]
Remv sgml-data [2.0.4]
Remv xml-core [0.13]
Remv sgml-base [1.26]
Remv perl [5.10.1-8ubuntu2] [perl-modules ]
Remv perl-modules [5.10.1-8ubuntu2]
Remv policykit-desktop-privileges [0.1]
Remv poppler-utils [0.12.4-0ubuntu5]
Remv python-crypto [2.0.1+dfsg1-4ubuntu2]
Remv python-egenix-mxdatetime [3.1.3-2ubuntu1]
Remv python-egenix-mxtools [3.1.3-2ubuntu1]
Remv python-ubuntuone-storageprotocol [1.2.0-0ubuntu1]
Remv python-protobuf [2.2.0a-0.1ubuntu1]
Remv radeontool [1.6.1-0ubuntu1]
Remv rdesktop [1.6.0-2ubuntu3]
Remv shared-desktop-ontologies [0.3-1]
Remv toshset [1.75-2]
Remv vbetool [1.1-2]
Remv wireless-tools [30~pre9-3ubuntu4]
Remv x11proto-render-dev [2:0.11-1]
Remv x11proto-input-dev [2.0-2]
Remv x11proto-core-dev [7.0.16-1]
Remv x11proto-kb-dev [1.0.4-1]
Remv x11proto-randr-dev [1.3.1-1]
Remv x11proto-xinerama-dev [1.2-2]
Inst e2fslibs [1.41.11-1ubuntu2] (1.41.11-1ubuntu2.1 Ubuntu:10.04/lucid-updates)
Conf e2fslibs (1.41.11-1ubuntu2.1 Ubuntu:10.04/lucid-updates)
Inst libplymouth2 [0.8.2-2ubuntu2] (0.8.2-2ubuntu2.1 Ubuntu:10.04/lucid-updates)
Inst update-manager-core [1:0.134.10] (1:0.134.11 Ubuntu:10.04/lucid-updates)
Inst libaprutil1-dbd-sqlite3 [1.3.9+dfsg-3build1] (1.3.9+dfsg-3ubuntu0.10.04.1 Ubuntu:10.04/lucid-updates) []
Inst libaprutil1 [1.3.9+dfsg-3build1] (1.3.9+dfsg-3ubuntu0.10.04.1 Ubuntu:10.04/lucid-updates)
Inst mysql-common [5.1.41-3ubuntu12.6] (5.1.41-3ubuntu12.7 Ubuntu:10.04/lucid-updates)
Inst libmysqlclient16 [5.1.41-3ubuntu12.6] (5.1.41-3ubuntu12.7 Ubuntu:10.04/lucid-updates)
Inst libnspr4-0d [4.8.4-0ubuntu1] (4.8.6-0ubuntu0.10.04.2 Ubuntu:10.04/lucid-updates)
Inst libpackagekit-glib2-12 [0.5.7-0ubuntu2.1] (0.5.7-0ubuntu2.2 Ubuntu:10.04/lucid-updates)
Conf libplymouth2 (0.8.2-2ubuntu2.1 Ubuntu:10.04/lucid-updates)
Conf update-manager-core (1:0.134.11 Ubuntu:10.04/lucid-updates)
Conf libaprutil1 (1.3.9+dfsg-3ubuntu0.10.04.1 Ubuntu:10.04/lucid-updates)
Conf libaprutil1-dbd-sqlite3 (1.3.9+dfsg-3ubuntu0.10.04.1 Ubuntu:10.04/lucid-updates)
Conf mysql-common (5.1.41-3ubuntu12.7 Ubuntu:10.04/lucid-updates)
Conf libmysqlclient16 (5.1.41-3ubuntu12.7 Ubuntu:10.04/lucid-updates)
Conf libnspr4-0d (4.8.6-0ubuntu0.10.04.2 Ubuntu:10.04/lucid-updates)
Conf libpackagekit-glib2-12 (0.5.7-0ubuntu2.2 Ubuntu:10.04/lucid-updates)
```

---

### Post by zwobott80 on 2011-01-02
[QUOTE=libssd;10309697]Try this: sudo apt-get install --reinstall ubuntu-desktop

it shows:

Reading package lists... Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ubuntu

---

### Post by zwobott80 on 2011-01-02
[QUOTE=NT4usB;10309713]yikes...
hmmm... wonder what would happen if you apt-get install tor*.*?

no, didn't work
probably will have to go and get a new hdd, replace the old one, reinstall ubuntu, and then recover all my files...

---

### Post by libssd on 2011-01-02
Yikes indeed! NT4usB's report suggests that your only realistic option is to save your data to another device (using command line), and reinstall the OS. This is a great illustration of why it can be good to have the OS and /home on separate partitions.

---

### Post by NT4usB on 2011-01-02
> **zwobott80 said:**
> [QUOTE=libssd;10309697]Try this: sudo apt-get install --reinstall ubuntu-desktop

it shows:

Reading package lists... Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ubuntu

Tab (autocomplete) key is your friend.
Type apt-get install ubuntu then Tab twice to see all the available options.

apt-cache search is another way to see package names.

---

### Post by nice_like_rice on 2011-01-02
That's ubuntu-desktop, not ubuntu desktop.

You might want to do as was suggested, backup your /home and reinstall ubuntu.

---

### Post by zwobott80 on 2011-01-02
save your data to another device (using command line)... how could this be done ? ;)

---

### Post by zwobott80 on 2011-01-02
> **NT4usB said:**
> [QUOTE=zwobott80;10309711]

Tab (autocomplete) key is your friend.
Type apt-get install ubuntu then Tab twice to see all the available options.

apt-cache search is another way to see package names.

well, I got now a list of ubuntu-..... what next ?

---

### Post by NT4usB on 2011-01-02
> **zwobott80 said:**
> [QUOTE=NT4usB;10309733]

well, I got now a list of ubuntu-..... what next ?

Basically...
Throw packages at it until it works.
One in the list should be ubuntu-desktop. That's a start.

---

### Post by zwobott80 on 2011-01-02
after:
apt-get install ubuntu-desktop it shows:

E:Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by zwobott80 on 2011-01-02
> **NT4usB said:**
> [QUOTE=zwobott80;10309744]

Basically...
Throw packages at it until it works.
One in the list should be ubuntu-desktop. That's a start.

one of them indeed is ubuntu-desktop, what should I do next ? thank you

---

### Post by nice_like_rice on 2011-01-02
You must do

sudo apt-get install ubuntu-desktop

you forgot the sudo, and didn't have the required priveledges

---

### Post by zwobott80 on 2011-01-03
still doesn't work,
I think I will have to try to recover as much data as possible using a liveUSB, then reinstall the system... ;( <crying>

question:
is it possible to recover bookmarks from my browser (Firefox)? and how?

---

### Post by nice_like_rice on 2011-01-03
Backup your home directory, they are stored in there.

Somewhere under /home/username/.mozilla/firefox

Then in some other wierdly named directory, and then under bookmarkbackups.

---

### Post by libssd on 2011-01-03
> **zwobott80 said:**
> still doesn't work,
I think I will have to try to recover as much data as possible using a liveUSB, then reinstall the system... ;( <crying>

question:
is it possible to recover bookmarks from my browser (Firefox)? and how?
This is probably your least-bad option at this point, and booting from a live USB or DVD will provide you with a graphical user interface to find and copy your data.

Here is a tutorial for finding your Firefox preferences: [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

Since your Ubuntu install is borked, you'll need to use the approach described for FF 3.5.

---

### Post by woodmaster on 2011-01-09
pretty much did a similar thing to my PC at home, I went into synaptics and removed all packages installed that came up when I searched for "cups":-) I was trying to start over with setting up printing.  Maybe sudo apt-get install cups*.* will work?  I'll have to try the reinstall ubuntu-desktop, gdm, etc. suggestions too.

---

### Post by Krytarik on 2011-01-09
@woodmaster: Unfortunately this advice comes to late for the OP of this thread, but I can still help you!

To lookup which packages have been removed, enter in the console:
```
more /var/log/apt/history.log
```Then just re-install them with one single command:
```
sudo apt-get install PACKAGE1 PACKAGE2 ...
```You may have some experience in typing after that.;-)

Good luck!

---

