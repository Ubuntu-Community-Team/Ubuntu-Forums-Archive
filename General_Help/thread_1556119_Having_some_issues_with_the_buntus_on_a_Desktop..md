---
title: "Having some issues with the *buntus on a Desktop."
date: 2010-08-19
forum: General Help
---

### Post by kaldor on 2010-08-19
Posted this a while ago, but here I go again...

I have a "workstation" set up that I use strictly for work. I can't run any versions of Ubuntu or derivatives (mint etc) without a load of lag. I want to use Ubuntu on my work-based machine. I can't tolerate waiting 10 seconds for a right-click menu to pop up, or waiting 10 seconds for a window to minimize/maximize/close. 

I decided to remove Fedora (I don't trust updates) from it and put Lucid back on and find the root of the problem. I am currently removing all the Ubuntu One stuff and Gwibber, etc. This issue only sprouted up at Karmic. Jaunty and below work wonderfully. 

So, here are the symptoms. Help me out here!

-Fast boot, fast login, but very slow responsiveness.

-Box makes a lot of noise as if it's choking whenever I do something. Like I said, aside from the Ubuntu family, no other OS has this problem.

-Cold starting a program takes *so* long by today's standards. It's like using Windows Vista on a laptop from 2002. 

-Mouse very often lags across the screen. Getting from one end of a 15 inch monitor to another shouldn't be this hard! And like stated before, the computer makes a lot of noise even when moving the mouse.

Specs..

512 MB RAM
2.5 Ghz intel processor
Intel graphics (forget which card, but I will check later if needed. Couldn't use the desktop to check it; too slow).

---

### Post by dcollier on 2010-08-19
Are you using a 32bit or 64bit version of Ubuntu?

---

### Post by kaldor on 2010-08-19
> **dcollier said:**
> Are you using a 32bit or 64bit version of Ubuntu?

32 bit; not really a need to use 64 bit on a machine with my specs :)

---

### Post by Redblade20XX on 2010-08-19
Maybe it has something to do with an overheating GPU if the box is making noise. Have you tried any other non-linux oses and have the same problem?

---

### Post by kaldor on 2010-08-19
> **Redblade20XX said:**
> Maybe it has something to do with an overheating GPU if the box is making noise. Have you tried any other non-linux oses and have the same problem?

Came with Windows XP, but I ditched it. It had no problems. Even OpenSolaris (which is a resource hog) didn't have the problems when I tested that out. Fedora 13 ran smoothly, but like I said I did not trust the updates. OpenSUSE was great too, but zypper kept getting messed up. Mint and Ubuntu both have this issue, and only Since Karmic (Ubuntu 9.10/Mint 8 )

---

### Post by linux18 on 2010-08-19
if you don't mind a reinstall:
[http://www.mediafire.com/?bsfru0tqfdgls](http://www.mediafire.com/?bsfru0tqfdgls)
just download all 4 pieces and unzip, it will turn into an iso 
this is a custom ubuntu I'm working on, still early in developement, but capable of running in 56 MB of ram with a full GUI. If your problem persists with this, then its the ubuntu distro itself and some incompatibility somewhere

EDIT: also try this on a live cd:
[http://www.mediafire.com/?uiidi4woovo3x](http://www.mediafire.com/?uiidi4woovo3x)
it a super custom xubuntu 6.06 with debian tweaks, so you can really tell if this came from 9.10-10.04 or there is some bad ram or a bad fan

---

### Post by kaldor on 2010-08-19
> **linux18 said:**
> if you don't mind a reinstall:
[http://www.mediafire.com/?bsfru0tqfdgls](http://www.mediafire.com/?bsfru0tqfdgls)
just download all 4 pieces and unzip, it will turn into an iso 
this is a custom ubuntu I'm working on, still early in developement, but capable of running in 56 MB of ram with a full GUI. If your problem persists with this, then its the ubuntu distro itself and some incompatibility somewhere

Would prefer to stick to an official LTS, but I might look at it for other machines or in a VM :)

---

### Post by linux18 on 2010-08-19
> **kaldor said:**
> Would prefer to stick to an official LTS, but I might look at it for other machines or in a VM :)
you can try it live, just to see wether or not its the current configuration or a hardware issue.

---

### Post by Redblade20XX on 2010-08-19
Also giving us the graphics driver details would be helpful,

---

### Post by kaldor on 2010-08-19
> **Redblade20XX said:**
> Also giving us the graphics driver details would be helpful,

Lspci gives "Intel Corp. 82945G/GZ Integrated Graphics Controlled (rev 02)"

---

### Post by mastablasta on 2010-08-19
You could try Debian. It's quite fast. I htink it has a bit older kernel, so maybe your issue won't be there. you could also try the testing version to see if this issue pops out there as well.

---

### Post by kaldor on 2010-08-19
> **mastablasta said:**
> You could try Debian. It's quite fast. I htink it has a bit older kernel, so maybe your issue won't be there. you could also try the testing version to see if this issue pops out there as well.

Would rather stick with what I have right now; don't want to go burning any more discs with this slow internet connection :(

Also, older kernel doesn't really seem to matter.. doesn't the latest Fedora + all updates have the same kernel?

---

### Post by linux18 on 2010-08-19
> **kaldor said:**
> 

Also, older kernel doesn't really seem to matter.. doesn't the latest Fedora + all updates have the same kernel?
yes it does, so you may need to download and burn/unetbootin an iso to test wether or not it ubuntu or thr hardware and mines a smaller download (366 MB)
and i only get 88KBps down speed, so slow internet is no excuse

---

### Post by kaldor on 2010-08-19
Wow. I removed all of the new stuff from Karmic-Lucid (Ubuntu One, Music store, gwibber, and all that) and Ubuntu now runs much, much better even with compiz running...

Still not perfect, but did Lucid really add THAT much bloat?

---

### Post by linux18 on 2010-08-19
here is the bloat removed from my version compared to regular 10.04 

xubuntu:
```
 a2ps 
abiword 
abiword-common 
abiword-plugin-grammar 
abiword-plugin-mathview 
aisleriot 
app-install-data 
apport 
apport-gtk 
aspell 
aspell-en 
bc 
bluez 
bluez-cups 
bogofilter 
bogofilter-bdb 
bogofilter-common 
brasero 
brasero-common 
byobu 
catfish 
command-not-found 
command-not-found-data 
cups 
cups-bsd 
cups-client 
cups-common 
cups-driver-gutenprint 
dictionaries-common 
dmz-cursor-theme 
doc-base 
espeak 
espeak-data 
evince 
exaile 
firefox 
firefox-branding 
firefox-gnome-support 
foo2zjs 
foomatic-db 
foomatic-db-engine 
foomatic-filters 
gcalctool 
gdb 
ghostscript 
ghostscript-cups 
ghostscript-x 
gimp 
gimp-data 
gimp-help-common 
gimp-help-en 
gnome-accessibility-themes 
gnome-doc-utils 
gnome-games-common 
gnome-mag 
gnome-mahjongg 
gnome-orca 
gnome-sudoku 
gnome-user-guide 
gnomine 
gnumeric 
gnumeric-common 
gnumeric-doc 
gucharmap 
guile-1.8-libs 
gvfs-backends 
hpijs 
hplip 
hplip-data 
language-pack-ar 
language-pack-ar-base 
language-pack-bn 
language-pack-bn-base 
language-pack-de 
language-pack-de-base 
language-pack-en 
language-pack-en-base 
language-pack-es 
language-pack-es-base 
language-pack-fr 
language-pack-fr-base 
language-pack-gnome-ar 
language-pack-gnome-ar-base 
language-pack-gnome-bn 
language-pack-gnome-bn-base 
language-pack-gnome-de 
language-pack-gnome-de-base 
language-pack-gnome-en 
language-pack-gnome-en-base 
language-pack-gnome-es 
language-pack-gnome-es-base 
language-pack-gnome-fr 
language-pack-gnome-fr-base 
language-pack-gnome-hi 
language-pack-gnome-hi-base 
language-pack-gnome-ja 
language-pack-gnome-ja-base 
language-pack-gnome-pt 
language-pack-gnome-pt-base 
language-pack-gnome-ru 
language-pack-gnome-ru-base 
language-pack-gnome-xh 
language-pack-gnome-xh-base 
language-pack-hi 
language-pack-hi-base 
language-pack-ja 
language-pack-ja-base 
language-pack-pt 
language-pack-pt-base 
language-pack-ru 
language-pack-ru-base 
libabiword-2.8 
libbrasero-media0 
libespeak1 
libgimp2.0 
libgnomevfs2-extra 
libgoffice-0.8-8 
libgs8 
libgucharmap7 
libgutenprint2 
liblink-grammar4 
liblouis-data 
liblouis0 
libpoppler-glib4 
libpoppler5 
libpurple0 
libsane 
libscim8c2a 
libsmbclient 
libspectre1 
link-grammar-dictionaries-en 
miscfiles 
modemmanager 
mousepad 
murrine-themes 
myspell-en-au 
myspell-en-gb 
myspell-en-us 
myspell-en-za 
myspell-es 
myspell-fr 
myspell-pt 
myspell-pt-br 
myspell-pt-pt 
myspell-ru 
myspell-xh 
notify-osd-icons 
onboard 
openprinting-ppds 
orage 
pidgin 
pidgin-data 
pidgin-libnotify 
pidgin-otr 
pnm2ppa 
poppler-utils 
pxljr 
python-louis 
python-smbc 
python-speechd 
quadrapassel 
ristretto 
samba-common 
samba-common-bin 
sane-utils 
scim 
scim-bridge-agent 
scim-bridge-client-gtk 
scim-gtk2-immodule 
scim-modules-socket 
screen 
screensaver-default-images 
simple-scan 
smbclient 
software-center 
speech-dispatcher 
splix 
system-config-printer-common 
system-config-printer-gnome 
tango-icon-theme 
tango-icon-theme-common 
thunderbird 
thunderbird-locale-ar 
thunderbird-locale-de 
thunderbird-locale-fr 
thunderbird-locale-ja 
thunderbird-locale-ru 
totem 
totem-common 
totem-mozilla 
totem-plugins 
transmission-common 
transmission-gtk 
ttf-freefont 
ttf-indic-fonts-core 
ttf-khmeros-core 
ttf-liberation 
ttf-lyx 
ttf-takao-pgothic 
ttf-thai-tlwg 
ttf-unfonts-core 
ttf-wqy-microhei 
ubiquity-slideshow-xubuntu 
ubufox 
vim-runtime 
vinagre 
w3m 
wodim 
x11-apps 
xchat 
xchat-common 
xcursor-themes 
xfce4-appfinder 
xfce4-clipman-plugin 
xfce4-cpugraph-plugin 
xfce4-dict 
xfce4-fsguard-plugin 
xfce4-mailwatch-plugin 
xfce4-mount-plugin 
xfce4-places-plugin 
xfce4-screenshooter 
xfce4-terminal 
xfce4-verve-plugin 
xfce4-weather-plugin 
xfce4-xkb-plugin 
xfonts-75dpi 
xfprint4 
xfswitch-plugin 
xfwm4-themes 
xorg 
xscreensaver 
xscreensaver-data 
xscreensaver-gl 
xubuntu-artwork 
xubuntu-default-settings 
xubuntu-desktop 
xubuntu-docs 
xubuntu-icon-theme 
xubuntu-wallpapers 
xulrunner-1.9.2 
yelp 
zenity 

libgtkspell0
libots0
libgstfarsight0.10-0
libwps-0.1-1
libgegl-0.0-0
tk8.4
libgtk-vnc-1.0-0
libwbclient0
libloudmouth1-0
libxss1
libtelepathy-glib0
libgc1c2
libtotem-plparser17
libkpathsea5
libslp1
libimobiledevice0
libotr2
libindicate-gtk2
libavahi-ui0
libcupsmime1
libieee1284-3
libspeechd2
libcupsdriver1
libevview2
libportaudio2
libevent-1.4-2
libsilc-1.1-2
libclutter-gtk-0.10-0
libcdio-paranoia0
libwpg-0.1-1
libsilcclient-1.1-3
libxmlrpc-core-c3
libpsiconv6
libavahi-gobject0
libhpmud0
libwv-1.2-3
libaiksaurusgtk-1.2-0c2a
libijs-0.35
libmng1
libgadu3
liblircclient0
libgtkmathview0c2a
libbeagle1
libxp6
libdotconf1.0
libcupscgi1
libgphoto2-2
libarchive1
libzephyr4
libcupsppdc1
libmeanwhile1
libgnome-mag2
libgoffice-0.8-8-common
libgdata6
libcupsimage2
libclutter-1.0-0
libt1-5
libsdl1.2debian
libgdome2-cpp-smart0c2a
libcdio-cdda0
libgdata-common
libevdocument2
libsnmp15
libbabl-0.0-0
libcurl3
libgmime-2.4-2
liblzma1
libplist1
libaiksaurus-1.2-0c2a
libindicate4
libtalloc2
libgphoto2-port0
libwpd8c2a
libperl5.10
libsnmp-base
libcdio10
libgdome2-0
libsdl1.2debian-alsa
libaiksaurus-1.2-data
 
```ubuntu:
```
 aisleriot 
apport 
apport-gtk 
apturl 
aspell 
aspell-en 
bc 
bluez 
bluez-cups 
bluez-gstreamer 
bogofilter 
bogofilter-bdb 
bogofilter-common 
branding-ubuntu 
brasero 
brasero-common 
brltty 
brltty-x11 
byobu 
checkbox 
checkbox-gtk 
command-not-found 
command-not-found-data 
compiz 
compiz-core 
compiz-fusion-plugins-main 
compiz-gnome 
compiz-plugins 
compizconfig-backend-gconf 
computer-janitor 
computer-janitor-gtk 
couchdb-bin 
cups 
cups-bsd 
cups-client 
cups-common 
cups-driver-gutenprint 
desktopcouch 
dictionaries-common 
dmz-cursor-theme 
doc-base 
empathy 
empathy-common 
eog 
espeak 
espeak-data 
evince 
evolution 
evolution-common 
evolution-couchdb 
evolution-data-server 
evolution-exchange 
evolution-indicator 
evolution-plugins 
example-content 
f-spot 
firefox 
firefox-branding 
firefox-gnome-support 
foo2zjs 
foomatic-db 
foomatic-db-engine 
foomatic-filters 
gbrainy 
gcalctool 
gedit 
gedit-common 
ghostscript 
ghostscript-cups 
ghostscript-x 
gnome-accessibility-themes 
gnome-bluetooth 
gnome-codec-install 
gnome-doc-utils 
gnome-games-common 
gnome-mag 
gnome-mahjongg 
gnome-media 
gnome-media-common 
gnome-orca 
gnome-screensaver 
gnome-sudoku 
gnome-themes-selected 
gnome-themes-ubuntu 
gnome-user-guide 
gnome-user-share 
gnomine 
gsfonts 
gstreamer0.10-alsa 
gstreamer0.10-gnonlin 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-pulseaudio 
gstreamer0.10-x 
gucharmap 
guile-1.8-libs 
gvfs-backends 
gwibber 
gwibber-service 
hpijs 
hplip 
hplip-data 
humanity-icon-theme 
hunspell-en-ca 
hunspell-en-us 
indicator-me 
indicator-messages 
language-pack-de 
language-pack-de-base 
language-pack-en 
language-pack-en-base 
language-pack-es 
language-pack-es-base 
language-pack-gnome-de 
language-pack-gnome-de-base 
language-pack-gnome-en 
language-pack-gnome-en-base 
language-pack-gnome-es 
language-pack-gnome-es-base 
language-pack-gnome-pt 
language-pack-gnome-pt-base 
language-pack-gnome-xh 
language-pack-gnome-xh-base 
language-pack-pt 
language-pack-pt-base 
language-pack-xh 
language-pack-xh-base 
language-support-en 
language-support-writing-en 
libart2.0-cil 
libaspell15 
libbrasero-media0 
libcompizconfig0 
libenchant1c2a 
libespeak1 
libflickrnet2.2-cil 
libgconf2.0-cil 
libglade2.0-cil 
libglib2.0-cil 
libgmime2.4-cil 
libgnome-keyring1.0-cil 
libgnome-media0 
libgnome-vfs2.0-cil 
libgnome2.24-cil 
libgnomepanel2.24-cil 
libgnomevfs2-extra 
libgs8 
libgstfarsight0.10-0 
libgstreamer-plugins-base0.10-0 
libgtk2.0-cil 
libgtkhtml-editor0 
libgtkhtml3.14-19 
libgtkspell0 
libgutenprint2 
libhunspell-1.2-0 
liblaunchpad-integration1.0-cil 
liblouis-data 
liblouis0 
libmagickcore2-extra 
libmono-addins-gui0.2-cil 
libmono-addins0.2-cil 
libmono-cairo2.0-cil 
libmono-corlib2.0-cil 
libmono-data-tds2.0-cil 
libmono-i18n-west2.0-cil 
libmono-posix2.0-cil 
libmono-security2.0-cil 
libmono-sharpzip2.84-cil 
libmono-sqlite2.0-cil 
libmono-system-data2.0-cil 
libmono-system-runtime2.0-cil 
libmono-system-web2.0-cil 
libmono-system2.0-cil 
libmono2.0-cil 
libndesk-dbus-glib1.0-cil 
libndesk-dbus1.0-cil 
libnunit2.4-cil 
libpurple0 
libsane 
libsmbclient 
libspectre1 
libtelepathy-farsight0 
libtelepathy-glib0 
libtotem-plparser17 
libubuntuone-1.0-1 
libwebkit-1.0-2 
libwmf0.2-7 
libwmf0.2-7-gtk 
light-themes 
m17n-contrib 
m17n-db 
manpages-dev 
modemmanager 
mono-2.0-gac 
mono-gac 
mono-runtime 
mousetweaks 
myspell-en-au 
myspell-en-gb 
myspell-en-za 
nautilus-sendto 
nautilus-sendto-empathy 
nautilus-share 
notify-osd-icons 
onboard 
openoffice.org-base-core 
openoffice.org-calc 
openoffice.org-common 
openoffice.org-core 
openoffice.org-draw 
openoffice.org-emailmerge 
openoffice.org-gnome 
openoffice.org-gtk 
openoffice.org-help-en-us 
openoffice.org-impress 
openoffice.org-math 
openoffice.org-style-human 
openoffice.org-writer 
openprinting-ppds 
openssh-client 
pitivi 
pnm2ppa 
pppconfig 
pxljr 
python-aptdaemon-gtk 
python-desktopcouch 
python-desktopcouch-records 
python-farsight 
python-gst0.10 
python-gtkspell 
python-louis 
python-papyon 
python-smbc 
python-speechd 
python-telepathy 
python-ubuntuone 
python-uno 
python-webkit 
quadrapassel 
rhythmbox 
rhythmbox-plugin-cdrecorder 
rhythmbox-plugins 
rhythmbox-ubuntuone-music-store 
samba-common 
samba-common-bin 
sane-utils 
screen 
screensaver-default-images 
seahorse 
simple-scan 
smbclient 
software-center 
speech-dispatcher 
splix 
ssh-askpass-gnome 
syslinux 
system-config-printer-common 
system-config-printer-gnome 
telepathy-butterfly 
telepathy-gabble 
telepathy-haze 
telepathy-idle 
telepathy-mission-control-5 
telepathy-salut 
tomboy 
totem 
totem-common 
totem-mozilla 
totem-plugins 
transmission-common 
transmission-gtk 
ttf-indic-fonts-core 
ttf-khmeros-core 
ttf-liberation 
ttf-takao-pgothic 
ttf-thai-tlwg 
ttf-unfonts-core 
ttf-wqy-microhei 
ubiquity-slideshow-ubuntu 
ubufox 
ubuntu-artwork 
ubuntu-desktop 
ubuntu-docs 
ubuntu-mono 
ubuntu-sounds 
ubuntu-wallpapers 
ubuntuone-client 
ubuntuone-client-gnome 
uno-libs3 
ure 
usb-creator-common 
usb-creator-gtk 
vinagre 
vino 
wamerican 
wbritish 
wodim 
x11-apps 
x11-utils 
xcursor-themes 
xfonts-75dpi 
xorg 
xscreensaver-data 
xscreensaver-gl 
xulrunner-1.9.2 
yelp 

gvfs-bin
libgraphite3
libwps-0.1-1
libsdl1.2debian
tk8.4
libv4l-0
libglitz-glx1
libavc1394-0
libgtk-vnc-1.0-0
libwbclient0
libloudmouth1-0
libwavpack1
libexchange-storage1.2-3
libmtp8
libegroupwise1.2-13
librdf0
libxxf86dga1
libkpathsea5
libslp1
liboil0.3
libgtkhtml-editor-common
libcupsmime1
libdv4
libneon27-gnutls
libgpgme11
libieee1284-3
libspeechd2
gnome-session-canberra
libcupsdriver1
libevview2
libgdiplus
libportaudio2
libevent-1.4-2
libdesktopcouch-glib-1.0-2
libshout3
libsilc-1.1-2
libclutter-gtk-0.10-0
libcdio-paranoia0
libwpg-0.1-1
libsqlite0
libpoppler-glib4
libsilcclient-1.1-3
libpst4
libcryptui0
libavahi-gobject0
libgraphviz4
libopenexr6
libgnome-pilot2
libhpmud0
libcurl3
libijs-0.35
libgadu3
libiec61883-0
libgmime-2.4-2
liblircclient0
libgail-gnome-module
libbeagle1
libwebkit-1.0-common
libxp6
libgdata-google1.2-1
libdotconf1.0
libedata-book1.2-2
libhyphen0
libcaca0
libcupscgi1
libtag1c2a
libgphoto2-2
liblpint-bonobo0
libedata-cal1.2-6
libarchive1
libedit2
libzephyr4
libcupsppdc1
libaa1
libdjvulibre21
libmeanwhile1
libgnome-mag2
libmusicbrainz4c2a
gvfs-fuse
libgdata6
libcupsimage2
libclutter-1.0-0
libpth20
libraw1394-11
libpisync1
libspeex1
libgif4
libtag1-vanilla
libcdio-cdda0
libgdata-common
libevdocument2
libsnmp15
libtheora0
libgdata1.2-1
libdjvulibre-text
libebackend1.2-0
liblzma1
libilmbase6
libsdl1.2debian-pulseaudio
librasqal2
libtalloc2
libcouchdb-glib-1.0-2
libglitz1
libgphoto2-port0
libwpd8c2a
libperl5.10
libsnmp-base
libcdio10
libpisock9
libraptor1 
```is my fully compatible remix looking more appealing now :)

---

