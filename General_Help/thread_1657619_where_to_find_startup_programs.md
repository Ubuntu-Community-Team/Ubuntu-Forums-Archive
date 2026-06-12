---
title: "where to find startup programs?"
date: 2011-01-01
forum: General Help
---

### Post by BaldNomad on 2011-01-01
I have somehow gotten two instances of Mediatomb running on my Ubuntu 10.04.1 box and need some help figuring out how to get rid of one of them.

There is one copy running as a daemon on system startup - that's the one I want to keep.

There is another copy running when I log in with my user account - this is the one I want to prevent from running.

I have looked in my Startup folder in the GUI and also in my .profile script for my user account but I don't see any references to mediatomb there.  Where else should I look?

I think the daemon version is running via an entry in init.d, but other than where I've already looked I don't know how to find out how the second copy is getting initiated during login.  It only seems to show up when I log in to the GUI on Ubuntu - not when I connect to the machine remotely via SSH.

Any help is appreciated!  I can post logs or command outputs if needed...just need to know where to look!

---

### Post by westgaard on 2011-01-01
With "startup folder in the GUI" do you mean System - Preferences - Startup Applications?

---

### Post by BaldNomad on 2011-01-01
> **westgaard said:**
> With "startup folder in the GUI" do you mean System - Preferences - Startup Applications?

yes!  is there another such folder I should check?

---

### Post by QLee on 2011-01-01
[QUOTE=BaldNomad]...
There is another copy running when I log in with my user account - this is the one I want to prevent from running.

...just need to know where to look![/QUOTE]

I'm going to make a guess from the symptoms you describe.

At some point you had checked the box for "Automatically remember running programs when logging out" on the Options tab of the Startup Applications preferences sheet. Seems like that might cause the symptoms detailed. Doesn't take long to check that. If it isn't still checked, check it, then close any programs you don't want running when your user logs in and push the "Remember Currently Running Application" button to clear then unckeck it again. At least, it's an easy thing to try.

---

### Post by westgaard on 2011-01-01
You can try to check the .config/autostart-folder in your home-directory. Also, if you try 'locate mediathomb' you might find the autostart-script.

---

### Post by BaldNomad on 2011-01-01
> **westgaard said:**
> You can try to check the .config/autostart-folder in your home-directory. Also, if you try 'locate mediathomb' you might find the autostart-script.

the autostart folder looks clean - no mediatomb references there.  I ran the locate command and don't see anything suspicious there, but then I'm not really sure exactly what I'm looking for.  Command output is below:


