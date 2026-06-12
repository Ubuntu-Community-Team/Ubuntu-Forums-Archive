---
title: "Ubuntu apt-get purge is a bit fscked...."
date: 2010-03-20
forum: General Help
---

### Post by jbeiter on 2010-03-20
so I try to upgrade to the latest warzone using the source and start wading through dependencies.  I load bison, and flex. No problems. Then I need "sdl". So a little poking around in google find I need to install libsdl1.2-dev and libsdl1.2debian. I see some other things get loaded with the word "audio" in them and begin to grow concerned, knowing how brittle ubuntu is when it comes to sound.

Then I need to load something called theora and decide it's getting to risky and stop.

I check sound in firefox, still works so I breath a sigh of relief. Start up amarok, no sound. ****. so in trying to "back out slowly", I up-arrow to my install of the last thing and replace "install" with "purge" to get rid of the sdl stuff and hit enter.. Next thing I see is things getting removed like virtualbox, warzone, gimp, audio, WTF!!!  I hit control-C to stop the insanity..

So now I'm trying to put things back together, apt bitches about a long list of packages that are installed and no longer required.. lke libqt, amarok, vlc, rpm, alien, mailx???, along with about 45 other packages and libraries I have no clue if I need or not.

THIS FSCKING SUCKS.

Anyway out of this cluster-fk or am I looking at a re-install?

---

### Post by jbeiter on 2010-03-20
this is what apt wants to remove:

The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl librpmbuild0 libqt4-assistant debhelper
  libxcb-keysyms1 intltool-debian libxvidcore4 kdebase-runtime-data-common
  postfix mplayer-skins libsvga1 libqt4-sql-mysql libqt4-dbus
  libxine1-misc-plugins lsb-graphics kdelibs5 libxcb-xv0 lsb-desktop
  libqt4-qt3support librpmio0 amarok-common librpm0 libknotificationitem1
  po-debconf ncurses-term libcddb2 kde-icons-oxygen libexiv2-5 tremulous-data
  libdvbpsi5 liblzma0 libmail-sendmail-perl libsoprano4 libqtscript4-core
  libvlc2 gettext libqt4-webkit libqt4-gui kdelibs5-data vlc-nox cvs
  libqtcore4 libupnp3 libxcb-shape0 libqtscript4-gui libqt4-sql-sqlite
  libqtscript4-uitools lsb pax liblzo2-2 libqt4-sql libqt4-svg rpm
  libstreamanalyzer0 libiso9660-5 libqt4-xml libplasma3 libqtscript4-sql
  libqt4-network libqt4-designer kdelibs-bin libqtgui4 libqtscript4-xml
  libqt4-phonon liblua5.1-0 bsd-mailx libstreams0 vlc-plugin-pulse html2text
  vlc-data exiv2 libtag-extras1 libtar libqt3-mt mailx liblastfm0
  libqt4-script libquicktime1 lsb-core libxcb-shm0 libvlccore2 soprano-daemon
  alien libvcdinfo0 amarok-utils kdebase-runtime-data libebml0
  libqtscript4-network libsys-hostname-long-perl libmatroska0 libxine1-console
  lsb-cxx libfaac0
Use 'apt-get autoremove' to remove them.

---

