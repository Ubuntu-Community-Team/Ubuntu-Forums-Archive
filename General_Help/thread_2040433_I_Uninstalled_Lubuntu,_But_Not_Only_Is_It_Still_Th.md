---
title: "I Uninstalled Lubuntu, But Not Only Is It Still There: It's Pervading My Other Shells"
date: 2012-08-11
forum: General Help
---

### Post by Shie6meepo on 2012-08-11
I uninstalled Lubuntu and LXDE after realizing that I didn't need such a low-use environment and that Xubuntu and plain 'ol Ubuntu suited my tastes more. However, it still shows up in the login menu and I can still run it just fine, like it was not uninstalled. In addition, my startup and shutdown screens are the Lubuntu screens, not the Ubuntu ones.

I did not install LXDE before regular Ubuntu; it was added on through the software center. Any ideas?

---

### Post by 2F4U on 2012-08-11
Did you remove the lubuntu meta package or single packages?

---

### Post by Rex Bouwense on 2012-08-11
I am guessing that from a Ubuntu install you installed LXDE.  Is that correct ot did you install Lubuntu over the Ubuntu install?  If it is still listed on your log-in list then it was probably not installed since you can still boot into it and use it.  Which procedure did you use to un-install, terminal, Software Center, or Synaptic Package Manager?  It obviously didn't work so try again.

---

### Post by Shie6meepo on 2012-08-11
> **Rex Bouwense said:**
> I am guessing that from a Ubuntu install you installed LXDE.  Is that correct ot did you install Lubuntu over the Ubuntu install?  If it is still listed on your log-in list then it was probably not installed since you can still boot into it and use it.  Which procedure did you use to un-install, terminal, Software Center, or Synaptic Package Manager?  It obviously didn't work so try again.

I installed 12.04 LTS with a flash drive, then installed Lubuntu through the Software Center. I have since uninstalled the main Lubuntu package through the Software Center, and Software Center claims that LXDE and Lubuntu are not installed on my sytstem.

---

### Post by dummy910 on 2012-08-11
Have a look on the following page, and your answer is the code under the title:
[B]Remove Lubuntu

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

OR

just copy-paste the following into a terminal to completely remove Lubuntu from your system and go pure Gnome. (use at your own risk after backing up your data)
[/B]```
 sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview ace-of-penguins audacious audacious-plugins  audacious-plugins-data blueman chromium-browser chromium-browser-l10n  chromium-codecs-ffmpeg docbook-xml elementary-icon-theme esound-common  galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data  gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf  guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0  libabiword-2.9 libass4 libaudclient2 libaudcore1 libaudiofile1  libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0  libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9  libdvdnav4 libdvdread4 libenca0 libencode-locale-perl libept1.4.12  libesd0 libexo-1-0 libexo-common libexo-helpers libfaad2  libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1  libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4  libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8  libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common  libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl  libmcrypt4 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0  libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  libnss3-1d libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0  libpisock9 libpostproc52 librarian0 libresid-builder0c2a  libschroedinger-1.0-0 libsidplay2 libsocket6-perl libswscale2 libtar0  libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libts-0.0-0  libuniconf4.6 liburi-perl libva1 libvdpau1 libvpx1 libvte-common libvte9  libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4  libwvstreams4.6-base libwvstreams4.6-extras libwww-perl  libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin  libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl  libxml-twig-perl libxml-xpath-perl libxss1 libxvidcore4  lightdm-gtk-greeter link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lm-sensors lp-solve  lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core  lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme  lubuntu-software-center lxappearance lxappearance-obconf lxinput  lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin  lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2  mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin  pidgin-data pidgin-libnotify pidgin-microblog  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2  python-support python-xklavier rarian-compat scrot sgml-data sylpheed  sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic  system-tools-backends transmission tsconf ttf-lyx uvcdynctrl  uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts  xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad  xscreensaver xscreensaver-data && sudo apt-get install  ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g  unity-greeter 

```

---

### Post by Shie6meepo on 2012-08-12
> **dummy910 said:**
> Have a look on the following page, and your answer is the code under the title:
[B]Remove Lubuntu

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

OR

just copy-paste the following into a terminal to completely remove Lubuntu from your system and go pure Gnome. (use at your own risk after backing up your data)
[/B]```
 sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview ace-of-penguins audacious audacious-plugins  audacious-plugins-data blueman chromium-browser chromium-browser-l10n  chromium-codecs-ffmpeg docbook-xml elementary-icon-theme esound-common  galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data  gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf  guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0  libabiword-2.9 libass4 libaudclient2 libaudcore1 libaudiofile1  libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0  libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9  libdvdnav4 libdvdread4 libenca0 libencode-locale-perl libept1.4.12  libesd0 libexo-1-0 libexo-common libexo-helpers libfaad2  libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1  libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4  libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8  libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common  libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl  libmcrypt4 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0  libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  libnss3-1d libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0  libpisock9 libpostproc52 librarian0 libresid-builder0c2a  libschroedinger-1.0-0 libsidplay2 libsocket6-perl libswscale2 libtar0  libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libts-0.0-0  libuniconf4.6 liburi-perl libva1 libvdpau1 libvpx1 libvte-common libvte9  libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4  libwvstreams4.6-base libwvstreams4.6-extras libwww-perl  libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin  libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl  libxml-twig-perl libxml-xpath-perl libxss1 libxvidcore4  lightdm-gtk-greeter link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lm-sensors lp-solve  lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core  lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme  lubuntu-software-center lxappearance lxappearance-obconf lxinput  lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin  lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2  mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin  pidgin-data pidgin-libnotify pidgin-microblog  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2  python-support python-xklavier rarian-compat scrot sgml-data sylpheed  sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic  system-tools-backends transmission tsconf ttf-lyx uvcdynctrl  uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts  xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad  xscreensaver xscreensaver-data && sudo apt-get install  ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g  unity-greeter 

```
That worked for the most part, but now my startup and shutdown screen is showing the Xubuntu screen. While I like that startup screen a lot, it seems like false advertising to me, so I guess I may want to attempt the same type of code to Xubuntu. However, I don't want to go back and reinstall some of my programs like I did when not being careful last time.

---

### Post by dummy910 on 2012-08-12
let's say one wanted to install gnome display login manager, in a terminal they would type the following:

```
sudo apt-get install gdm
```then:
reboot

---

### Post by Shie6meepo on 2012-08-12
> **dummy910 said:**
> let's say one wanted to install gnome display login manager, in a terminal they would type the following:

```
sudo apt-get install gdm
```then:
reboot
Unless I'm completely off here, it's not the display manager that's the problem. I have LightDM fully functioning, but the only thing that's not right is literally the screens when you start up and shut down, where the logo and progress dots are displayed. I'm getting the Xubuntu one with a blue bar sliding back and forth and the Xubuntu logo.

---

### Post by Shie6meepo on 2012-08-14
Thanks for the help everyone, especially he who posted the system purge link. Though I did lose a few programs that I had to reinstall (my own fault), I got everything back to normal. Time to experiment with Cairo Dock and see what I can screw up there.

---