```
dbowman@camaro:~/.config/autostart$ ls -alp
total 24
drwx------  2 dbowman dbowman 4096 2010-12-25 16:49 ./
drwxr-xr-x 13 dbowman dbowman 4096 2010-12-23 17:33 ../
-rw-r--r--  1 dbowman dbowman  336 2009-10-23 15:11 bluetooth-applet.desktop
-rw-r--r--  1 dbowman dbowman  468 2009-10-23 15:11 evolution-alarm-notify.desktop
-rw-r--r--  1 dbowman dbowman  555 2009-10-23 15:12 gnome-power-manager.desktop
-rw-r--r--  1 dbowman dbowman  491 2009-10-23 15:11 jockey-gtk.desktop
dbowman@camaro:~/.config/autostart$ locate mediatomb
/etc/mediatomb
/etc/default/mediatomb
/etc/default/mediatomb~
/etc/init.d/mediatomb
/etc/logrotate.d/mediatomb
/etc/mediatomb/config.xml
/etc/mediatomb/config.xml.dpkg-old
/etc/mediatomb/config.xml~
/etc/rc0.d/K20mediatomb
/etc/rc1.d/K20mediatomb
/etc/rc2.d/S20mediatomb
/etc/rc3.d/S20mediatomb
/etc/rc4.d/S20mediatomb
/etc/rc5.d/S20mediatomb
/etc/rc6.d/K20mediatomb
/home/dbowman/.mediatomb
/home/dbowman/.mediatomb/config.xml
/home/dbowman/.mediatomb/config.xml~
/home/dbowman/.mediatomb/mediatomb.db
/home/dbowman/.mediatomb/mediatomb.html
/home/dbowman/.mediatomb/mediatomb.html~
/home/dbowman/Desktop/mediatomb UI
/usr/bin/mediatomb
/usr/share/mediatomb
/usr/share/app-install/desktop/mediatomb.desktop
/usr/share/applications/mediatomb.desktop
/usr/share/doc/mediatomb
/usr/share/doc/mediatomb-common
/usr/share/doc/mediatomb-daemon
/usr/share/doc/mediatomb/README.Debian
/usr/share/doc/mediatomb/changelog.Debian.gz
/usr/share/doc/mediatomb/changelog.gz
/usr/share/doc/mediatomb/copyright
/usr/share/doc/mediatomb-common/README.gz
/usr/share/doc/mediatomb-common/changelog.Debian.gz
/usr/share/doc/mediatomb-common/changelog.gz
/usr/share/doc/mediatomb-common/copyright
/usr/share/doc/mediatomb-common/examples
/usr/share/doc/mediatomb-common/scripting.txt.gz
/usr/share/doc/mediatomb-common/transcoding.txt.gz
/usr/share/doc/mediatomb-common/ui.txt.gz
/usr/share/doc/mediatomb-common/examples/config.xml.gz
/usr/share/doc/mediatomb-common/examples/mediatomb-transcode
/usr/share/doc/mediatomb-daemon/README.Debian
/usr/share/doc/mediatomb-daemon/changelog.Debian.gz
/usr/share/doc/mediatomb-daemon/changelog.gz
/usr/share/doc/mediatomb-daemon/copyright
/usr/share/lintian/overrides/mediatomb
/usr/share/man/man1/mediatomb.1.gz
/usr/share/mediatomb/js
/usr/share/mediatomb/mappings.xml
/usr/share/mediatomb/mysql.sql
/usr/share/mediatomb/sqlite3.sql
/usr/share/mediatomb/web
/usr/share/mediatomb/js/common.js
/usr/share/mediatomb/js/import-dvd.js
/usr/share/mediatomb/js/import.js
/usr/share/mediatomb/js/playlists.js
/usr/share/mediatomb/web/cds.xml
/usr/share/mediatomb/web/cm.xml
/usr/share/mediatomb/web/disabled.html
/usr/share/mediatomb/web/favicon.ico
/usr/share/mediatomb/web/icons
/usr/share/mediatomb/web/index.html
/usr/share/mediatomb/web/js
/usr/share/mediatomb/web/left.html
/usr/share/mediatomb/web/main.css
/usr/share/mediatomb/web/mr_reg.xml
/usr/share/mediatomb/web/right.html
/usr/share/mediatomb/web/std_treelook.css
/usr/share/mediatomb/web/top.html
/usr/share/mediatomb/web/topleft.html
/usr/share/mediatomb/web/topright.html
/usr/share/mediatomb/web/icons/add_as_autoscan.png
/usr/share/mediatomb/web/icons/autoscan_inotify_config_folder_open.png
/usr/share/mediatomb/web/icons/autoscan_inotify_folder_open.png
/usr/share/mediatomb/web/icons/autoscan_timed_config_folder_open.png
/usr/share/mediatomb/web/icons/autoscan_timed_folder_open.png
/usr/share/mediatomb/web/icons/blank.gif
/usr/share/mediatomb/web/icons/blank.png
/usr/share/mediatomb/web/icons/document-new.png
/usr/share/mediatomb/web/icons/film.png
/usr/share/mediatomb/web/icons/folder_new.png
/usr/share/mediatomb/web/icons/folder_open.png
/usr/share/mediatomb/web/icons/go-first.png
/usr/share/mediatomb/web/icons/go-last.png
/usr/share/mediatomb/web/icons/go-next.png
/usr/share/mediatomb/web/icons/go-previous.png
/usr/share/mediatomb/web/icons/mediatomb.png
/usr/share/mediatomb/web/icons/mt-icon120.bmp
/usr/share/mediatomb/web/icons/mt-icon120.jpg
/usr/share/mediatomb/web/icons/mt-icon120.png
/usr/share/mediatomb/web/icons/mt-icon32.bmp
/usr/share/mediatomb/web/icons/mt-icon32.jpg
/usr/share/mediatomb/web/icons/mt-icon32.png
/usr/share/mediatomb/web/icons/mt-icon48.bmp
/usr/share/mediatomb/web/icons/mt-icon48.jpg
/usr/share/mediatomb/web/icons/mt-icon48.png
/usr/share/mediatomb/web/icons/nanotree
/usr/share/mediatomb/web/icons/remove_all.png
/usr/share/mediatomb/web/icons/remove_autoscan.png
/usr/share/mediatomb/web/icons/remove_this.png
/usr/share/mediatomb/web/icons/status.png
/usr/share/mediatomb/web/icons/status_loading.png
/usr/share/mediatomb/web/icons/status_updates_pending.png
/usr/share/mediatomb/web/icons/stock-add.png
/usr/share/mediatomb/web/icons/stock_edit.png
/usr/share/mediatomb/web/icons/stock_exit.png
/usr/share/mediatomb/web/icons/nanotree/images
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_inotify_config_folder_closed.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_inotify_config_folder_open.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_inotify_folder_closed.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_inotify_folder_open.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_timed_config_folder_closed.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_timed_config_folder_open.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_timed_folder_closed.png
/usr/share/mediatomb/web/icons/nanotree/images/autoscan_timed_folder_open.png
/usr/share/mediatomb/web/icons/nanotree/images/folder_closed.png
/usr/share/mediatomb/web/icons/nanotree/images/folder_open.png
/usr/share/mediatomb/web/icons/nanotree/images/lastnode.png
/usr/share/mediatomb/web/icons/nanotree/images/line.png
/usr/share/mediatomb/web/icons/nanotree/images/minus.png
/usr/share/mediatomb/web/icons/nanotree/images/minus_last.png
/usr/share/mediatomb/web/icons/nanotree/images/minus_last_no_root.png
/usr/share/mediatomb/web/icons/nanotree/images/minus_no_root.png
/usr/share/mediatomb/web/icons/nanotree/images/plus.png
/usr/share/mediatomb/web/icons/nanotree/images/plus_last.png
/usr/share/mediatomb/web/icons/nanotree/images/plus_last_no_root.png
/usr/share/mediatomb/web/icons/nanotree/images/plus_no_root.png
/usr/share/mediatomb/web/icons/nanotree/images/t.png
/usr/share/mediatomb/web/icons/nanotree/images/t_no_root.png
/usr/share/mediatomb/web/icons/nanotree/images/white.png
/usr/share/mediatomb/web/js/auth.js
/usr/share/mediatomb/web/js/autoscan.js
/usr/share/mediatomb/web/js/icons.js
/usr/share/mediatomb/web/js/iepngfix.htc
/usr/share/mediatomb/web/js/items.js
/usr/share/mediatomb/web/js/md5.js
/usr/share/mediatomb/web/js/nanotree.js
/usr/share/mediatomb/web/js/prototype.js
/usr/share/mediatomb/web/js/tasks.js
/usr/share/mediatomb/web/js/tools.js
/usr/share/mediatomb/web/js/tree.js
/usr/share/menu/mediatomb
/usr/share/pixmaps/mediatomb.png
/usr/share/pixmaps/mediatomb.xpm
/var/cache/apt/archives/mediatomb-common_0.12.0~svn2018-6ubuntu2_amd64.deb
/var/cache/apt/archives/mediatomb-daemon_0.12.0~svn2018-6ubuntu2_all.deb
/var/cache/apt/archives/mediatomb_0.12.0~svn2018-6ubuntu2_all.deb
/var/lib/mediatomb
/var/lib/dpkg/info/mediatomb-common.list
/var/lib/dpkg/info/mediatomb-common.md5sums
/var/lib/dpkg/info/mediatomb-daemon.conffiles
/var/lib/dpkg/info/mediatomb-daemon.list
/var/lib/dpkg/info/mediatomb-daemon.md5sums
/var/lib/dpkg/info/mediatomb-daemon.postinst
/var/lib/dpkg/info/mediatomb-daemon.postrm
/var/lib/dpkg/info/mediatomb-daemon.preinst
/var/lib/dpkg/info/mediatomb-daemon.prerm
/var/lib/dpkg/info/mediatomb.list
/var/lib/dpkg/info/mediatomb.md5sums
/var/lib/dpkg/info/mediatomb.postinst
/var/lib/dpkg/info/mediatomb.postrm
/var/lib/mediatomb/mediatomb.db
/var/lib/mediatomb/mediatomb.db-journal
/var/lib/mediatomb/mediatomb.html
/var/lib/update-rc.d/mediatomb
/var/log/mediatomb.log
/var/log/mediatomb.log.1
/var/log/mediatomb.log.2
/var/log/mediatomb.log.3
/var/log/mediatomb.log.4
/var/log/mediatomb.log.5

```

---

### Post by BaldNomad on 2011-01-02
> **QLee said:**
> I'm going to make a guess from the symptoms you describe.

At some point you had checked the box for "Automatically remember running programs when logging out" on the Options tab of the Startup Applications preferences sheet. Seems like that might cause the symptoms detailed. Doesn't take long to check that. If it isn't still checked, check it, then close any programs you don't want running when your user logs in and push the "Remember Currently Running Application" button to clear then unckeck it again. At least, it's an easy thing to try.

thanks for the tip, tried this but it didn't help in this case.  Now it seems to be fixed after a reboot - maybe I had inadvertently started up another copy at some point while troubleshooting - I rarely reboot this machine.  Thanks to everyone for the help.

---

