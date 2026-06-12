---
title: "Strange Problem: Lost my GUI?"
date: 2009-12-15
forum: General Help
---

### Post by Cornova on 2009-12-15
Update: The "FSCK" command seemed to solve the problem, although everytime I think it is fixed something comes up, could be some odd power fluctuation on the motherboard or something.


I have a very strange problem and will attempt to be concise and make sense with this thread:

A couple months ago I had a strange issue with GRUB [which I posted about](http://ubuntuforums.org/showthread.php?t=1297686). It was due to my dual boot (XP/Ubuntu on seperate disks) XP disk showing signs of eminent failure and therefore causing the weird GRUB errors. Eventually it simply started working again as though there was no problem after I backed up everything by moving the important files to my Ubuntu drive incase the XP drive failed.

Fast forward to last night, I had to do some work in the room where the PC is located, so unhooked everything and placed it in another room. When finished I booted up and got this same behavior with the motherboard screen sticking and then getting GRUB errors, so I figured here we go again.

After restarting over and over knowing eventually it would load the GRUB list, I boot into XP and the disk checker starts up with those "deleting index entry" and "USN Journal Verification" messages. OK fine, I've seen this before. I get into XP and just use as normal when all the sudden I get the BS of Death about some memory problem. After rebooting I put in my password and my desktop is different and all my files are gone! It was as though I did a complete reinstall but that wasn't the case since the space on the HD hadn't changed, so my files were somewhere...

Couldn't find the files so I thought, "OK XP drive is just going to fail, no problem I'll simply quit using it in favor of Ubuntu." So I go into Ubuntu, open up the XP drive to find my files so I can copy anything new that was added since my last periodic backup. And I ended up finding my files in some weird "found.001" folder at the root. So I copied everything over to Ubuntu drive.

After this I was just fiddling around listening to music, organizing the moved files etc, when I decided to use Amarok instead of that default player. Amarok gave me some KDE error (I use Gnome). Had to force quit Amarok though the song kept playing until it finished. Then the GUI started acting weird. I tried to shut down the PC but when you get that "system will shut down in X seconds" I couldn't actually see the message or buttons so I waited until the countdown was over, when it said Amarok was still open and I force quit it, the PC shuts down...

After selecting Ubuntu the weirdness begins. I tried to handwrite some of the errors after the filesystem check:

> 
"Could not update ICEauthority file /var/lib/gdm/.ICEauthority"

"There is a problem with the configuration server. (/usr./lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

"Install problem!" (this was in a corner pop-up box after a restart where the login GUI was blue and white which is odd since I was using brown/orange, I couldn't write the entire message fast enough before it poofed)

"Mount of file system failed.
A  maintenance shell will now be started.
Control-D will now terminate this shell and retry."

"fsck.ext: error while loading shared library: /lib/libc2p.so.2: cannot read file data: input/ouput error"


At this point the strange errors have for the most part stopped and I am left with either the login screen in GUI form, to which I can select my name, type password and click enter. Or it looks like the terminal and I type in username and then type the password. Both result in having a terminal like screen where the prompt is root@myname-desktop:~#

The only other information that may make sense of this is that a few days ago after the update manager ran, there were a bunch of updates with KDE in the name, though again I use Gnome, so I suspect something is wrong with the GUI? Because it's like I am completely booted and can do whatever, but no GUI.  Everytime I reboot it does goes through the filesystem check process.

I hope this makes some kind of sense. :(

---

### Post by greg963 on 2009-12-15
Well first, a bad drive in windows is for some odd reason contagious, the only explanation I know for that is that it is windows.
Second, I think you are probably getting a filesystem error when the filesystem check runs.  It is likely that you are then being dropped to a (root) shell to give you an opportunity to fix the problem. from that point you can try just typing "exit" and your computer may boot normally, but you probably wnat to try to fix the file system first. Try to catch the error, and then google for the fix.

---

### Post by john newbuntu on 2009-12-15
These appear to be symptoms of bad sector(s) in the disk drive.  But to check that, boot from a Live CD and open a terminal.  Type:
```
sudo e2fsck -C0 -p -f -v /dev/sda2
```(Now replace /dev/sda2 with the partition where your linux root partition is mounted)
See what error you get.  If you have a damaged superblock, you may be able to fix it, although, if you have several bad sectors, it may be good to replace the drive.

---

### Post by daenoid on 2009-12-15
You may want to consider just removing your current install of Gnome and the KDE packages that came with Amarok. Since your system is at least dropping you into a shell you should still be able to work with aptitude to change installed software.

```
sudo apt-get remove ubuntu-desktop
```
That command will effectively remove GNOME and ALL of the applications associated with the Ubuntu Desktop experience. If you're not sure what's going to happen from running that command then you probably shouldn't do it.

However, you may be able to clear out your GNOME configuration. If you cd into your home directory you'll find a .gconf file that houses all the relevant config information for GNOME. Simply:
```
mv .gconf gconf-bak
```

A new .gconf file will be created whenever you try to login again. This might solve one of the problems but not your filesystem situation.

Good luck.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
sudo apt-get remove ubuntu-desktop Will not remove Gnome. (K)(X)Ubuntu-desktop are meta packages, they reference everything that needed for that particular desktop environment. 

If you truly want to uninstall and reinstall gnome you need to run this command (this is for 9.10, the command is a little different for other releases):
```

sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity

```Then run 
```

sudo apt-get install ubuntu-desktop

```I don't know that this would solve your problem though.

---

