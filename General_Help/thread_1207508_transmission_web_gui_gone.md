---
title: "transmission web gui gone"
date: 2009-07-08
forum: General Help
---

### Post by shortridge11 on 2009-07-08
I was having problems with transmission's web gui, so i uninstalled using

```
sudo apt-get purge transmission
```

to completely get rid of it so i could start over again.  However, this didn't get rid of everything from transmission, so i went through and manually got rid of everything using

```
sudo locate transmission
```

to find the rest.  Before this, i had been using clutch as my web gui.  I upgraded when i found that transmission had one built in to the newer versions, but the transmission gui was a bit buggy- ie. it didn't display all buttons on the page properly, didn't display some at all, wouldn't save my preferences, etc.  So after install transmission again, i can't find any settings files, or any files at all.  I tried locating it again, and it says files are /etc but they aren't.

```

xxxxx@xxxxx:/etc/init.d$ sudo locate transmission
/etc/transmission
/etc/default/transmission-daemon
/etc/init.d/transmission-daemon
/etc/rc0.d/K20transmission-daemon
/etc/rc1.d/K20transmission-daemon
/etc/rc2.d/S20transmission-daemon
/etc/rc3.d/S20transmission-daemon
/etc/rc4.d/S20transmission-daemon
/etc/rc5.d/S20transmission-daemon
/etc/rc6.d/K20transmission-daemon
/home/xxxxx/.config/transmission
/home/xxxxx/.config/transmission-daemon
/home/xxxxx/.config/transmission-daemon/blocklists
/home/xxxxx/.config/transmission-daemon/resume
/home/xxxxx/.config/transmission-daemon/settings.json
/home/xxxxx/.config/transmission-daemon/stats.json
/home/xxxxx/.config/transmission-daemon/torrents
/home/xxx/public_html/webtopCOPY/img/transmission.png
/usr/bin/transmission
/usr/bin/transmission-daemon
/usr/bin/transmission-remote
/usr/bin/transmissioncli
/usr/lib/mime/packages/transmission-gtk
/usr/share/transmission
/usr/share/app-install/desktop/transmission.desktop
/usr/share/app-install/icons/transmission.png
/usr/share/applications/transmission.desktop
/usr/share/doc/transmission
/usr/share/doc/transmission-cli
/usr/share/doc/transmission-common
/usr/share/doc/transmission-gtk
/usr/share/doc/transmission-common/AUTHORS
/usr/share/doc/transmission-common/README
/usr/share/doc/transmission-common/README.Debian
/usr/share/doc/transmission-common/changelog.Debian.gz
/usr/share/doc/transmission-common/changelog.gz
/usr/share/doc/transmission-common/copyright
/usr/share/icons/UbuntuStudio/scalable/apps/transmission.svg
/usr/share/icons/hicolor/16x16/apps/transmission.png
/usr/share/icons/hicolor/22x22/apps/transmission.png
/usr/share/icons/hicolor/24x24/apps/transmission.png
/usr/share/icons/hicolor/32x32/apps/transmission.png
/usr/share/icons/hicolor/48x48/apps/transmission.png
/usr/share/icons/hicolor/scalable/apps/transmission.svg
/usr/share/locale-langpack/en_CA/LC_MESSAGES/transmission.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/transmission.mo
/usr/share/man/man1/transmission-daemon.1.gz
/usr/share/man/man1/transmission-remote.1.gz
/usr/share/man/man1/transmission.1.gz
/usr/share/man/man1/transmissioncli.1.gz
/usr/share/menu/transmission-gtk
/usr/share/pixmaps/transmission.png
/usr/share/pixmaps/transmission.xpm
/var/lib/dpkg/info/transmission-cli.list
/var/lib/dpkg/info/transmission-cli.md5sums
/var/lib/dpkg/info/transmission-common.list
/var/lib/dpkg/info/transmission-common.md5sums
/var/lib/dpkg/info/transmission-gtk.list
/var/lib/dpkg/info/transmission-gtk.md5sums
/var/lib/dpkg/info/transmission-gtk.postinst
/var/lib/dpkg/info/transmission-gtk.postrm
/var/lib/dpkg/info/transmission.list
xxxxx@xxxxx:/etc/init.d$


```

but when i go to /etc/init.d there isn't a file or folder named transmission-daemon.  I feel i've messed something up somewhere, but i'm not sure what i've done wrong at this point. Any ideas?

---

### Post by Cheesemill on 2009-07-08
You do know that locate searches its own database to locate files? This only gets updated once every 24 hours so will still show recently deleted files.
You can update the database using the updatedb command.

---

### Post by shortridge11 on 2009-07-08
alright, that solved the mystery of the ghost files (thanks), now how do i get around the loss of the web gui, and the lack of settings?  When i go to :9091 i get redirected to /transmission/web/
and then i get a 404 error.  Is this some kind of error with apache? because i was under the impression that transmission's web gui either had its own web server or at least piggybacked on apache somehow.

---

### Post by shortridge11 on 2009-07-09
alright, now i've got it kind of working, but when i tell it to save files somewhere it says that place doesnt exist and the torrent pauses.

---

