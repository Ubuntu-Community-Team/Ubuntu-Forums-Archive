---
title: "How to install Opera for Ubuntu 8.10"
date: 2010-04-18
forum: General Help
---

### Post by sunnyengineeer on 2010-04-18
Hi,
   I've dowmloaded .tar.bz2 file from net of Opera,but I think it is having some error in it,bcz Im not able to compile from the source ,and also Make & Makeinstall are also worthless..
 .So could someome please tell me where can I find the .deb package of Opera or download via terminal(So repositiries link for that.)...

Thanks
Windows always've glasses so they'll eventually break

---

### Post by howefield on 2010-04-18
From the Opera website.

[ftp://ftp.opera.com/pub/opera/linux/](ftp://ftp.opera.com/pub/opera/linux/)

Or click on the big green button on the homepage

[http://www.opera.com/](http://www.opera.com/)

---

### Post by Eraemaajaervi on 2010-04-18
if it's one of the UNIX 10.5x snapshots just cd to the folder and do ```
./opera &
```

---

### Post by cogier on 2010-04-18
If you download the .deb file from the Opera web site (see attached) Ubuntu will be able to install it all for you. Just double click on the file once it's downloaded and follow the prompts.

Hope that helps.

---

### Post by sunnyengineeer on 2010-04-18
Hi,
        I've tried using /.opera & /.configure commands both ,but sasly none of them working in my case..
        The limk which was given is not working,though it starts but in the middle it breaks somewhat completing around 20% only...
.........Does Ubuntu have a repository for this...so that I can install from Synaptci itself..

Thanks..

---

### Post by sunnyengineeer on 2010-04-18
Hi,
     I have .tar.bz2 file which I installed in following way,
1.)Extracted it.
2.)CD to that folder
3.) There it was having .sh file so I used 
sudo sh thinkorswim_intaller.sh

It installed successfully(All things were OK in terminal..)

So if someone oculd plz tell me where it has been installed..Bcz it is not coming under
Applications>Iternet

Help me out...
I think Im just a small step away from Opera..

Thanks
Ubuntu Lover

---

### Post by howefield on 2010-04-18
> **sunnyengineeer said:**
> So if someone oculd plz tell me where it has been installed..

Try tpying in terminal

```
locate opera
```

---

### Post by sunnyengineeer on 2010-04-18
Hi,
 Here is the O/P of command "locate Opera"

/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
/usr/include/c++/4.3/parallel/set_operations.h
/usr/lib/evolution/2.24/plugins/liborg-gnome-exchange-operations.so
/usr/lib/evolution/2.24/plugins/org-gnome-exchange-operations.eplug
/usr/lib/python2.5/lib-dynload/operator.so
/usr/share/evolution/2.24/errors/org-gnome-exchange-operations.error
/usr/share/man/man7/operator.7.gz
/usr/share/pixmaps/pidgin/emblems/16/half-operator.png
/usr/share/pixmaps/pidgin/emblems/16/operator.png
/usr/share/transmission/web/images/graphics/browser_opera.gif
/usr/src/linux-headers-2.6.27-7-generic/include/config/dvb/usb/opera1.h
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages


Still I am not able to find from where to run it,I've tried several files...
Somebody cna help me....

Thanks

---

### Post by sunnyengineeer on 2010-04-19
Hello,
         Can plz someone help me out of this..or till the ash settles I have to wait...

Please guys...I love Opera...man help me to find it out...

Thanks

---

### Post by sunnyengineeer on 2010-04-19
Here is the correct O/P of command "locate opera"

/home/jaguar/opera/usr/share/opera/java/opera.jar
/home/jaguar/opera/usr/share/opera/java/opera.policy
/home/jaguar/opera/usr/share/opera/locale/be
/home/jaguar/opera/usr/share/opera/locale/bg
/home/jaguar/opera/usr/share/opera/locale/cs
/home/jaguar/opera/usr/share/opera/locale/da
/home/jaguar/opera/usr/share/opera/locale/de
/home/jaguar/opera/usr/share/opera/locale/el
/home/jaguar/opera/usr/share/opera/locale/en
/home/jaguar/opera/usr/share/opera/locale/en-GB
/home/jaguar/opera/usr/share/opera/locale/es-ES
/home/jaguar/opera/usr/share/opera/locale/es-LA
/home/jaguar/opera/usr/share/opera/locale/et
/home/jaguar/opera/usr/share/opera/locale/fi
/home/jaguar/opera/usr/share/opera/locale/fr
/home/jaguar/opera/usr/share/opera/locale/fr-CA
/home/jaguar/opera/usr/share/opera/locale/fy
/home/jaguar/opera/usr/share/opera/locale/hi
/home/jaguar/opera/usr/share/opera/locale/hr
/home/jaguar/opera/usr/share/opera/locale/hu
/home/jaguar/opera/usr/share/opera/locale/id
/home/jaguar/opera/usr/share/opera/locale/it
/home/jaguar/opera/usr/share/opera/locale/ja
/home/jaguar/opera/usr/share/opera/locale/ka
/home/jaguar/opera/usr/share/opera/locale/ko
/home/jaguar/opera/usr/share/opera/locale/lt
/home/jaguar/opera/usr/share/opera/locale/mk
/home/jaguar/opera/usr/share/opera/locale/nb
/home/jaguar/opera/usr/share/opera/locale/nl
/home/jaguar/opera/usr/share/opera/locale/nn
/home/jaguar/opera/usr/share/opera/locale/pl
/home/jaguar/opera/usr/share/opera/locale/pt
/home/jaguar/opera/usr/share/opera/locale/pt-BR
/home/jaguar/opera/usr/share/opera/locale/ro
/home/jaguar/opera/usr/share/opera/locale/ru
/home/jaguar/opera/usr/share/opera/locale/sk
/home/jaguar/opera/usr/share/opera/locale/sr
/home/jaguar/opera/usr/share/opera/locale/sv
/home/jaguar/opera/usr/share/opera/locale/ta
/home/jaguar/opera/usr/share/opera/locale/te
/home/jaguar/opera/usr/share/opera/locale/tr
/home/jaguar/opera/usr/share/opera/locale/uk
/home/jaguar/opera/usr/share/opera/locale/zh-cn
/home/jaguar/opera/usr/share/opera/locale/zh-hk
/home/jaguar/opera/usr/share/opera/locale/zh-tw
/home/jaguar/opera/usr/share/opera/locale/be/be.lng
/home/jaguar/opera/usr/share/opera/locale/be/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/be/search.ini
/home/jaguar/opera/usr/share/opera/locale/be/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/bg/bg.lng
/home/jaguar/opera/usr/share/opera/locale/cs/cs.lng
/home/jaguar/opera/usr/share/opera/locale/da/da.lng
/home/jaguar/opera/usr/share/opera/locale/de/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/de/de.lng
/home/jaguar/opera/usr/share/opera/locale/de/search.ini
/home/jaguar/opera/usr/share/opera/locale/de/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/el/el.lng
/home/jaguar/opera/usr/share/opera/locale/en/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/en/en.lng
/home/jaguar/opera/usr/share/opera/locale/en/en.zip
/home/jaguar/opera/usr/share/opera/locale/en/license.txt
/home/jaguar/opera/usr/share/opera/locale/en/search.ini
/home/jaguar/opera/usr/share/opera/locale/en/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/en-GB/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/en-GB/en-GB.lng
/home/jaguar/opera/usr/share/opera/locale/en-GB/search.ini
/home/jaguar/opera/usr/share/opera/locale/en-GB/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/es-ES/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/es-ES/es-ES.lng
/home/jaguar/opera/usr/share/opera/locale/es-ES/search.ini
/home/jaguar/opera/usr/share/opera/locale/es-ES/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/es-LA/es-LA.lng
/home/jaguar/opera/usr/share/opera/locale/et/et.lng
/home/jaguar/opera/usr/share/opera/locale/fi/fi.lng
/home/jaguar/opera/usr/share/opera/locale/fr/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/fr/fr.lng
/home/jaguar/opera/usr/share/opera/locale/fr/search.ini
/home/jaguar/opera/usr/share/opera/locale/fr/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/fr-CA/fr-CA.lng
/home/jaguar/opera/usr/share/opera/locale/fy/fy.lng
/home/jaguar/opera/usr/share/opera/locale/hi/hi.lng
/home/jaguar/opera/usr/share/opera/locale/hi/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/hr/hr.lng
/home/jaguar/opera/usr/share/opera/locale/hu/hu.lng
/home/jaguar/opera/usr/share/opera/locale/id/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/id/id.lng
/home/jaguar/opera/usr/share/opera/locale/id/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/it/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/it/it.lng
/home/jaguar/opera/usr/share/opera/locale/it/search.ini
/home/jaguar/opera/usr/share/opera/locale/it/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/ja/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/ja/ja.lng
/home/jaguar/opera/usr/share/opera/locale/ja/license.txt
/home/jaguar/opera/usr/share/opera/locale/ja/search.ini
/home/jaguar/opera/usr/share/opera/locale/ja/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/ka/ka.lng
/home/jaguar/opera/usr/share/opera/locale/ko/ko.lng
/home/jaguar/opera/usr/share/opera/locale/lt/lt.lng
/home/jaguar/opera/usr/share/opera/locale/mk/mk.lng
/home/jaguar/opera/usr/share/opera/locale/nb/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/nb/nb.lng
/home/jaguar/opera/usr/share/opera/locale/nb/search.ini
/home/jaguar/opera/usr/share/opera/locale/nb/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/nl/nl.lng
/home/jaguar/opera/usr/share/opera/locale/nn/nn.lng
/home/jaguar/opera/usr/share/opera/locale/pl/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/pl/pl.lng
/home/jaguar/opera/usr/share/opera/locale/pl/search.ini
/home/jaguar/opera/usr/share/opera/locale/pl/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/pt/pt.lng
/home/jaguar/opera/usr/share/opera/locale/pt-BR/pt-BR.lng
/home/jaguar/opera/usr/share/opera/locale/ro/ro.lng
/home/jaguar/opera/usr/share/opera/locale/ru/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/ru/ru.lng
/home/jaguar/opera/usr/share/opera/locale/ru/search.ini
/home/jaguar/opera/usr/share/opera/locale/ru/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/sk/sk.lng
/home/jaguar/opera/usr/share/opera/locale/sr/sr.lng
/home/jaguar/opera/usr/share/opera/locale/sv/sv.lng
/home/jaguar/opera/usr/share/opera/locale/ta/ta.lng
/home/jaguar/opera/usr/share/opera/locale/te/te.lng
/home/jaguar/opera/usr/share/opera/locale/tr/tr.lng
/home/jaguar/opera/usr/share/opera/locale/uk/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/uk/search.ini
/home/jaguar/opera/usr/share/opera/locale/uk/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/uk/uk.lng
/home/jaguar/opera/usr/share/opera/locale/zh-cn/bookmarks.adr
/home/jaguar/opera/usr/share/opera/locale/zh-cn/browser.js
/home/jaguar/opera/usr/share/opera/locale/zh-cn/search.ini
/home/jaguar/opera/usr/share/opera/locale/zh-cn/standard_speeddial.ini
/home/jaguar/opera/usr/share/opera/locale/zh-cn/turbosettings.xml
/home/jaguar/opera/usr/share/opera/locale/zh-cn/zh-cn.lng
/home/jaguar/opera/usr/share/opera/locale/zh-hk/browser.js
/home/jaguar/opera/usr/share/opera/locale/zh-hk/turbosettings.xml
/home/jaguar/opera/usr/share/opera/locale/zh-tw/browser.js
/home/jaguar/opera/usr/share/opera/locale/zh-tw/turbosettings.xml
/home/jaguar/opera/usr/share/opera/locale/zh-tw/zh-tw.lng
/home/jaguar/opera/usr/share/opera/scripts/common.js
/home/jaguar/opera/usr/share/opera/scripts/substance.js
/home/jaguar/opera/usr/share/opera/skin/standard_skin.zip
/home/jaguar/opera/usr/share/opera/styles/about.css
/home/jaguar/opera/usr/share/opera/styles/cache.css
/home/jaguar/opera/usr/share/opera/styles/certinfo.css
/home/jaguar/opera/usr/share/opera/styles/config.css
/home/jaguar/opera/usr/share/opera/styles/contentblock.css
/home/jaguar/opera/usr/share/opera/styles/debug.css
/home/jaguar/opera/usr/share/opera/styles/dir.css
/home/jaguar/opera/usr/share/opera/styles/error.css
/home/jaguar/opera/usr/share/opera/styles/history.css
/home/jaguar/opera/usr/share/opera/styles/im.css
/home/jaguar/opera/usr/share/opera/styles/image.css
/home/jaguar/opera/usr/share/opera/styles/images
/home/jaguar/opera/usr/share/opera/styles/info.css
/home/jaguar/opera/usr/share/opera/styles/m2_welcome_message.mbs
/home/jaguar/opera/usr/share/opera/styles/mail.css
/home/jaguar/opera/usr/share/opera/styles/mathml.css
/home/jaguar/opera/usr/share/opera/styles/message.css
/home/jaguar/opera/usr/share/opera/styles/mime.css
/home/jaguar/opera/usr/share/opera/styles/opera.css
/home/jaguar/opera/usr/share/opera/styles/plugins.css
/home/jaguar/opera/usr/share/opera/styles/search.css
/home/jaguar/opera/usr/share/opera/styles/unstyledxml.css
/home/jaguar/opera/usr/share/opera/styles/user
/home/jaguar/opera/usr/share/opera/styles/warning.css
/home/jaguar/opera/usr/share/opera/styles/webfeeds.html
/home/jaguar/opera/usr/share/opera/styles/wml.css
/home/jaguar/opera/usr/share/opera/styles/images/Opera_256x256.png
/home/jaguar/opera/usr/share/opera/styles/images/bar.png
/home/jaguar/opera/usr/share/opera/styles/images/bullet.png
/home/jaguar/opera/usr/share/opera/styles/images/center.png
/home/jaguar/opera/usr/share/opera/styles/images/customize.gif
/home/jaguar/opera/usr/share/opera/styles/images/darkBox.png
/home/jaguar/opera/usr/share/opera/styles/images/defaultFavicon.png
/home/jaguar/opera/usr/share/opera/styles/images/error.png
/home/jaguar/opera/usr/share/opera/styles/images/file.png
/home/jaguar/opera/usr/share/opera/styles/images/flag.png
/home/jaguar/opera/usr/share/opera/styles/images/folder.png
/home/jaguar/opera/usr/share/opera/styles/images/header-expanded.png
/home/jaguar/opera/usr/share/opera/styles/images/header.png
/home/jaguar/opera/usr/share/opera/styles/images/opera.png
/home/jaguar/opera/usr/share/opera/styles/images/page-bot.png
/home/jaguar/opera/usr/share/opera/styles/images/red_center.png
/home/jaguar/opera/usr/share/opera/styles/images/red_left.png
/home/jaguar/opera/usr/share/opera/styles/images/red_right.png
/home/jaguar/opera/usr/share/opera/styles/images/root.png
/home/jaguar/opera/usr/share/opera/styles/images/section.png
/home/jaguar/opera/usr/share/opera/styles/images/smartGroup.png
/home/jaguar/opera/usr/share/opera/styles/images/top.png
/home/jaguar/opera/usr/share/opera/styles/images/warning.png
/home/jaguar/opera/usr/share/opera/styles/user/accessibility.css
/home/jaguar/opera/usr/share/opera/styles/user/altdebugger.css
/home/jaguar/opera/usr/share/opera/styles/user/classid.css
/home/jaguar/opera/usr/share/opera/styles/user/contrastbw.css
/home/jaguar/opera/usr/share/opera/styles/user/contrastwb.css
/home/jaguar/opera/usr/share/opera/styles/user/disablebreaks.css
/home/jaguar/opera/usr/share/opera/styles/user/disablefloats.css
/home/jaguar/opera/usr/share/opera/styles/user/disableforms.css
/home/jaguar/opera/usr/share/opera/styles/user/disablepositioning.css
/home/jaguar/opera/usr/share/opera/styles/user/disabletables.css
/home/jaguar/opera/usr/share/opera/styles/user/outline.css
/home/jaguar/opera/usr/share/opera/styles/user/structureblock.css
/home/jaguar/opera/usr/share/opera/styles/user/structureinline.css
/home/jaguar/opera/usr/share/opera/styles/user/structuretables.css
/home/jaguar/opera/usr/share/opera/styles/user/tablelayout.css
/home/jaguar/opera/usr/share/opera/styles/user/toc.css
/home/jaguar/opera/usr/share/opera/ui/dialog.ini
/home/jaguar/opera/usr/share/opera/ui/fastforward.ini
/home/jaguar/opera/usr/share/opera/ui/standard_keyboard.ini
/home/jaguar/opera/usr/share/opera/ui/standard_keyboard_compat.ini
/home/jaguar/opera/usr/share/opera/ui/standard_menu.ini
/home/jaguar/opera/usr/share/opera/ui/standard_mouse.ini
/home/jaguar/opera/usr/share/opera/ui/standard_toolbar.ini
/home/jaguar/opera/usr/share/opera/ui/unix_keyboard.ini
/home/jaguar/opera/usr/share/opera/unite/fileSharing.ua
/home/jaguar/opera/usr/share/opera/unite/fridge.ua
/home/jaguar/opera/usr/share/opera/unite/home.ua
/home/jaguar/opera/usr/share/opera/unite/mediaPlayer.ua
/home/jaguar/opera/usr/share/opera/unite/messenger.ua
/home/jaguar/opera/usr/share/opera/unite/photoSharing.ua
/home/jaguar/opera/usr/share/opera/unite/webserver.ua
/home/jaguar/opera/usr/share/pixmaps/opera.xpm
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
/usr/bin/opera
/usr/include/c++/4.3/parallel/set_operations.h
/usr/lib/opera
/usr/lib/evolution/2.24/plugins/liborg-gnome-exchange-operations.so
/usr/lib/evolution/2.24/plugins/org-gnome-exchange-operations.eplug
/usr/lib/opera/10.10
/usr/lib/opera/plugins
/usr/lib/opera/10.10/missingsyms.so
/usr/lib/opera/10.10/opera
/usr/lib/opera/10.10/operaplugincleaner
/usr/lib/opera/10.10/operapluginwrapper
/usr/lib/opera/10.10/operapluginwrapper-ia32-linux
/usr/lib/opera/10.10/operapluginwrapper-native
/usr/lib/opera/10.10/spellcheck.so
/usr/lib/opera/10.10/works
/usr/lib/python2.5/lib-dynload/operator.so
/usr/local/share/applications/opera.desktop
/usr/local/share/icons/hicolor/22x22/apps/opera.png
/usr/local/share/icons/hicolor/32x32/apps/opera.png
/usr/local/share/icons/hicolor/48x48/apps/opera.png
/usr/share/opera
/usr/share/doc/opera
/usr/share/doc/opera/LGPL
/usr/share/doc/opera/LICENSE
/usr/share/evolution/2.24/errors/org-gnome-exchange-operations.error
/usr/share/man/man1/opera.1
/usr/share/man/man7/operator.7.gz
/usr/share/opera/defaults
/usr/share/opera/encoding.bin
/usr/share/opera/extra
/usr/share/opera/html40_entities.dtd
/usr/share/opera/java
/usr/share/opera/lngcode.txt
/usr/share/opera/locale
/usr/share/opera/scripts
/usr/share/opera/skin
/usr/share/opera/styles
/usr/share/opera/ui
/usr/share/opera/unite
/usr/share/opera/defaults/bookmarks.adr
/usr/share/opera/defaults/feedreaders.ini
/usr/share/opera/defaults/filehandler.ini
/usr/share/opera/defaults/font.ini
/usr/share/opera/defaults/license.txt
/usr/share/opera/defaults/mailproviders.xml
/usr/share/opera/defaults/pluginpath.ini
/usr/share/opera/defaults/search.ini
/usr/share/opera/defaults/standard_speeddial.ini
/usr/share/opera/defaults/standard_trusted_repositories.ini
/usr/share/opera/defaults/webmailproviders.ini
/usr/share/opera/defaults/xmlentities.ini
/usr/share/opera/extra/missingplugin.svg
/usr/share/opera/extra/missingpluginhover.svg
/usr/share/opera/extra/svg-mo.dat
/usr/share/opera/extra/svg-mobd.dat
/usr/share/opera/extra/svg-sa.dat
/usr/share/opera/extra/svg-sabd.dat
/usr/share/opera/extra/svg-se.dat
/usr/share/opera/extra/svg-sebd.dat
/usr/share/opera/java/opera.jar
/usr/share/opera/java/opera.policy
/usr/share/opera/locale/be
/usr/share/opera/locale/bg
/usr/share/opera/locale/cs
/usr/share/opera/locale/da
/usr/share/opera/locale/de
/usr/share/opera/locale/el
/usr/share/opera/locale/en
/usr/share/opera/locale/en-GB
/usr/share/opera/locale/es-ES
/usr/share/opera/locale/es-LA
/usr/share/opera/locale/et
/usr/share/opera/locale/fi
/usr/share/opera/locale/fr
/usr/share/opera/locale/fr-CA
/usr/share/opera/locale/fy
/usr/share/opera/locale/hi
/usr/share/opera/locale/hr
/usr/share/opera/locale/hu
/usr/share/opera/locale/id
/usr/share/opera/locale/it
/usr/share/opera/locale/ja
/usr/share/opera/locale/ka
/usr/share/opera/locale/ko
/usr/share/opera/locale/lt
/usr/share/opera/locale/mk
/usr/share/opera/locale/nb
/usr/share/opera/locale/nl
/usr/share/opera/locale/nn
/usr/share/opera/locale/pl
/usr/share/opera/locale/pt
/usr/share/opera/locale/pt-BR
/usr/share/opera/locale/ro
/usr/share/opera/locale/ru
/usr/share/opera/locale/sk
/usr/share/opera/locale/sr
/usr/share/opera/locale/sv
/usr/share/opera/locale/ta
/usr/share/opera/locale/te
/usr/share/opera/locale/tr
/usr/share/opera/locale/uk
/usr/share/opera/locale/zh-cn
/usr/share/opera/locale/zh-hk
/usr/share/opera/locale/zh-tw
/usr/share/opera/locale/be/be.lng
/usr/share/opera/locale/be/bookmarks.adr
/usr/share/opera/locale/be/search.ini
/usr/share/opera/locale/be/standard_speeddial.ini
/usr/share/opera/locale/bg/bg.lng
/usr/share/opera/locale/cs/cs.lng
/usr/share/opera/locale/da/da.lng
/usr/share/opera/locale/de/bookmarks.adr
/usr/share/opera/locale/de/de.lng
/usr/share/opera/locale/de/search.ini
/usr/share/opera/locale/de/standard_speeddial.ini
/usr/share/opera/locale/el/el.lng
/usr/share/opera/locale/en/bookmarks.adr
/usr/share/opera/locale/en/en.lng
/usr/share/opera/locale/en/en.zip
/usr/share/opera/locale/en/license.txt
/usr/share/opera/locale/en/search.ini
/usr/share/opera/locale/en/standard_speeddial.ini
/usr/share/opera/locale/en-GB/bookmarks.adr
/usr/share/opera/locale/en-GB/en-GB.lng
/usr/share/opera/locale/en-GB/search.ini
/usr/share/opera/locale/en-GB/standard_speeddial.ini
/usr/share/opera/locale/es-ES/bookmarks.adr
/usr/share/opera/locale/es-ES/es-ES.lng
/usr/share/opera/locale/es-ES/search.ini
/usr/share/opera/locale/es-ES/standard_speeddial.ini
/usr/share/opera/locale/es-LA/es-LA.lng
/usr/share/opera/locale/et/et.lng
/usr/share/opera/locale/fi/fi.lng
/usr/share/opera/locale/fr/bookmarks.adr
/usr/share/opera/locale/fr/fr.lng
/usr/share/opera/locale/fr/search.ini
/usr/share/opera/locale/fr/standard_speeddial.ini
/usr/share/opera/locale/fr-CA/fr-CA.lng
/usr/share/opera/locale/fy/fy.lng
/usr/share/opera/locale/hi/hi.lng
/usr/share/opera/locale/hi/standard_speeddial.ini
/usr/share/opera/locale/hr/hr.lng
/usr/share/opera/locale/hu/hu.lng
/usr/share/opera/locale/id/bookmarks.adr
/usr/share/opera/locale/id/id.lng
/usr/share/opera/locale/id/standard_speeddial.ini
/usr/share/opera/locale/it/bookmarks.adr
/usr/share/opera/locale/it/it.lng
/usr/share/opera/locale/it/search.ini
/usr/share/opera/locale/it/standard_speeddial.ini
/usr/share/opera/locale/ja/bookmarks.adr
/usr/share/opera/locale/ja/ja.lng
/usr/share/opera/locale/ja/license.txt
/usr/share/opera/locale/ja/search.ini
/usr/share/opera/locale/ja/standard_speeddial.ini
/usr/share/opera/locale/ka/ka.lng
/usr/share/opera/locale/ko/ko.lng
/usr/share/opera/locale/lt/lt.lng
/usr/share/opera/locale/mk/mk.lng
/usr/share/opera/locale/nb/bookmarks.adr
/usr/share/opera/locale/nb/nb.lng
/usr/share/opera/locale/nb/search.ini
/usr/share/opera/locale/nb/standard_speeddial.ini
/usr/share/opera/locale/nl/nl.lng
/usr/share/opera/locale/nn/nn.lng
/usr/share/opera/locale/pl/bookmarks.adr
/usr/share/opera/locale/pl/pl.lng
/usr/share/opera/locale/pl/search.ini
/usr/share/opera/locale/pl/standard_speeddial.ini
/usr/share/opera/locale/pt/pt.lng
/usr/share/opera/locale/pt-BR/pt-BR.lng
/usr/share/opera/locale/ro/ro.lng
/usr/share/opera/locale/ru/bookmarks.adr
/usr/share/opera/locale/ru/ru.lng
/usr/share/opera/locale/ru/search.ini
/usr/share/opera/locale/ru/standard_speeddial.ini
/usr/share/opera/locale/sk/sk.lng
/usr/share/opera/locale/sr/sr.lng
/usr/share/opera/locale/sv/sv.lng
/usr/share/opera/locale/ta/ta.lng
/usr/share/opera/locale/te/te.lng
/usr/share/opera/locale/tr/tr.lng
/usr/share/opera/locale/uk/bookmarks.adr
/usr/share/opera/locale/uk/search.ini
/usr/share/opera/locale/uk/standard_speeddial.ini
/usr/share/opera/locale/uk/uk.lng
/usr/share/opera/locale/zh-cn/bookmarks.adr
/usr/share/opera/locale/zh-cn/browser.js
/usr/share/opera/locale/zh-cn/search.ini
/usr/share/opera/locale/zh-cn/standard_speeddial.ini
/usr/share/opera/locale/zh-cn/turbosettings.xml
/usr/share/opera/locale/zh-cn/zh-cn.lng
/usr/share/opera/locale/zh-hk/browser.js
/usr/share/opera/locale/zh-hk/turbosettings.xml
/usr/share/opera/locale/zh-tw/browser.js
/usr/share/opera/locale/zh-tw/turbosettings.xml
/usr/share/opera/locale/zh-tw/zh-tw.lng
/usr/share/opera/scripts/common.js
/usr/share/opera/scripts/substance.js
/usr/share/opera/skin/standard_skin.zip
/usr/share/opera/styles/about.css
/usr/share/opera/styles/cache.css
/usr/share/opera/styles/certinfo.css
/usr/share/opera/styles/config.css
/usr/share/opera/styles/contentblock.css
/usr/share/opera/styles/debug.css
/usr/share/opera/styles/dir.css
/usr/share/opera/styles/error.css
/usr/share/opera/styles/history.css
/usr/share/opera/styles/im.css
/usr/share/opera/styles/image.css
/usr/share/opera/styles/images
/usr/share/opera/styles/info.css
/usr/share/opera/styles/m2_welcome_message.mbs
/usr/share/opera/styles/mail.css
/usr/share/opera/styles/mathml.css
/usr/share/opera/styles/message.css
/usr/share/opera/styles/mime.css
/usr/share/opera/styles/opera.css
/usr/share/opera/styles/plugins.css
/usr/share/opera/styles/search.css
/usr/share/opera/styles/unstyledxml.css
/usr/share/opera/styles/user
/usr/share/opera/styles/warning.css
/usr/share/opera/styles/webfeeds.html
/usr/share/opera/styles/wml.css
/usr/share/opera/styles/images/Opera_256x256.png
/usr/share/opera/styles/images/bar.png
/usr/share/opera/styles/images/bullet.png
/usr/share/opera/styles/images/center.png
/usr/share/opera/styles/images/customize.gif
/usr/share/opera/styles/images/darkBox.png
/usr/share/opera/styles/images/defaultFavicon.png
/usr/share/opera/styles/images/error.png
/usr/share/opera/styles/images/file.png
/usr/share/opera/styles/images/flag.png
/usr/share/opera/styles/images/folder.png
/usr/share/opera/styles/images/header-expanded.png
/usr/share/opera/styles/images/header.png
/usr/share/opera/styles/images/opera.png
/usr/share/opera/styles/images/page-bot.png
/usr/share/opera/styles/images/red_center.png
/usr/share/opera/styles/images/red_left.png
/usr/share/opera/styles/images/red_right.png
/usr/share/opera/styles/images/root.png
/usr/share/opera/styles/images/section.png
/usr/share/opera/styles/images/smartGroup.png
/usr/share/opera/styles/images/top.png
/usr/share/opera/styles/images/warning.png
/usr/share/opera/styles/user/accessibility.css
/usr/share/opera/styles/user/altdebugger.css
/usr/share/opera/styles/user/classid.css
/usr/share/opera/styles/user/contrastbw.css
/usr/share/opera/styles/user/contrastwb.css
/usr/share/opera/styles/user/disablebreaks.css
/usr/share/opera/styles/user/disablefloats.css
/usr/share/opera/styles/user/disableforms.css
/usr/share/opera/styles/user/disablepositioning.css
/usr/share/opera/styles/user/disabletables.css
/usr/share/opera/styles/user/outline.css
/usr/share/opera/styles/user/structureblock.css
/usr/share/opera/styles/user/structureinline.css
/usr/share/opera/styles/user/structuretables.css
/usr/share/opera/styles/user/tablelayout.css
/usr/share/opera/styles/user/toc.css
/usr/share/opera/ui/dialog.ini
/usr/share/opera/ui/fastforward.ini
/usr/share/opera/ui/standard_keyboard.ini
/usr/share/opera/ui/standard_keyboard_compat.ini
/usr/share/opera/ui/standard_menu.ini
/usr/share/opera/ui/standard_mouse.ini
/usr/share/opera/ui/standard_toolbar.ini
/usr/share/opera/ui/unix_keyboard.ini
/usr/share/opera/unite/fileSharing.ua
/usr/share/opera/unite/fridge.ua
/usr/share/opera/unite/home.ua
/usr/share/opera/unite/mediaPlayer.ua
/usr/share/opera/unite/messenger.ua
/usr/share/opera/unite/photoSharing.ua
/usr/share/opera/unite/webserver.ua
/usr/share/pixmaps/pidgin/emblems/16/half-operator.png
/usr/share/pixmaps/pidgin/emblems/16/operator.png
/usr/share/transmission/web/images/graphics/browser_opera.gif
/usr/src/linux-headers-2.6.27-7-generic/include/config/dvb/usb/opera1.h
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages


Can someone figure it out...

---

### Post by Eraemaajaervi on 2010-04-20
I'm guessing you want the latest stable release, so go ahead and add the opera repository to your sources:
```

echo "deb http://deb.opera.com/opera/ stable non-free" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-cache policy opera       # see what version of opera is available

```

and eventually...

```
sudo apt-get install opera
```

---

### Post by sunnyengineeer on 2010-04-21
Hi,

 Thanks a lot now I've got the latets version & also got my problem resolved...
Really thanks a lot man....

Windows will always break bcz they have glasses...

Thanks

---

