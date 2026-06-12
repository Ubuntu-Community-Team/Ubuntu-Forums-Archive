---
title: "Xsession problem."
date: 2012-01-17
forum: General Help
---

### Post by HHx66 on 2012-01-17
Not sure how to fix this, but originally I had Xubuntu installed on this system, then I decided to move to Lubuntu/LXDE, I used the command off of psychocats.net:

```
sudo apt-get remove acpi-support acpid aisleriot app-install-data app-install-data-partner apt-xapian-index apturl apturl-common avahi-autoipd bison blueman bluez-alsa bluez-cups brltty brltty-x11 c2esp catfish cups-bsd dc dmz-cursor-theme doc-base espeak espeak-data exiv2 exo-utils firefox firefox-globalmenu firefox-gnome-support flex foo2zjs gamin gcalctool gcc gcc-4.6 ghostscript-x gigolo gimp gimp-data gir1.2-gconf-2.0 gir1.2-gmenu-3.0 gir1.2-launchpad-integration-3.0 gmusicbrowser gnome-accessibility-themes gnome-codec-install gnome-games-common gnome-mahjongg gnome-menus gnome-sudoku gnomine gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gthumb gthumb-data gtk2-engines-xfce guile-1.8-libs hplip hplip-cups hplip-data ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table im-switch indicator-application-gtk2 indicator-messages-gtk2 indicator-sound indicator-sound-gtk2 inputattach kerneloops-daemon lftp libao-common libao4 libasound2-plugins libaudio-scrobbler-perl libavahi-gobject0 libbabl-0.0-0 libbrlapi0.5 libc-dev-bin libc6-dev libclutter-1.0-0 libclutter-1.0-common libclutter-gtk-1.0-0 libcogl-common libcogl5 libconfig-inifiles-perl libcrypt-passwdmd5-perl libdotconf1.0 libespeak1 libexiv2-10 libfile-copy-recursive-perl libgamin0 libgarcon-1-0 libgarcon-common libgd2-xpm libgegl-0.0-0 libgimp2.0 libgnome-menu-3-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgomp1 libgstreamer-perl libgtk-vnc-2.0-0 libgtk2-notify-perl libgtk2-trayicon-perl libgvnc-1.0-0 libibus-1.0-0 libido-0.1-0 libido3-0.1-0 libilmbase6 libjson-glib-1.0-0 libkeybinder0 liblightdm-gobject-1-0 libmad0 libmng1 libnotify-bin libopencc1 libopenexr6 libotr2 libpulse-mainloop-glib0 libquadmath0 libsane-hpaio libsexy2 libspeechd2 libspeexdsp1 libtagc0 libthunarx-2-0 libtumbler-1-0 libunique-1.0-0 libutempter0 libuuid-perl libwnck-common libwnck22 libxp6 libxres1 libyaml-tiny-perl lightdm lightdm-gtk-greeter linux-libc-dev m4 make mpg321 mscompress murrine-themes onboard oneconf openprinting-ppds orage parole pastebinit pidgin-otr pinyin-database pkg-config plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text ptouch-driver pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils pxljr python-configobj python-gconf python-ibus python-imaging python-openssl python-pam python-pexpect python-piston-mini-client python-serial python-twisted-bin python-twisted-core python-twisted-web python-virtkey python-webkit quadrapassel radeontool rastertosag-gdi rdesktop rfkill ristretto rtkit sane-utils screensaver-default-images software-center speech-dispatcher splix syslinux syslinux-common tango-icon-theme tango-icon-theme-common tcl8.5 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird thunderbird-globalmenu toshset ttf-droid ttf-opensymbol tumbler tumbler-common ubufox ubuntu-sso-client unity-greeter update-inetd usb-creator-common usb-creator-gtk vinagre xbitmaps xchat xchat-common xcursor-themes xdg-user-dirs-gtk xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfdesktop4 xfdesktop4-data xfwm4 xfwm4-themes xscreensaver-gl xterm xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers xul-ext-ubufox zeitgeist-core zenity zenity-common && sudo apt-get install lubuntu-desktop

```

Everything works fine, but when I boot up I get this little window after I login:

```
xsession: unable to launch "xubuntu" X session --- "xubuntu" not found; falling back to default session
```

Then it loads up the LXDE desktop and everything works. How can I fix this?

---

### Post by raja.genupula on 2012-01-17
> I had Xubuntu installed on this system, then I decided to move to Lubuntu/LXDE

you have to change your default boot session to LXDE  i think . check it out.

---

