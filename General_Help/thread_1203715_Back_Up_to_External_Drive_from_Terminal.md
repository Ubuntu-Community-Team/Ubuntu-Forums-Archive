---
title: "Back Up to External Drive from Terminal?"
date: 2009-07-03
forum: General Help
---

### Post by dedukes on 2009-07-03
So, after an upgrade debacle (power outage during upgrade from 8.10 to 9.04, and probably shouldn't have done it anyway because of the intel graphics issues), I need to do a fresh install of 8.04.

But first I need to back up my user files, preferences (or the linux equivalent of what we mac users call preferences), and whatever other system files you folks think are import.

Can someone point me to how-to for this?  I need to know the basic paths to, e.g., all Open Office documents (the vast majority of my files), etc.  Then, also, I'll need a blow by blow of exactly how to copy the files to an external drive.

Thanks!  It's been a long day.

---

### Post by Boondoklife on 2009-07-03
Here is a script that I wrote to backup a nix box. It works out great for a system restore.
```
#!/bin/bash
TIMESTAMP=`date +%H.%M.%S.%d.%m.%Y`
BACKUP_FILE=${HOSTNAME}-backup-$TIMESTAMP.tar.bz2 
BACKUP_LOCATION=/root/
EXCLUDE="--exclude=$BACKUP_LOCATION$BACKUP_FILE --exclude=/var/log/backup.log --exclude=/home --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/shares --exclude=/tmp"
tar cvpjf "$BACKUP_LOCATION$BACKUP_FILE" $EXCLUDE / > /var/log/backup.log
mv /var/log/backup.log /var/log/backup-${TIMESTAMP}.log
```Note that this does not backup the /home directory, really you should have this on a separate partition and backed up separately as it changes frequently and has YOUR profile data on it.

I personaly have a setup as follows

/ sda1 15GB
swap sda2 2GB
/home sda3 91GB

Then for backups I use a network boot and bacula to backup just the sda1 partition. The data on sda3 I have on an external drive too that I sync every now and again.

---

### Post by coffeecat on 2009-07-03
> **dedukes said:**
> So, after an upgrade debacle (power outage during upgrade from 8.10 to 9.04, and probably shouldn't have done it anyway because of the intel graphics issues), I need to do a fresh install of 8.04.

Before you commit yourself to a version 8.04 reinstall, download the 9.04 live CD and try running that live. Not all Intel chipsets are adversely affected in the 9.04 version of the xserver. Depending on your Intel chipset, you might be lucky. My old laptop has the 915GM Intel chipset and works fine (compiz and all) with Jaunty, and I'm posting from my newer laptop running Jaunty with the...

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```... graphics chipset, and that's fine too.

> **dedukes said:**
> Can someone point me to how-to for this?  I need to know the basic paths to, e.g., all Open Office documents (the vast majority of my files), etc.  Then, also, I'll need a blow by blow of exactly how to copy the files to an external drive.

Simply boot up with the live CD (9.04 for preference :wink: ). Once you've got to the live desktop, look for your Ubuntu HD partition in the Places menu and click on it. Once a Nautilus windows opens, navigate to /home/yourusername and that's where you'll find your personal files. Plug a usb drive in, which will be automounted, and drag/drop/copy away.

---

### Post by spibou on 2009-07-03
> **Boondoklife said:**
> Here is a script that I wrote to backup a nix box. It works out great for a system restore.
```
#!/bin/bash
TIMESTAMP=`date +%H.%m.%S.%d.%m.%Y`

```
I think the first %m should be %M

---

### Post by Boondoklife on 2009-07-03
> **spibou said:**
> I think the first %m should be %M

Good catch, thanks

---

### Post by blueridgedog on 2009-07-03
> **dedukes said:**
> 
But first I need to back up my user files, preferences

I use rsync for this.  Unless you have deliberately stored your files in a non-standard location, you just need to get your home directory.

Assuming you mount your external drive as /mnt/Backup, it would be:

rsync -av /home/USER/ /mnt/Backup/ 

Put your user name in place of USER and change /mnt/Backup/ to the mount point of your external drive.

---

### Post by dedukes on 2009-07-07
Thanks everyone for replying.  I'm finally giving this another go.

Coffeecat, I'm taking your advice.  

I've booted up on the 9.04 LiveCD.  I've plugged in an external drive.  The drive has mounted fine.  I can view it and its content.  But I can't drag and drop my home folder to back it up.  I get the following error:  "Error while copying.  The folder ".dbus" cannot be handled because you do not have permissions to read it."

What am I doing wrong?

---

### Post by mocha on 2009-07-07
> **dedukes said:**
> I've plugged in an external drive.  The drive has mounted fine.  I can view it and its content.  But I can't drag and drop my home folder to back it up.

Don't do this.  You'll lose your owner/permissions attributes for your files and directories and when you restore you'll be in for major headaches.  Make a Tar archive instead, like the backup script method a few posts back.

---

### Post by dedukes on 2009-07-07
Okay.  thanks.

Would you please paste the backup script you're talking about into your post?

I thought I could do it via Ubuntu LiveCD, but I'm getting a "permission denied" message.

---

### Post by Boondoklife on 2009-07-07
> **dedukes said:**
> Okay.  thanks.

Would you please paste the backup script you're talking about into your post?

I thought I could do it via Ubuntu LiveCD, but I'm getting a "permission denied" message.

If you are just trying to backup your home dir then use this:
```
sudo tar -zcvpf home_backup.tar.gz /home
```

Then move the home_backup.tar.gz to your backup medium

---

### Post by dedukes on 2009-07-07
It's looking like it didn't work.  The output is below.  Shouldn't there be a visible tar archive in my home folder in Ubuntu?

Isn't this backing up my home folder from my Ubuntu LiveCD?  As opposed to the home folder on my computer's hard drive (which would be something like /home/dare)?




tar: Removing leading `/' from member names
/home/
/home/ubuntu/
/home/ubuntu/home_backup.tar.gz
/home/ubuntu/.recently-used.xbel
/home/ubuntu/.ssh/
/home/ubuntu/.mozilla/
/home/ubuntu/.mozilla/extensions/
/home/ubuntu/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/
/home/ubuntu/.mozilla/firefox/
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/sessionstore.js
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/localstore.rdf
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/signons3.txt
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/mimeTypes.rdf
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/pluginreg.dat
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/downloads.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/urlclassifierkey3.txt
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/urlclassifier3.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/key3.db
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/cert8.db
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/secmod.db
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/FF73AA5Fd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/F13DF8E5d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/7FE4E3DAd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/BF8615B2d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/7FE3E3DAd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/6EEC73BBd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/EA1716B3d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/96FBD1DBd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/39E99F6Dd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/9DAAB6FFd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/69420059d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/660FC29Ed01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/8D0AFD86d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/4140BE4Dd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/6094FE78d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/2134BFD8d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/81F51F19d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/41B5DF59d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/18D58639d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/788CE660d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/392CA7C0d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/2508F599d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/5A5E9CDDd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/B24E2E16d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/622EE9BEd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/A1D31E17d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/8A085C7Dd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/304157E5d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/CE80EF7Fd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/BAFB14C6d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/BF158376d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/2EFD036Dd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/BD4F03D6d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/70BCC72Ad01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/FAAC7363d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/36D2CA76d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/F1700DD4d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/29005241d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/85F91836d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/14474A3Fd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/7E9D606Cd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/FA58FDE3d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/65A3A55Bd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/26012304d01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/42D1DC3Dd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/6336FDDAd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/83F71D1Bd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/43B7DD5Bd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/00D79E3Bd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/A89F4DBCd01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/7F8C2D8Ed01
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/_CACHE_003_
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/_CACHE_002_
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/_CACHE_001_
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/Cache/_CACHE_MAP_
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/cookies.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/content-prefs.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/formhistory.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/search.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/prefs.js
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/places.sqlite-journal
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/places.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/compreg.dat
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/xpti.dat
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/lock
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/extensions.ini
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/extensions.cache
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/extensions.rdf
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/permissions.sqlite
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/extensions/
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/XPC.mfasl
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/XUL.mfasl
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/compatibility.ini
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/.parentlock
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/chrome/
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/chrome/userContent-example.css
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/chrome/userChrome-example.css
/home/ubuntu/.mozilla/firefox/hfkcrxbv.default/bookmarks.html
/home/ubuntu/.mozilla/firefox/profiles.ini
/home/ubuntu/.gtk-bookmarks
/home/ubuntu/.update-notifier/
/home/ubuntu/.thumbnails/
/home/ubuntu/.thumbnails/normal/
/home/ubuntu/.thumbnails/normal/7a5ff48cf34b7cd9583f351795a7311e.png
/home/ubuntu/.thumbnails/normal/6b46380775bce7c9e240fdfc32d3ffa8.png
/home/ubuntu/.nautilus/
/home/ubuntu/.nautilus/metafiles/
/home/ubuntu/.nautilus/metafiles/computer:%2F%2F%2F.xml
/home/ubuntu/.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml
/home/ubuntu/.nautilus/metafiles/file:%2F%2F%2Fmedia.xml
/home/ubuntu/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fubuntu%2FDesktop.xml
/home/ubuntu/.cache/
/home/ubuntu/.cache/notify-osd.log
/home/ubuntu/.cache/event-sound-cache.tdb.79c740c5e3503ca2d731ea8c4a5380cd.i486-pc-linux-gnu
/home/ubuntu/.cache/compizconfig/
/home/ubuntu/.cache/compizconfig/zoom.pb
/home/ubuntu/.cache/compizconfig/workarounds.pb
/home/ubuntu/.cache/compizconfig/wobbly.pb
/home/ubuntu/.cache/compizconfig/winrules.pb
/home/ubuntu/.cache/compizconfig/widget.pb
/home/ubuntu/.cache/compizconfig/water.pb
/home/ubuntu/.cache/compizconfig/wallpaper.pb
/home/ubuntu/.cache/compizconfig/wall.pb
/home/ubuntu/.cache/compizconfig/vpswitch.pb
/home/ubuntu/.cache/compizconfig/video.pb
/home/ubuntu/.cache/compizconfig/trailfocus.pb
/home/ubuntu/.cache/compizconfig/thumbnail.pb
/home/ubuntu/.cache/compizconfig/text.pb
/home/ubuntu/.cache/compizconfig/switcher.pb
/home/ubuntu/.cache/compizconfig/svg.pb
/home/ubuntu/.cache/compizconfig/staticswitcher.pb
/home/ubuntu/.cache/compizconfig/splash.pb
/home/ubuntu/.cache/compizconfig/snap.pb
/home/ubuntu/.cache/compizconfig/showmouse.pb
/home/ubuntu/.cache/compizconfig/showdesktop.pb
/home/ubuntu/.cache/compizconfig/shift.pb
/home/ubuntu/.cache/compizconfig/shelf.pb
/home/ubuntu/.cache/compizconfig/session.pb
/home/ubuntu/.cache/compizconfig/screenshot.pb
/home/ubuntu/.cache/compizconfig/scalefilter.pb
/home/ubuntu/.cache/compizconfig/scaleaddon.pb
/home/ubuntu/.cache/compizconfig/scale.pb
/home/ubuntu/.cache/compizconfig/rotate.pb
/home/ubuntu/.cache/compizconfig/ring.pb
/home/ubuntu/.cache/compizconfig/resizeinfo.pb
/home/ubuntu/.cache/compizconfig/resize.pb
/home/ubuntu/.cache/compizconfig/regex.pb
/home/ubuntu/.cache/compizconfig/reflex.pb
/home/ubuntu/.cache/compizconfig/put.pb
/home/ubuntu/.cache/compizconfig/png.pb
/home/ubuntu/.cache/compizconfig/place.pb
/home/ubuntu/.cache/compizconfig/opacify.pb
/home/ubuntu/.cache/compizconfig/obs.pb
/home/ubuntu/.cache/compizconfig/neg.pb
/home/ubuntu/.cache/compizconfig/move.pb
/home/ubuntu/.cache/compizconfig/mousepoll.pb
/home/ubuntu/.cache/compizconfig/minimize.pb
/home/ubuntu/.cache/compizconfig/mblur.pb
/home/ubuntu/.cache/compizconfig/maximumize.pb
/home/ubuntu/.cache/compizconfig/mag.pb
/home/ubuntu/.cache/compizconfig/loginout.pb
/home/ubuntu/.cache/compizconfig/inotify.pb
/home/ubuntu/.cache/compizconfig/imgjpeg.pb
/home/ubuntu/.cache/compizconfig/group.pb
/home/ubuntu/.cache/compizconfig/grid.pb
/home/ubuntu/.cache/compizconfig/gnomecompat.pb
/home/ubuntu/.cache/compizconfig/glib.pb
/home/ubuntu/.cache/compizconfig/gears.pb
/home/ubuntu/.cache/compizconfig/fs.pb
/home/ubuntu/.cache/compizconfig/firepaint.pb
/home/ubuntu/.cache/compizconfig/fadedesktop.pb
/home/ubuntu/.cache/compizconfig/fade.pb
/home/ubuntu/.cache/compizconfig/ezoom.pb
/home/ubuntu/.cache/compizconfig/extrawm.pb
/home/ubuntu/.cache/compizconfig/expo.pb
/home/ubuntu/.cache/compizconfig/decoration.pb
/home/ubuntu/.cache/compizconfig/dbus.pb
/home/ubuntu/.cache/compizconfig/cubeaddon.pb
/home/ubuntu/.cache/compizconfig/cube.pb
/home/ubuntu/.cache/compizconfig/crashhandler.pb
/home/ubuntu/.cache/compizconfig/core.pb
/home/ubuntu/.cache/compizconfig/commands.pb
/home/ubuntu/.cache/compizconfig/colorfilter.pb
/home/ubuntu/.cache/compizconfig/clone.pb
/home/ubuntu/.cache/compizconfig/blur.pb
/home/ubuntu/.cache/compizconfig/bicubic.pb
/home/ubuntu/.cache/compizconfig/bench.pb
/home/ubuntu/.cache/compizconfig/annotate.pb
/home/ubuntu/.cache/compizconfig/animationaddon.pb
/home/ubuntu/.cache/compizconfig/animation.pb
/home/ubuntu/.cache/compizconfig/addhelper.pb
/home/ubuntu/.cache/compizconfig/3d.pb
/home/ubuntu/.gnome2_private/
/home/ubuntu/.gstreamer-0.10/
/home/ubuntu/.gstreamer-0.10/registry.i486.bin
/home/ubuntu/.gnome2/
/home/ubuntu/.gnome2/file-roller/
/home/ubuntu/.gnome2/keyrings/
/home/ubuntu/.gnome2/panel2.d/
/home/ubuntu/.gnome2/panel2.d/default/
/home/ubuntu/.gnome2/panel2.d/default/launchers/
/home/ubuntu/.gnome2/nautilus-scripts/
/home/ubuntu/.gnome2/gnome-power-manager/
/home/ubuntu/.gnome2/gnome-power-manager/profile-PA3465U-59200-3658Q-charging.csv
/home/ubuntu/.gnome2/gnome-power-manager/profile-PA3465U-59200-3658Q-discharging.csv
/home/ubuntu/.gnome2/accels/
/home/ubuntu/.gnome2/accels/nautilus
/home/ubuntu/.fontconfig/
/home/ubuntu/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
tar: /home/ubuntu/.gvfs: Cannot stat: Permission denied
/home/ubuntu/.gnupg/
/home/ubuntu/.gnupg/gpg.conf
/home/ubuntu/.pulse-cookie
/home/ubuntu/.esd_auth
/home/ubuntu/.gconfd/
/home/ubuntu/.gconfd/saved_state
/home/ubuntu/.pulse/
/home/ubuntu/.pulse/79c740c5e3503ca2d731ea8c4a5380cd:default-source
/home/ubuntu/.pulse/79c740c5e3503ca2d731ea8c4a5380cd:default-sink
/home/ubuntu/.pulse/79c740c5e3503ca2d731ea8c4a5380cd:stream-volumes.i486-pc-linux-gnu.gdbm
/home/ubuntu/.pulse/79c740c5e3503ca2d731ea8c4a5380cd:device-volumes.i486-pc-linux-gnu.gdbm
/home/ubuntu/.pulse/79c740c5e3503ca2d731ea8c4a5380cd:runtime
/home/ubuntu/.dbus/
/home/ubuntu/.dbus/session-bus/
/home/ubuntu/.dbus/session-bus/79c740c5e3503ca2d731ea8c4a5380cd-0
/home/ubuntu/Videos/
/home/ubuntu/Pictures/
/home/ubuntu/Music/
/home/ubuntu/Documents/
/home/ubuntu/Public/
/home/ubuntu/Templates/
/home/ubuntu/.config/
/home/ubuntu/.config/compiz/
/home/ubuntu/.config/compiz/compizconfig/
/home/ubuntu/.config/compiz/compizconfig/config
/home/ubuntu/.config/gnome-session/
/home/ubuntu/.config/gnome-session/saved-session/
/home/ubuntu/.config/user-dirs.locale
/home/ubuntu/.config/user-dirs.dirs
/home/ubuntu/.dmrc
/home/ubuntu/.ICEauthority
/home/ubuntu/.xsession-errors
/home/ubuntu/.Xauthority
/home/ubuntu/.sudo_as_admin_successful
/home/ubuntu/.gconf/
/home/ubuntu/.gconf/system/
/home/ubuntu/.gconf/system/networking/
/home/ubuntu/.gconf/system/networking/connections/
/home/ubuntu/.gconf/system/networking/connections/1/
/home/ubuntu/.gconf/system/networking/connections/1/connection/
/home/ubuntu/.gconf/system/networking/connections/1/connection/%gconf.xml
/home/ubuntu/.gconf/system/networking/connections/1/802-11-wireless-security/
/home/ubuntu/.gconf/system/networking/connections/1/802-11-wireless-security/%gconf.xml
/home/ubuntu/.gconf/system/networking/connections/1/802-11-wireless/
/home/ubuntu/.gconf/system/networking/connections/1/802-11-wireless/%gconf.xml
/home/ubuntu/.gconf/system/networking/connections/1/%gconf.xml
/home/ubuntu/.gconf/system/networking/connections/%gconf.xml
/home/ubuntu/.gconf/system/networking/%gconf.xml
/home/ubuntu/.gconf/system/%gconf.xml
/home/ubuntu/.gconf/desktop/
/home/ubuntu/.gconf/desktop/gnome/
/home/ubuntu/.gconf/desktop/gnome/accessibility/
/home/ubuntu/.gconf/desktop/gnome/accessibility/keyboard/
/home/ubuntu/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/accessibility/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/applications/
/home/ubuntu/.gconf/desktop/gnome/applications/window_manager/
/home/ubuntu/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/applications/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/%gconf.xml
/home/ubuntu/.gconf/desktop/%gconf.xml
/home/ubuntu/.gconf/apps/
/home/ubuntu/.gconf/apps/file-roller/
/home/ubuntu/.gconf/apps/file-roller/dialogs/
/home/ubuntu/.gconf/apps/file-roller/dialogs/batch-add/
/home/ubuntu/.gconf/apps/file-roller/dialogs/batch-add/%gconf.xml
/home/ubuntu/.gconf/apps/file-roller/dialogs/%gconf.xml
/home/ubuntu/.gconf/apps/file-roller/general/
/home/ubuntu/.gconf/apps/file-roller/general/%gconf.xml
/home/ubuntu/.gconf/apps/file-roller/listing/
/home/ubuntu/.gconf/apps/file-roller/listing/%gconf.xml
/home/ubuntu/.gconf/apps/file-roller/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-terminal/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/Default/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-terminal/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/
/home/ubuntu/.gconf/apps/nautilus/preferences/
/home/ubuntu/.gconf/apps/nautilus/preferences/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/%gconf.xml
/home/ubuntu/.gconf/apps/nm-applet/
/home/ubuntu/.gconf/apps/nm-applet/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/
/home/ubuntu/.gconf/apps/compiz/general/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/options/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/general/allscreens/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/general/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/
/home/ubuntu/.gconf/apps/evolution/calendar/
/home/ubuntu/.gconf/apps/evolution/calendar/notify/
/home/ubuntu/.gconf/apps/evolution/calendar/notify/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/calendar/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-power-manager/
/home/ubuntu/.gconf/apps/gnome-power-manager/general/
/home/ubuntu/.gconf/apps/gnome-power-manager/general/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-power-manager/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-screensaver/
/home/ubuntu/.gconf/apps/gnome-screensaver/%gconf.xml
/home/ubuntu/.gconf/apps/panel/
/home/ubuntu/.gconf/apps/panel/toplevels/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/background/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/background/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/background/
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/background/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/%gconf.xml
/home/ubuntu/.gconf/apps/panel/general/
/home/ubuntu/.gconf/apps/panel/general/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/
/home/ubuntu/.gconf/apps/panel/objects/menu_bar_screen0/
/home/ubuntu/.gconf/apps/panel/objects/menu_bar_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/browser_launcher_screen0/
/home/ubuntu/.gconf/apps/panel/objects/browser_launcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/email_launcher_screen0/
/home/ubuntu/.gconf/apps/panel/objects/email_launcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/yelp_launcher_screen0/
/home/ubuntu/.gconf/apps/panel/objects/yelp_launcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/clock_separator_screen0/
/home/ubuntu/.gconf/apps/panel/objects/clock_separator_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/
/home/ubuntu/.gconf/apps/panel/applets/mixer_screen0/
/home/ubuntu/.gconf/apps/panel/applets/mixer_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/notification_area_screen0/
/home/ubuntu/.gconf/apps/panel/applets/notification_area_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/indicator_applet_screen0/
/home/ubuntu/.gconf/apps/panel/applets/indicator_applet_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/show_desktop_button_screen0/
/home/ubuntu/.gconf/apps/panel/applets/show_desktop_button_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/trashapplet_screen0/
/home/ubuntu/.gconf/apps/panel/applets/trashapplet_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/%gconf.xml
/home/ubuntu/.gconf/apps/panel/global/
/home/ubuntu/.gconf/apps/panel/global/%gconf.xml
/home/ubuntu/.gconf/apps/panel/%gconf.xml
/home/ubuntu/.gconf/apps/%gconf.xml
/home/ubuntu/Desktop/
/home/ubuntu/Desktop/examples.desktop
/home/ubuntu/Desktop/ubiquity-gtkui.desktop
/home/ubuntu/.profile
/home/ubuntu/.bashrc
/home/ubuntu/.bash_logout
tar: Error exit delayed from previous errors

---

### Post by Boondoklife on 2009-07-07
The tar file will be where ever you ran the command from, but keep in mind you should not run this while in the /home dir or any of its subdirectories.

---

### Post by dedukes on 2009-07-07
thanks.

but do you see how the home directory being archived is /home/ubunut/?

isn't that the liveCD from which i'm running Ubuntu?

the home directory i need to back up is my computer hard drive, which should be /home/dare/?  no?  "dare" is my login usual login.

---

### Post by Boondoklife on 2009-07-07
What I gave you would be run from the pc when it is in the ubuntu environment you installed, If you can not boot that and are wanting to just backup then you will need to first mount the drive and then change the /home to the actual mounted location /media/disk1/home or what ever it is.

---

### Post by dedukes on 2009-07-07
Hey, Boondoklife.  Thanks for your patience.  I'm very dumb when it comes to the terminal.  I'm running a LiveCD of 9.04 because my 8.10 got corrupted during upgrade.  

So would you please give me the exact commands to change directories from my ubuntu livecd to my regular hard drive home directory?

---

### Post by Boondoklife on 2009-07-07
Would be happy to but I am not infront of your computer so I have no way to know what exactly it will say.

Try browsing to your home dir that has your name and then copy the path and use that.

---

### Post by blueridgedog on 2009-07-07
> **dedukes said:**
> Hey, Boondoklife.  Thanks for your patience.  I'm very dumb when it comes to the terminal.  I'm running a LiveCD of 9.04 because my 8.10 got corrupted during upgrade.  

So would you please give me the exact commands to change directories from my ubuntu livecd to my regular hard drive home directory?

If you post the output of:

```
sudo fdisk -l 
```

and 
```

mount
```

We can determine where your internal hard drive is mounted and give you some exact commands to make a backup copy.  Do you have a USB drive or flash stick to store your backup on once made?  If so, having it plugged in when you run these commands will help even more.

---

