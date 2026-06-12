---
title: "download APP that dont work"
date: 2012-03-08
forum: General Help
---

### Post by cold37 on 2012-03-08
i have ubuntu 11.10 why is it when i try to install something like --> sudo apt-add-repository ppa:plexydesk/plexydesk-dailybuild
sudo apt-get update
sudo apt-get install plexydesk <-- it dont work i dont see it anywheres in applications i have deen this 10 or 15 times with others and never see it or where its installed at i mean if i could see it and start it up and it dont work that be ok but too install it and never find it just upset me i put each code in one at a time and it acts like it work but nothings there.... ooh when i post it shows a smile face when i dont want it too all it is --> : p

---

### Post by sikander3786 on 2012-03-08
Please run these commands again and post the complete outputs this time:

```
sudo apt-get update
sudo apt-get install plexydesk
```

If it installed successfully, as you said, you can press the <Super> (Windows logo key) and search the Dash for 'plexydesk'. Does it show up?

---

### Post by cold37 on 2012-03-08
no its not on here ill look everywhere i just dont get i know i installed it right and its not on here:confused:

---

### Post by winh8r on 2012-03-08
You just need to go here:

[https://launchpad.net/~plexydesk/+archive/plexydesk-dailybuild/+packages]("https://launchpad.net/~plexydesk/+archive/plexydesk-dailybuild/+packages")

and select the correct .deb package for your architecture and it will be downloaded and installed for you.

I think you may have downloaded the source code package instead which needs to be built from scratch.


once it is installed it will either be in the menu or it will run from the terminal

just type 

```
plexydesk
```

and it should run.

Hope this helps.

---

### Post by jerome1232 on 2012-03-08
What does this return? Please post the output wraped in code tags (go advanved highlight all output, click the # symbol) ctrl+****+c to copy text from a terminal window.

```
sudo dpkg-query -L plexydesk
```

---

### Post by Face-Ache on 2012-04-11
Hi there

I came across this thread when i was looking for some advice on how to get PlexyDesk working in Ubuntu 11.10. I didn't want to start a new thread!

Anyway, i'm having the same issue as the OP; can't find PlexyDesk after installing - doesn't show up as an installed app in the Dash at all.

So i removed it via the Software Centre, then followed the advice of winh8r, and seem to now have PlexyDesk installed, although it still isn't showing in the Dash programs. 

From a Terminal, when i enter 'plexydesk' i get the following;
[I](plexydesk:25324): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[/I]
It then seems to load, but disappears when i close the Terminal.

When i enter what Jerome1232 has suggested, 
sudo dpkg-query -L plexydesk I get the following results in italics. So it kinda works, until i close the Terminal, and i'm not sure what i am doing wrong! Would really appreciate any help you can provide - looks like a really nice program, so would be fantastic if i could get it working.

Many thanks
Chris

[I]/.
/usr
/usr/share
/usr/share/dbus-1
/usr/share/dbus-1/services
/usr/share/dbus-1/services/org.plexydesk.social.service
/usr/share/dbus-1/services/org.plexydesk.SocialAccountsManager.service
/usr/share/applications
/usr/share/applications/plexydesk.desktop
/usr/share/plexy
/usr/share/plexy/fbjson
/usr/share/plexy/fbjson/data
/usr/share/plexy/fbjson/data/fbstatus.json
/usr/share/plexy/fbjson/data/fbinfo.json
/usr/share/plexy/skins
/usr/share/plexy/skins/widgets
/usr/share/plexy/skins/widgets/base-widget
/usr/share/plexy/skins/widgets/base-widget/pila.png
/usr/share/plexy/skins/widgets/base-widget/filmback.png
/usr/share/plexy/skins/widgets/base-widget/xine.png
/usr/share/plexy/skins/widgets/base-widget/icon.png
/usr/share/plexy/skins/widgets/base-widget/schedule.png
/usr/share/plexy/skins/default
/usr/share/plexy/skins/default/clock
/usr/share/plexy/skins/default/clock/hour-hand.png
/usr/share/plexy/skins/default/clock/minute-hand-long.png
/usr/share/plexy/skins/default/clock/clock-shadow.png
/usr/share/plexy/skins/default/clock/date_field.png
/usr/share/plexy/skins/default/clock/mask.png
/usr/share/plexy/skins/default/clock/gloss.png
/usr/share/plexy/skins/default/clock/second-hand-long.png
/usr/share/plexy/skins/default/clock/face.png
/usr/share/plexy/skins/default/clock/thedot.png
/usr/share/plexy/skins/default/clock/second-hand.png
/usr/share/plexy/skins/default/clock/background.png
/usr/share/plexy/skins/default/clock/hour-hand-long.png
/usr/share/plexy/skins/default/clock/minute-hand.png
/usr/share/plexy/skins/default/cpu
/usr/share/plexy/skins/default/cpu/mask.png
/usr/share/plexy/skins/default/cpu/gloss.png
/usr/share/plexy/skins/default/cpu/dot.png
/usr/share/plexy/skins/default/cpu/background.png
/usr/share/plexy/skins/default/cpu/needle.png
/usr/share/plexy/skins/default/cpu/icon.png
/usr/share/plexy/skins/default/flick
/usr/share/plexy/skins/default/flick/bg-hover.png
/usr/share/plexy/skins/default/flick/bg-content.png
/usr/share/plexy/skins/default/flick/bg-top.png
/usr/share/plexy/skins/default/flick/bg-search.png
/usr/share/plexy/ext
/usr/share/plexy/ext/groups
/usr/share/plexy/ext/groups/folderwidget.desktop
/usr/share/plexy/ext/groups/clock.desktop
/usr/share/plexy/ext/groups/rest.desktop
/usr/share/plexy/ext/groups/photoframe.desktop
/usr/share/plexy/ext/groups/classic.desktop
/usr/share/plexy/ext/groups/cpu.desktop
/usr/share/plexy/ext/groups/plexydesktopview.desktop
/usr/share/plexy/ext/groups/authwidget.desktop
/usr/share/plexy/plexydesk.png
/usr/share/plexy/themepack
/usr/share/plexy/themepack/default
/usr/share/plexy/themepack/default/digitalclock
/usr/share/plexy/themepack/default/digitalclock/digitalClock.qml
/usr/share/plexy/themepack/default/resources
/usr/share/plexy/themepack/default/resources/txt.png
/usr/share/plexy/themepack/default/resources/doc.png
/usr/share/plexy/themepack/default/resources/php.png
/usr/share/plexy/themepack/default/resources/qml_widgets_background.png
/usr/share/plexy/themepack/default/resources/exe.png
/usr/share/plexy/themepack/default/resources/pdf.png
/usr/share/plexy/themepack/default/resources/config.png
/usr/share/plexy/themepack/default/resources/photo-border.png
/usr/share/plexy/themepack/default/resources/h.png
/usr/share/plexy/themepack/default/resources/package.png
/usr/share/plexy/themepack/default/resources/lnk.png
/usr/share/plexy/themepack/default/resources/background.svg
/usr/share/plexy/themepack/default/resources/default-16x9.png
/usr/share/plexy/themepack/default/resources/photo-border-shadow.png
/usr/share/plexy/themepack/default/resources/default-photo.png
/usr/share/plexy/themepack/default/resources/script.png
/usr/share/plexy/themepack/default/resources/back.png
/usr/share/plexy/themepack/default/resources/js.png
/usr/share/plexy/themepack/default/resources/panel.png
/usr/share/plexy/themepack/default/resources/rb.png
/usr/share/plexy/themepack/default/resources/html.png
/usr/share/plexy/themepack/default/resources/qml_widgets_container_background.png
/usr/share/plexy/themepack/default/resources/xml.png
/usr/share/plexy/themepack/default/resources/audio.png
/usr/share/plexy/themepack/default/resources/ppt.png
/usr/share/plexy/themepack/default/resources/img.png
/usr/share/plexy/themepack/default/resources/drop_shadow__1.png
/usr/share/plexy/themepack/default/resources/iso.png
/usr/share/plexy/themepack/default/resources/cardboard.png
/usr/share/plexy/themepack/default/resources/folder.png
/usr/share/plexy/themepack/default/resources/hdd.png
/usr/share/plexy/themepack/default/resources/obj.png
/usr/share/plexy/themepack/default/resources/odb.png
/usr/share/plexy/themepack/default/resources/busy.png
/usr/share/plexy/themepack/default/resources/la.png
/usr/share/plexy/themepack/default/resources/xls.png
/usr/share/plexy/themepack/default/resources/exec.png
/usr/share/plexy/themepack/default/resources/svg.png
/usr/share/plexy/themepack/default/resources/photo_frame_background.png
/usr/share/plexy/themepack/default/resources/py.png
/usr/share/plexy/themepack/default/resources/alt_default-4x3.png
/usr/share/plexy/themepack/default/resources/c.png
/usr/share/plexy/themepack/default/resources/url.png
/usr/share/plexy/themepack/default/resources/clock_background.png
/usr/share/plexy/themepack/default/resources/drop_shadow.png
/usr/share/plexy/themepack/default/resources/torrent.png
/usr/share/plexy/themepack/default/resources/video.png
/usr/share/plexy/themepack/default/resources/background.png
/usr/share/plexy/themepack/default/resources/archive.png
/usr/share/plexy/themepack/default/resources/unknown.png
/usr/share/plexy/themepack/default/resources/qml_widget_background.svg
/usr/share/plexy/themepack/default/resources/default-4x3.png
/usr/share/plexy/themepack/default/resources/reverse.png
/usr/share/plexy/themepack/default/resources/cpp.png
/usr/share/plexy/themepack/default/resources/java.png
/usr/share/plexy/themepack/default/resources/icon.png
/usr/share/plexy/themepack/default/resources/pl.png
/usr/share/plexy/themepack/default/resources/alt_default-16x9.png
/usr/share/plexy/themepack/default/resources/so.png
/usr/share/plexy/themepack/default/resources/box-shadow.png
/usr/share/plexy/themepack/default/folderview
/usr/share/plexy/themepack/default/folderview/resources
/usr/share/plexy/themepack/default/folderview/resources/Scripts.js
/usr/share/plexy/themepack/default/folderview/resources/Icon.qml
/usr/share/plexy/themepack/default/folderview/folderview.qml
/usr/share/plexy/themepack/default/backdrop
/usr/share/plexy/themepack/default/backdrop/RadialWaveEffect.qml
/usr/share/plexy/themepack/default/backdrop/Water.qml
/usr/share/plexy/themepack/default/backdrop/RadialWave.qml
/usr/share/plexy/themepack/default/backdrop/TestWater.qml
/usr/share/plexy/themepack/default/photoframe
/usr/share/plexy/themepack/default/photoframe/photoframe.qml
/usr/share/plexy/themepack/default/photoviewer
/usr/share/plexy/themepack/default/photoviewer/photoviewer.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/PhotoDelegate.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/BusyIndicator.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/AlbumDelegate.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/RssModel.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/ProgressBar.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/Tag.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/script
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/script/script.js
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/EditableButton.qml
/usr/share/plexy/themepack/default/photoviewer/PhotoViewerCore/Button.qml
/usr/share/plexy/themepack/default/main.cfg
/usr/share/plexy/themepack/default/welcome
/usr/share/plexy/themepack/default/welcome/welcome.qml
/usr/share/plexy/themepack/default/welcome/scripts
/usr/share/plexy/themepack/default/welcome/scripts/Scripts.js
/usr/share/plexy/themepack/default/weather
/usr/share/plexy/themepack/default/weather/weather.qml
/usr/share/plexy/themepack/default/photo
/usr/share/plexy/themepack/default/photo/photoElement.qml
/usr/share/doc
/usr/share/doc/plexydesk
/usr/share/doc/plexydesk/changelog.Debian.gz
/usr/share/doc/plexydesk/COPYING.gz
/usr/share/doc/plexydesk/README.Debian
/usr/share/doc/plexydesk/changelog.gz
/usr/share/doc/plexydesk/AUTHORS
/usr/share/doc/plexydesk/README.gz
/usr/share/doc/plexydesk/TODO
/usr/share/doc/plexydesk/copyright
/usr/bin
/usr/bin/plexypanel
/usr/bin/socialplexyaccountman
/usr/bin/socialplexydaemon
/usr/bin/plexy_json_test
/usr/bin/plexydesk
/usr/lib
/usr/lib/libwebqgv.so
/usr/lib/libplexyjson.so
/usr/lib/libmimetype.so
/usr/lib/plexyext
/usr/lib/plexyext/librestengine.so
/usr/lib/plexyext/libphotoframe.so
/usr/lib/plexyext/libclassicbackdrop.so
/usr/lib/plexyext/libplexyauth.so
/usr/lib/plexyext/libplexyclock.so
/usr/lib/plexyext/libplexydesktopview.so
/usr/lib/plexyext/libfolderwidget.so
/usr/lib/plexyext/libplexycpu.so
/usr/lib/qt4
/usr/lib/qt4/imports
/usr/lib/qt4/imports/PlexyDesk
/usr/lib/qt4/imports/PlexyDesk/FolderListModel
/usr/lib/qt4/imports/PlexyDesk/FolderListModel/qmldir
/usr/lib/qt4/imports/PlexyDesk/FolderListModel/libfolderlistmodel.so
/usr/lib/libplexymime.so
/usr/lib/libplexydeskcore.so
chris@Chris-Ubuntu:~$ 
[/I]

---

### Post by Face-Ache on 2012-04-12
So ... no-one knows about this issue huh?  :)

---

### Post by mcduck on 2012-04-13
Based on your description, the program works just fine, and the only problem is that the installer didn't create a launcher icon in the menus for it. Just make one yourself using the Alacarte menu editor (it appears as "Main Menu" in Dash, if I remember right).

Programs opened from a terminal closing when you close the terminal is the expected behaviour. (A child process should be ended when it's parent process is ended). Just don't close the terminal, use commands like "nohup", or the Alt-F2 "Run" dialog instead. Or, like I said, create a menu entry. :)

---

### Post by Face-Ache on 2012-04-13
Thanks McDuck - i'm very much a "Linux Newbie", and i'm liking it, but it's quite different to what i'm used to.

That seems to have done the trick - created a menu entry, and now it looks like it's working.

But i've no idea how to use it! :D  That's okay though, i'll Google it.

To make it start when i boot, i just need to add it to the Startup Applications?

---

### Post by mcduck on 2012-04-13
> **Face-Ache said:**
> Thanks McDuck - i'm very much a "Linux Newbie", and i'm liking it, but it's quite different to what i'm used to.

That seems to have done the trick - created a menu entry, and now it looks like it's working.

But i've no idea how to use it! :D  That's okay though, i'll Google it.

To make it start when i boot, i just need to add it to the Startup Applications?

yeah, adding to startup applications should work for automatically starting the program as soon as you log in.

---

