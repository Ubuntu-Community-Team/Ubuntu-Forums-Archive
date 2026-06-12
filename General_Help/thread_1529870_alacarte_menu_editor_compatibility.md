---
title: "alacarte menu editor compatibility"
date: 2010-07-12
forum: General Help
---

### Post by jeidern on 2010-07-12
I've just recently downloaded Lubuntu 10.04 and tried it. It was nice because it was light on my machine. My only problem is, is that it doesn't have a graphical menu editor, and I don't know how to edit menus other than using GUIs.

I've read something about alacarte-menu-editor being able to be used in Lubuntu. I would just like to confirm if it DOES work with Lubuntu.

Thanks in advance. :p

---

### Post by jeidern on 2010-07-13
Bumping this thread. Sure would appreciate some reps. Thanks again

---

### Post by gadolinio on 2010-07-13
i'm not sure, as I've only tried Lubuntu a little in a virtual machine, but I think that could be done with the default tools that come with the system. Try right-clicking everything, looking for "properties", etc. It may be not a tool like "Menu editor, hey! click me", but some menu/obect's properties. Good luck!

---

### Post by jeidern on 2010-07-14
I tried the right clicking thing. When I right click the menu button, there is an option about the settings of the menu but when you click it, it's only the setting of the image shown in the menu button, nothing else.

Hmmm... anyways, I'm currently installing... when I'm finished installing I'll try the alacarte menu editor and I'll post the results afterwards.

---

### Post by jeidern on 2010-07-14
Well, I've successfully installed lubuntu, upgraded and installed alacarte via synaptic package manager. The said program installed quite well, It was added to the list of programs in the lubuntu main menu. But the problem is, even though alacarte worked as a program, the changes you make in it doesn't apply to the lubuntu menu. So in other words, my question as to the compatibility of alacarte to lubuntu is sadly answered with a "no" T_T

But I would like to ask another question... How do I edit the lubuntu Menu? I would just like to omit but not delete some items in the menu. Can anyone help me with this?

---

### Post by jeidern on 2010-07-14
Bumping for help ^_^

---

### Post by cavalier911 on 2010-07-14
What determines a program or functions location in the lxpanel menu plugin is the Categories=   of it's .desktop file.

cat /usr/share/applications/abiword.desktop 

[Desktop Entry]
Exec=abiword
Icon=abiword_48
Terminal=false
Type=Application
**Categories=Office**;WordProcessor;GNOME;GTK;X-Red-Hat-Base;
StartupNotify=true
X-Desktop-File-Install-Version=0.9
MimeType=application/x-abiword;text/x-abiword;text/x-xml-abiword;text/plain;application/msword;application/rtf;application/vnd.plain;application/xhtml+xml;text/html;application/x-crossmark;application/docbook+xml;application/x-t602;application/vnd.oasis.opendocument.text;application/vnd.sun.xml.writer;application/vnd.stardivision.writer;text/vnd.wap.wml;application/wordperfect6;application/wordperfect5.1;application/vnd.wordperfect;application/x-abicollab;application/vnd.palm;application/x-applix-word;application/x-kword;application/x-mif;application/x-mswrite;application/x-palm-database;text/abiword;text/richtext;text/rtf;application/x-abicollab
Name=AbiWord
GenericName=Word Processor
Comment=Compose, edit, and view documents

Categories list: [http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

---

### Post by jeidern on 2010-07-15
Im sorry for I am a newbie when it comes to these things. I tried searching for the .desktop file. I checked the /usr/share/applications directory and I can't seem to find it... how do I find it and how do I go about editing the .desktop file?

---

### Post by lance bermudez on 2011-01-25
open terminal and 
cd /usr/share/applications
sudo leafpad nameoffile.destop

I have nautilus installed so i would do
sudo leafpad nautilus-browser.desktop
found out the name by using pcmanfm right click properties
now to make then go away look at the example

[Desktop Entry]
Name=File Browser
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=nautilus --no-desktop --browser %U
Icon=system-file-manager
Terminal=false
StartupNotify=true
Type=Application
NoDisplay=true
Categories=GTK;System;Utility;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus

the above has 
NoDisplay=true
OnlyShowIn=GNOME; just add them to the files you dont want to show up I had to take it out of the above file so that nautilus would show up in the menu listings

---

### Post by matsonfamily on 2011-05-25
yeah, I've noticed that Alacarte does show the menu items, but cannot edit them (pressing the properties button).  Anyone know where specifically I'm supposed to post a bug like this?  I'm not interested in editing files; that's why I use a desktop-environment.  Thanks.

---

### Post by Rodney9 on 2011-11-02
> **matsonfamily said:**
> yeah, I've noticed that Alacarte does show the menu items, but cannot edit them (pressing the properties button).  Anyone know where specifically I'm supposed to post a bug like this?  I'm not interested in editing files; that's why I use a desktop-environment.  Thanks.

I have been searching and searching for a way to add items to my Lubuntu 11.10 menu as some software programs, ie Shutter & Alarm Clock, don't get added automatically.

I have tried lxde methods and lxmed, but neither work.
I have seen many posts about Alacarte , but again it is said it does not work.

So is there any news on a easy to use menu editor for Lubuntu ?

Rodney

---

### Post by Rodney9 on 2011-11-03
No news ? 

How to you add new apps to the menu ?

---

### Post by amjjawad on 2011-11-03
> **Rodney9 said:**
> No news ? 

How to you add new apps to the menu ?

It's an old thread but it's ok if that will help everyone :)

I follow the manual approach. I do that manually to the .desktop file on **/usr/share/applications**

For example: to show LockScreen on the Menu:

1- Open PCManFM
2- Tools > Open Current Folder as Root
3- Right Click on ScreenLock and choose "Leafpad"
4- Add these two lines in red:

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=ScreenLock
Name[zh_TW]=&#37782;&#20303;&#34722;&#24149;
Comment=Lock your screen
Icon=system-lock-screen
Exec=xscreensaver-command -lock
**[COLOR="Red"]#[/COLOR]**NoDisplay=true
[COLOR="red"]**Categories=Settings**[/COLOR]
```

5- You'll find it under Preferences

6- For other applications that you can't find under "applications", you can use "allocate" command in LXTerminal + the package name so you can allocate its location. For example, "conky" will be available in "/etc".

See also: [http://forum.lxde.org/viewtopic.php?f=8&t=31189](http://forum.lxde.org/viewtopic.php?f=8&t=31189)

---

### Post by Rodney9 on 2011-11-03
> **amjjawad said:**
> It's an old thread but it's ok if that will help everyone :)

I follow the manual approach. I do that manually to the .desktop file on **/usr/share/applications**

For example: to show LockScreen on the Menu:

1- Open PCManFM
2- Tools > Open Current Folder as Root
3- Right Click on ScreenLock and choose "Leafpad"
4- Add these two lines in red:

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=ScreenLock
Name[zh_TW]=&#37782;&#20303;&#34722;&#24149;
Comment=Lock your screen
Icon=system-lock-screen
Exec=xscreensaver-command -lock
**[COLOR="Red"]#[/COLOR]**NoDisplay=true
[COLOR="red"]**Categories=Settings**[/COLOR]
```

5- You'll find it under Preferences

6- For other applications that you can't find under "applications", you can use "allocate" command in LXTerminal + the package name so you can allocate its location. For example, "conky" will be available in "/etc".

See also: [http://forum.lxde.org/viewtopic.php?f=8&t=31189](http://forum.lxde.org/viewtopic.php?f=8&t=31189)

I tried Alarm Clock, as it is one that is not showing in the menu -

```
[Desktop Entry]
Version=1.0
Name=Alarm Clock
Name[pl]=Budzik
Name[pt]=Relógio Despertador
Comment=Schedule your tasks
Comment[pl]=Budzik dla &#347;rodowiska GNOME
Comment[pt]=Agende as suas tarefas
Name[sr]=&#1041;&#1091;&#1076;&#1080;&#1083;&#1085;&#1080;&#1082;
Name[sr@latin]=Budilnik
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112;&#1090;&#1077; &#1042;&#1072;&#1096;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;
Comment[sr@latin]=Organizujte Vaše vreme
Exec=alarmclock
Terminal=false
Type=Application
Icon=alarm-clock
StartupNotify=falsefallocate  is  used  to  preallocate blocks to a file. 
OnlyShowIn=GNOME;
#NoDisplay=true
Categories=Accessories
```

it did not work.

So I tried what you suggested and it doesn't work either.

```
Desktop Entry]
Encoding=UTF-8
Type=Application
Name=ScreenLock
Name[zh_TW]=&#37782;&#20303;&#34722;&#24149;
Comment=Lock your screen
Icon=system-lock-screen
Exec=xscreensaver-command -lock
#NoDisplay=true
Categories=Settings
```

Am I missing something ?

Also that "allocate" command gives this message - 


```
$ allocate +shutter
No command 'allocate' found, did you mean:
 Command 'fallocate' from package 'util-linux' (main)
allocate: command not found
```

*fallocate  is  used  to  preallocate blocks to a file.* 

I have googled allocate linux command with no luck, there is no man for it.

Rodney

---

### Post by amjjawad on 2011-11-04
Try this:

```
[Desktop Entry]
Version=1.0
Name=Alarm Clock
Name[pl]=Budzik
Name[pt]=Relógio Despertador
Comment=Schedule your tasks
Comment[pl]=Budzik dla &#347;rodowiska GNOME
Comment[pt]=Agende as suas tarefas
Name[sr]=&#1041;&#1091;&#1076;&#1080;&#1083;&#1085;&#1080;&#1082;
Name[sr@latin]=Budilnik
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112;&#1090;&#1077; &#1042;&#1072;&#1096;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;
Comment[sr@latin]=Organizujte Vaše vreme
Exec=alarmclock
Terminal=false
Type=Application
Icon=alarm-clock
StartupNotify=falsefallocate  is  used  to  preallocate blocks to a file. 
[COLOR=Red]**#**[/COLOR]OnlyShowIn=GNOME;
#NoDisplay=true
Categories=Accessories
```


>  Also that "allocate" command gives this message - 
So sorry, my bad. It's "locate" not allocate.

for example:
```
lubuntu@lubuntu-desktop:~$ locate shutter 
```

---

### Post by Rodney9 on 2011-11-04
> **amjjawad said:**
> Try this:

```
[Desktop Entry]
Version=1.0
Name=Alarm Clock
Name[pl]=Budzik
Name[pt]=Relógio Despertador
Comment=Schedule your tasks
Comment[pl]=Budzik dla &#347;rodowiska GNOME
Comment[pt]=Agende as suas tarefas
Name[sr]=&#1041;&#1091;&#1076;&#1080;&#1083;&#1085;&#1080;&#1082;
Name[sr@latin]=Budilnik
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112;&#1090;&#1077; &#1042;&#1072;&#1096;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;
Comment[sr@latin]=Organizujte Vaše vreme
Exec=alarmclock
Terminal=false
Type=Application
Icon=alarm-clock
StartupNotify=falsefallocate  is  used  to  preallocate blocks to a file. 
[COLOR=Red]**#**[/COLOR]OnlyShowIn=GNOME;
#NoDisplay=true
Categories=Accessories
```



So sorry, my bad. It's "locate" not allocate.

for example:
```
lubuntu@lubuntu-desktop:~$ locate shutter 
```

Thank you for trying.

```
[COLOR=Red]**#**[/COLOR]OnlyShowIn=GNOME;
``` doesn't make any difference, I had already tried that.

It just seems you can not add to the menu, I have tried Lock Out as well. 
That's ok, we will work around it using the second panel, it's pity to clutter this though, with apps not frequently used.

Hopefully 12.04 will allow for new apps to be added to the menu to make it easy to find them.

Rodney

---

### Post by amjjawad on 2011-11-04
> **Rodney9 said:**
> Thank you for trying.

```
[COLOR=Red]**#**[/COLOR]OnlyShowIn=GNOME;
``` doesn't make any difference, I had already tried that.

It just seems you can not add to the menu, I have tried Lock Out as well. 
That's ok, we will work around it using the second panel, it's pity to clutter this though, with apps not frequently used.

Hopefully 12.04 will allow for new apps to be added to the menu to make it easy to find them.

Rodney


Rodney, I need to install that app and test it myself.

As for the Lock Screen, did you follow my steps?

---

### Post by Rodney9 on 2011-11-04
> As for the Lock Screen, did you follow my steps?

Well I just tried again with Screen lock, there are 2 of them in /usr/share/applications, it does seem to have worked, it is now in preferences. I thought that it would go on the main menu with logout as it said Settings.

This does give some hope, I don't know though which file to use for Shutter -


```
$ locate shutter
/home/rodney/.shutter
/home/rodney/.cache/shutter
/home/rodney/.cache/shutter/unsaved
/home/rodney/.config/autostart/shutter.desktop
/home/rodney/.shutter/accounts.xml
/home/rodney/.shutter/profiles
/home/rodney/.shutter/session.xml
/home/rodney/.shutter/settings.xml
/usr/bin/shutter
/usr/share/shutter
/usr/share/app-install/desktop/shutter:shutter.desktop
/usr/share/app-install/icons/shutter.png
/usr/share/applications/shutter.desktop
/usr/share/doc/shutter
/usr/share/doc/shutter/changelog.Debian.gz
/usr/share/doc/shutter/copyright
/usr/share/icons/Faenza/apps/16/shutter.png
/usr/share/icons/Faenza/apps/22/shutter.png
/usr/share/icons/Faenza/apps/24/shutter.png
/usr/share/icons/Faenza/apps/32/shutter.png
/usr/share/icons/Faenza/apps/48/shutter.png
/usr/share/icons/Faenza/apps/scalable/shutter.svg
/usr/share/icons/Faenza/status/22/shutter-panel.png
/usr/share/icons/Faenza/status/24/shutter-panel.png
/usr/share/icons/Faenza-Dark/status/22/shutter-panel.png
/usr/share/icons/Faenza-Dark/status/24/shutter-panel.png
/usr/share/icons/hicolor/128x128/apps/shutter.png
/usr/share/icons/hicolor/16x16/apps/shutter-panel.png
/usr/share/icons/hicolor/16x16/apps/shutter.png
/usr/share/icons/hicolor/192x192/apps/shutter.png
/usr/share/icons/hicolor/22x22/apps/shutter-panel.png
/usr/share/icons/hicolor/22x22/apps/shutter.png
/usr/share/icons/hicolor/24x24/apps/shutter-panel.png
/usr/share/icons/hicolor/24x24/apps/shutter.png
/usr/share/icons/hicolor/256x256/apps/shutter.png
/usr/share/icons/hicolor/32x32/apps/shutter.png
/usr/share/icons/hicolor/36x36/apps/shutter.png
/usr/share/icons/hicolor/48x48/apps/shutter.png
/usr/share/icons/hicolor/64x64/apps/shutter.png
/usr/share/icons/hicolor/72x72/apps/shutter.png
/usr/share/icons/hicolor/96x96/apps/shutter.png
/usr/share/icons/hicolor/scalable/apps/shutter-panel.svg
/usr/share/icons/hicolor/scalable/apps/shutter.svg
/usr/share/icons/ubuntu-mono-dark/16x16/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/22x22/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/24x24/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/scalable/apps/shutter-panel.svg
/usr/share/icons/ubuntu-mono-light/16x16/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/22x22/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/24x24/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/scalable/apps/shutter-panel.svg
/usr/share/locale/af/LC_MESSAGES/shutter.mo
/usr/share/locale/ar/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ar/LC_MESSAGES/shutter.mo
/usr/share/locale/as/LC_MESSAGES/shutter.mo
/usr/share/locale/ast/LC_MESSAGES/shutter.mo
/usr/share/locale/bg/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/bg/LC_MESSAGES/shutter.mo
/usr/share/locale/bn/LC_MESSAGES/shutter.mo
/usr/share/locale/bs/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/bs/LC_MESSAGES/shutter.mo
/usr/share/locale/ca/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ca/LC_MESSAGES/shutter.mo
/usr/share/locale/cs/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/cs/LC_MESSAGES/shutter.mo
/usr/share/locale/da/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/da/LC_MESSAGES/shutter.mo
/usr/share/locale/de/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/de/LC_MESSAGES/shutter.mo
/usr/share/locale/el/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/el/LC_MESSAGES/shutter.mo
/usr/share/locale/en_CA/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/en_CA/LC_MESSAGES/shutter.mo
/usr/share/locale/en_GB/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/en_GB/LC_MESSAGES/shutter.mo
/usr/share/locale/es/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/es/LC_MESSAGES/shutter.mo
/usr/share/locale/et/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/et/LC_MESSAGES/shutter.mo
/usr/share/locale/eu/LC_MESSAGES/shutter.mo
/usr/share/locale/fi/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/fi/LC_MESSAGES/shutter.mo
/usr/share/locale/fo/LC_MESSAGES/shutter.mo
/usr/share/locale/fr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/fr/LC_MESSAGES/shutter.mo
/usr/share/locale/gl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/gl/LC_MESSAGES/shutter.mo
/usr/share/locale/he/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/he/LC_MESSAGES/shutter.mo
/usr/share/locale/hr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/hr/LC_MESSAGES/shutter.mo
/usr/share/locale/hu/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/hu/LC_MESSAGES/shutter.mo
/usr/share/locale/id/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/id/LC_MESSAGES/shutter.mo
/usr/share/locale/it/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/it/LC_MESSAGES/shutter.mo
/usr/share/locale/ja/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ja/LC_MESSAGES/shutter.mo
/usr/share/locale/kk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/kk/LC_MESSAGES/shutter.mo
/usr/share/locale/ko/LC_MESSAGES/shutter.mo
/usr/share/locale/lt/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/lt/LC_MESSAGES/shutter.mo
/usr/share/locale/lv/LC_MESSAGES/shutter.mo
/usr/share/locale/ms/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ms/LC_MESSAGES/shutter.mo
/usr/share/locale/nb/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/nb/LC_MESSAGES/shutter.mo
/usr/share/locale/nl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/nl/LC_MESSAGES/shutter.mo
/usr/share/locale/nn/LC_MESSAGES/shutter.mo
/usr/share/locale/oc/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/oc/LC_MESSAGES/shutter.mo
/usr/share/locale/pl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pl/LC_MESSAGES/shutter.mo
/usr/share/locale/pt/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pt/LC_MESSAGES/shutter.mo
/usr/share/locale/pt_BR/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pt_BR/LC_MESSAGES/shutter.mo
/usr/share/locale/ro/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ro/LC_MESSAGES/shutter.mo
/usr/share/locale/ru/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ru/LC_MESSAGES/shutter.mo
/usr/share/locale/sk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sk/LC_MESSAGES/shutter.mo
/usr/share/locale/sl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sl/LC_MESSAGES/shutter.mo
/usr/share/locale/sr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sr/LC_MESSAGES/shutter.mo
/usr/share/locale/sv/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sv/LC_MESSAGES/shutter.mo
/usr/share/locale/te/LC_MESSAGES/shutter.mo
/usr/share/locale/th/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/th/LC_MESSAGES/shutter.mo
/usr/share/locale/tr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/tr/LC_MESSAGES/shutter.mo
/usr/share/locale/uk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/uk/LC_MESSAGES/shutter.mo
/usr/share/locale/ur/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ur/LC_MESSAGES/shutter.mo
/usr/share/locale/vi/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/vi/LC_MESSAGES/shutter.mo
/usr/share/locale/zh_CN/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/zh_CN/LC_MESSAGES/shutter.mo
/usr/share/locale/zh_TW/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/zh_TW/LC_MESSAGES/shutter.mo
/usr/share/man/man1/shutter.1.gz
/usr/share/pixmaps/shutter.png
/usr/share/shutter/resources
/usr/share/shutter/update-notifier-shutter
/usr/share/shutter/resources/conf
/usr/share/shutter/resources/credits
/usr/share/shutter/resources/icons
/usr/share/shutter/resources/license
/usr/share/shutter/resources/po
/usr/share/shutter/resources/system
/usr/share/shutter/resources/conf/shape.conf
/usr/share/shutter/resources/credits/art
/usr/share/shutter/resources/credits/dev
/usr/share/shutter/resources/icons/Image.svg
/usr/share/shutter/resources/icons/Normal.cur
/usr/share/shutter/resources/icons/desktop.svg
/usr/share/shutter/resources/icons/document-send.svg
/usr/share/shutter/resources/icons/draw.svg
/usr/share/shutter/resources/icons/drawing_tool
/usr/share/shutter/resources/icons/executable.svg
/usr/share/shutter/resources/icons/fullscreen.svg
/usr/share/shutter/resources/icons/logo-imagebanana.png
/usr/share/shutter/resources/icons/logo-imageshack.png
/usr/share/shutter/resources/icons/lpi-bug.png
/usr/share/shutter/resources/icons/lpi-help.png
/usr/share/shutter/resources/icons/lpi-translate.png
/usr/share/shutter/resources/icons/notify.svg
/usr/share/shutter/resources/icons/sel_window.svg
/usr/share/shutter/resources/icons/sel_window_active.svg
/usr/share/shutter/resources/icons/sel_window_menu.svg
/usr/share/shutter/resources/icons/sel_window_section.svg
/usr/share/shutter/resources/icons/sel_window_tooltip.svg
/usr/share/shutter/resources/icons/selection.svg
/usr/share/shutter/resources/icons/shutter_cursor.png
/usr/share/shutter/resources/icons/shutter_cursor_frame.png
/usr/share/shutter/resources/icons/throbber.gif
/usr/share/shutter/resources/icons/throbber_16x16.gif
/usr/share/shutter/resources/icons/web_image.svg
/usr/share/shutter/resources/icons/drawing_tool/cursor
/usr/share/shutter/resources/icons/drawing_tool/draw-arrow.png
/usr/share/shutter/resources/icons/drawing_tool/draw-callouts.png
/usr/share/shutter/resources/icons/drawing_tool/draw-censor.png
/usr/share/shutter/resources/icons/drawing_tool/draw-ellipse.png
/usr/share/shutter/resources/icons/drawing_tool/draw-eraser.png
/usr/share/shutter/resources/icons/drawing_tool/draw-freehand.png
/usr/share/shutter/resources/icons/drawing_tool/draw-highlighter.png
/usr/share/shutter/resources/icons/drawing_tool/draw-image.svg
/usr/share/shutter/resources/icons/drawing_tool/draw-line.png
/usr/share/shutter/resources/icons/drawing_tool/draw-locked.png
/usr/share/shutter/resources/icons/drawing_tool/draw-lower.png
/usr/share/shutter/resources/icons/drawing_tool/draw-number.png
/usr/share/shutter/resources/icons/drawing_tool/draw-pixelize.png
/usr/share/shutter/resources/icons/drawing_tool/draw-pointer.png
/usr/share/shutter/resources/icons/drawing_tool/draw-raise.png
/usr/share/shutter/resources/icons/drawing_tool/draw-rectangle.png
/usr/share/shutter/resources/icons/drawing_tool/draw-text.png
/usr/share/shutter/resources/icons/drawing_tool/draw-unlocked.png
/usr/share/shutter/resources/icons/drawing_tool/objects
/usr/share/shutter/resources/icons/drawing_tool/transform-crop.png
/usr/share/shutter/resources/icons/drawing_tool/cursor/arrow
/usr/share/shutter/resources/icons/drawing_tool/cursor/censor
/usr/share/shutter/resources/icons/drawing_tool/cursor/ellipse
/usr/share/shutter/resources/icons/drawing_tool/cursor/freehand
/usr/share/shutter/resources/icons/drawing_tool/cursor/line
/usr/share/shutter/resources/icons/drawing_tool/cursor/number
/usr/share/shutter/resources/icons/drawing_tool/cursor/pixelize
/usr/share/shutter/resources/icons/drawing_tool/cursor/rect
/usr/share/shutter/resources/icons/drawing_tool/cursor/text
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library
/usr/share/shutter/resources/icons/drawing_tool/objects/apply.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/cssed.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/error-round.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/important-red.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/information-red.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/information-yellow.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/notice.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/question.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/star.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/stop-hand.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/tux.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/warning.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Alternate.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Diagonal Resize 1.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Diagonal Resize 2.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Handwriting.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Help.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Horizontal Resize.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Link.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Move.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Normal.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Precision.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Text.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Unavailable.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Vertical Resize.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_center_bottom.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_center_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_left_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_right_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/address-book-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/appointment-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/bookmark-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/contact-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-open.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-print-preview.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-print.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-properties.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-save-as.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-save.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-clear.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-copy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-cut.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-delete.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-find-replace.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-find.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-paste.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-redo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-select-all.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-undo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/folder-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-indent-less.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-indent-more.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-fill.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-bold.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-italic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-strikethrough.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-underline.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-bottom.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-down.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-first.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-home.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-jump.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-last.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-next.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-previous.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-up.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/list-add.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/list-remove.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-mark-junk.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-message-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-reply-all.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-reply-sender.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-send-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-eject.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-pause.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-start.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-stop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-record.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-seek-backward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-seek-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-skip-backward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-skip-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/process-stop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-lock-screen.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-log-out.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-search.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-shutdown.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/tab-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/view-fullscreen.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/view-refresh.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/window-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-calculator.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-character-map.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-text-editor.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/help-browser.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-group-chat.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-mail.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-news-reader.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-web-browser.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/office-calendar.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-accessibility.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-assistive-technology.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-font.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-keyboard-shortcuts.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-locale.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-multimedia.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-remote-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-screensaver.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-theme.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-wallpaper.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-network-proxy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-session.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-windows.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-file-manager.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-installer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-software-update.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-users.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/utilities-system-monitor.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/utilities-terminal.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-accessories.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-development.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-games.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-graphics.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-internet.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-multimedia.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-office.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-other.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-desktop-peripherals.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/audio-card.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/audio-input-microphone.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/battery.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/camera-photo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/camera-video.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/computer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-harddisk.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-optical.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-removable-media.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-gaming.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-keyboard.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-mouse.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-flash.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-floppy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-optical.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/multimedia-player.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/network-wired.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/network-wireless.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/printer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/video-display.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-favorite.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-important.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-photos.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-readonly.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-symbolic-link.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-unreadable.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-angel.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-crying.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-devilish.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-glasses.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-grin.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-kiss.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-monkey.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-plain.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-sad.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-smile-big.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-smile.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-surprise.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-wink.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/application-certificate.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/application-x-executable.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/audio-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/font-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/image-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/package-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-html.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-generic-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-script.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/video-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-address-book.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-calendar.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-document-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-document.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-drawing-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-drawing.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-presentation-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-presentation.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-spreadsheet-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-spreadsheet.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder-remote.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder-saved-search.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/network-server.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/network-workgroup.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/start-here.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-home.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-trash.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-high.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-low.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-medium.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-muted.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/battery-caution.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-information.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-warning.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-drag-accept.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-drag-accept.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-open.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-visiting.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-visiting.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/image-loading.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/image-missing.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/mail-attachment.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-idle.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-offline.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-transmit-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-transmit.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-wireless-encrypted.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/printer-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/software-update-available.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/software-update-urgent.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/user-trash-full.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-clear-night.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-clear.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-few-clouds-night.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-few-clouds.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-overcast.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-severe-alert.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-showers-scattered.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-showers.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-snow.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-storm.svg
/usr/share/shutter/resources/license/gplv3
/usr/share/shutter/resources/license/gplv3_hint
/usr/share/shutter/resources/po/shutter
/usr/share/shutter/resources/po/shutter-plugins
/usr/share/shutter/resources/po/shutter/af.po
/usr/share/shutter/resources/po/shutter/ar.po
/usr/share/shutter/resources/po/shutter/as.po
/usr/share/shutter/resources/po/shutter/ast.po
/usr/share/shutter/resources/po/shutter/bg.po
/usr/share/shutter/resources/po/shutter/bn.po
/usr/share/shutter/resources/po/shutter/bs.po
/usr/share/shutter/resources/po/shutter/ca.po
/usr/share/shutter/resources/po/shutter/cs.po
/usr/share/shutter/resources/po/shutter/da.po
/usr/share/shutter/resources/po/shutter/de.po
/usr/share/shutter/resources/po/shutter/el.po
/usr/share/shutter/resources/po/shutter/en_CA.po
/usr/share/shutter/resources/po/shutter/en_GB.po
/usr/share/shutter/resources/po/shutter/es.po
/usr/share/shutter/resources/po/shutter/et.po
/usr/share/shutter/resources/po/shutter/eu.po
/usr/share/shutter/resources/po/shutter/fi.po
/usr/share/shutter/resources/po/shutter/fo.po
/usr/share/shutter/resources/po/shutter/fr.po
/usr/share/shutter/resources/po/shutter/gl.po
/usr/share/shutter/resources/po/shutter/he.po
/usr/share/shutter/resources/po/shutter/hr.po
/usr/share/shutter/resources/po/shutter/hu.po
/usr/share/shutter/resources/po/shutter/id.po
/usr/share/shutter/resources/po/shutter/it.po
/usr/share/shutter/resources/po/shutter/ja.po
/usr/share/shutter/resources/po/shutter/kk.po
/usr/share/shutter/resources/po/shutter/ko.po
/usr/share/shutter/resources/po/shutter/lt.po
/usr/share/shutter/resources/po/shutter/lv.po
/usr/share/shutter/resources/po/shutter/ms.po
/usr/share/shutter/resources/po/shutter/nb.po
/usr/share/shutter/resources/po/shutter/nl.po
/usr/share/shutter/resources/po/shutter/nn.po
/usr/share/shutter/resources/po/shutter/oc.po
/usr/share/shutter/resources/po/shutter/pl.po
/usr/share/shutter/resources/po/shutter/pt.po
/usr/share/shutter/resources/po/shutter/pt_BR.po
/usr/share/shutter/resources/po/shutter/ro.po
/usr/share/shutter/resources/po/shutter/ru.po
/usr/share/shutter/resources/po/shutter/shutter.pot
/usr/share/shutter/resources/po/shutter/sk.po
/usr/share/shutter/resources/po/shutter/sl.po
/usr/share/shutter/resources/po/shutter/sr.po
/usr/share/shutter/resources/po/shutter/sv.po
/usr/share/shutter/resources/po/shutter/te.po
/usr/share/shutter/resources/po/shutter/th.po
/usr/share/shutter/resources/po/shutter/tr.po
/usr/share/shutter/resources/po/shutter/uk.po
/usr/share/shutter/resources/po/shutter/ur.po
/usr/share/shutter/resources/po/shutter/vi.po
/usr/share/shutter/resources/po/shutter/zh_CN.po
/usr/share/shutter/resources/po/shutter/zh_TW.po
/usr/share/shutter/resources/po/shutter-plugins/ar.po
/usr/share/shutter/resources/po/shutter-plugins/bg.po
/usr/share/shutter/resources/po/shutter-plugins/bs.po
/usr/share/shutter/resources/po/shutter-plugins/ca.po
/usr/share/shutter/resources/po/shutter-plugins/cs.po
/usr/share/shutter/resources/po/shutter-plugins/da.po
/usr/share/shutter/resources/po/shutter-plugins/de.po
/usr/share/shutter/resources/po/shutter-plugins/el.po
/usr/share/shutter/resources/po/shutter-plugins/en_CA.po
/usr/share/shutter/resources/po/shutter-plugins/en_GB.po
/usr/share/shutter/resources/po/shutter-plugins/es.po
/usr/share/shutter/resources/po/shutter-plugins/et.po
/usr/share/shutter/resources/po/shutter-plugins/fi.po
/usr/share/shutter/resources/po/shutter-plugins/fr.po
/usr/share/shutter/resources/po/shutter-plugins/gl.po
/usr/share/shutter/resources/po/shutter-plugins/he.po
/usr/share/shutter/resources/po/shutter-plugins/hr.po
/usr/share/shutter/resources/po/shutter-plugins/hu.po
/usr/share/shutter/resources/po/shutter-plugins/id.po
/usr/share/shutter/resources/po/shutter-plugins/it.po
/usr/share/shutter/resources/po/shutter-plugins/ja.po
/usr/share/shutter/resources/po/shutter-plugins/kk.po
/usr/share/shutter/resources/po/shutter-plugins/lt.po
/usr/share/shutter/resources/po/shutter-plugins/ms.po
/usr/share/shutter/resources/po/shutter-plugins/nb.po
/usr/share/shutter/resources/po/shutter-plugins/nl.po
/usr/share/shutter/resources/po/shutter-plugins/oc.po
/usr/share/shutter/resources/po/shutter-plugins/pl.po
/usr/share/shutter/resources/po/shutter-plugins/pt.po
/usr/share/shutter/resources/po/shutter-plugins/pt_BR.po
/usr/share/shutter/resources/po/shutter-plugins/ro.po
/usr/share/shutter/resources/po/shutter-plugins/ru.po
/usr/share/shutter/resources/po/shutter-plugins/shutter-plugins.pot
/usr/share/shutter/resources/po/shutter-plugins/sk.po
/usr/share/shutter/resources/po/shutter-plugins/sl.po
/usr/share/shutter/resources/po/shutter-plugins/sr.po
/usr/share/shutter/resources/po/shutter-plugins/sv.po
/usr/share/shutter/resources/po/shutter-plugins/th.po
/usr/share/shutter/resources/po/shutter-plugins/tr.po
/usr/share/shutter/resources/po/shutter-plugins/uk.po
/usr/share/shutter/resources/po/shutter-plugins/ur.po
/usr/share/shutter/resources/po/shutter-plugins/vi.po
/usr/share/shutter/resources/po/shutter-plugins/zh_CN.po
/usr/share/shutter/resources/po/shutter-plugins/zh_TW.po
/usr/share/shutter/resources/system/plugins
/usr/share/shutter/resources/system/plugins/perl
/usr/share/shutter/resources/system/plugins/shell
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3drotate
/usr/share/shutter/resources/system/plugins/perl/spbardistortion
/usr/share/shutter/resources/system/plugins/perl/spbordereffects
/usr/share/shutter/resources/system/plugins/perl/spnegate
/usr/share/shutter/resources/system/plugins/perl/sppolaroid
/usr/share/shutter/resources/system/plugins/perl/spresize
/usr/share/shutter/resources/system/plugins/perl/spsepia
/usr/share/shutter/resources/system/plugins/perl/spshadow
/usr/share/shutter/resources/system/plugins/perl/spwatermark
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/3Dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/3Drotate
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/sp3dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/sp3dreflection.svg
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/3Drotate
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/sp3drotate
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/sp3drotate.png
/usr/share/shutter/resources/system/plugins/perl/spbardistortion/spbardistortion
/usr/share/shutter/resources/system/plugins/perl/spbardistortion/spbardistortion.png
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/bordereffects
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/spbordereffects
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/spbordereffects.svg
/usr/share/shutter/resources/system/plugins/perl/spnegate/spnegate
/usr/share/shutter/resources/system/plugins/perl/spnegate/spnegate.svg
/usr/share/shutter/resources/system/plugins/perl/sppolaroid/sppolaroid
/usr/share/shutter/resources/system/plugins/perl/sppolaroid/sppolaroid.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/Locked.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/Unlocked.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/spresize
/usr/share/shutter/resources/system/plugins/perl/spresize/spresize.svg
/usr/share/shutter/resources/system/plugins/perl/spsepia/spsepia
/usr/share/shutter/resources/system/plugins/perl/spsepia/spsepia.svg
/usr/share/shutter/resources/system/plugins/perl/spshadow/spshadow
/usr/share/shutter/resources/system/plugins/perl/spshadow/spshadow.svg
/usr/share/shutter/resources/system/plugins/perl/spwatermark/spwatermark
/usr/share/shutter/resources/system/plugins/perl/spwatermark/spwatermark.svg
/usr/share/shutter/resources/system/plugins/shell/spaddlogo
/usr/share/shutter/resources/system/plugins/shell/spgrayscale
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2
/usr/share/shutter/resources/system/plugins/shell/spoffset
/usr/share/shutter/resources/system/plugins/shell/spraise
/usr/share/shutter/resources/system/plugins/shell/spsoftedges
/usr/share/shutter/resources/system/plugins/shell/spsunk
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper
/usr/share/shutter/resources/system/plugins/shell/sptrim
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/shutter_branding.png
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/spaddlogo
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/spaddlogo.svg
/usr/share/shutter/resources/system/plugins/shell/spgrayscale/spgrayscale
/usr/share/shutter/resources/system/plugins/shell/spgrayscale/spgrayscale.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/jigsaw
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw1
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw1.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw_1.png
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/jigsaw
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw2
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw2.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw_2.png
/usr/share/shutter/resources/system/plugins/shell/spoffset/spoffset
/usr/share/shutter/resources/system/plugins/shell/spoffset/spoffset.svg
/usr/share/shutter/resources/system/plugins/shell/spraise/spraise
/usr/share/shutter/resources/system/plugins/shell/spraise/spraise.svg
/usr/share/shutter/resources/system/plugins/shell/spsoftedges/spsoftedges
/usr/share/shutter/resources/system/plugins/shell/spsoftedges/spsoftedges.svg
/usr/share/shutter/resources/system/plugins/shell/spsunk/spsunk
/usr/share/shutter/resources/system/plugins/shell/spsunk/spsunk.svg
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper/sptornedpaper
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper/sptornedpaper.png
/usr/share/shutter/resources/system/plugins/shell/sptrim/sptrim
/usr/share/shutter/resources/system/plugins/shell/sptrim/sptrim.svg
/usr/share/sounds/freedesktop/stereo/camera-shutter.oga
/var/cache/apt/archives/shutter_0.87.2-0ubuntu1_all.deb
/var/lib/dpkg/info/shutter.list
/var/lib/dpkg/info/shutter.md5sums
/var/lib/dpkg/info/shutter.postinst
/var/lib/dpkg/info/shutter.postrm
```

---

### Post by amjjawad on 2011-11-04
> **Rodney9 said:**
> Well I just tried again with Screen lock, there are 2 of them in /usr/share/applications, it does seem to have worked, it is now in preferences. I thought that it would go on the main menu with logout as it said Settings.

So did you mange it to get it to work?

> 
This does give some hope, I don't know though which file to use for Shutter -


```
$ locate shutter
/home/rodney/.shutter
/home/rodney/.cache/shutter
/home/rodney/.cache/shutter/unsaved
/home/rodney/.config/autostart/shutter.desktop
/home/rodney/.shutter/accounts.xml
/home/rodney/.shutter/profiles
/home/rodney/.shutter/session.xml
/home/rodney/.shutter/settings.xml
/usr/bin/shutter
/usr/share/shutter
/usr/share/app-install/desktop/shutter:shutter.desktop
/usr/share/app-install/icons/shutter.png
**[COLOR=Red] /usr/share/applications/shutter.desktop[/COLOR]**
/usr/share/doc/shutter
/usr/share/doc/shutter/changelog.Debian.gz
/usr/share/doc/shutter/copyright
/usr/share/icons/Faenza/apps/16/shutter.png
/usr/share/icons/Faenza/apps/22/shutter.png
/usr/share/icons/Faenza/apps/24/shutter.png
/usr/share/icons/Faenza/apps/32/shutter.png
/usr/share/icons/Faenza/apps/48/shutter.png
/usr/share/icons/Faenza/apps/scalable/shutter.svg
/usr/share/icons/Faenza/status/22/shutter-panel.png
/usr/share/icons/Faenza/status/24/shutter-panel.png
/usr/share/icons/Faenza-Dark/status/22/shutter-panel.png
/usr/share/icons/Faenza-Dark/status/24/shutter-panel.png
/usr/share/icons/hicolor/128x128/apps/shutter.png
/usr/share/icons/hicolor/16x16/apps/shutter-panel.png
/usr/share/icons/hicolor/16x16/apps/shutter.png
/usr/share/icons/hicolor/192x192/apps/shutter.png
/usr/share/icons/hicolor/22x22/apps/shutter-panel.png
/usr/share/icons/hicolor/22x22/apps/shutter.png
/usr/share/icons/hicolor/24x24/apps/shutter-panel.png
/usr/share/icons/hicolor/24x24/apps/shutter.png
/usr/share/icons/hicolor/256x256/apps/shutter.png
/usr/share/icons/hicolor/32x32/apps/shutter.png
/usr/share/icons/hicolor/36x36/apps/shutter.png
/usr/share/icons/hicolor/48x48/apps/shutter.png
/usr/share/icons/hicolor/64x64/apps/shutter.png
/usr/share/icons/hicolor/72x72/apps/shutter.png
/usr/share/icons/hicolor/96x96/apps/shutter.png
/usr/share/icons/hicolor/scalable/apps/shutter-panel.svg
/usr/share/icons/hicolor/scalable/apps/shutter.svg
/usr/share/icons/ubuntu-mono-dark/16x16/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/22x22/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/24x24/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-dark/scalable/apps/shutter-panel.svg
/usr/share/icons/ubuntu-mono-light/16x16/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/22x22/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/24x24/apps/shutter-panel.png
/usr/share/icons/ubuntu-mono-light/scalable/apps/shutter-panel.svg
/usr/share/locale/af/LC_MESSAGES/shutter.mo
/usr/share/locale/ar/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ar/LC_MESSAGES/shutter.mo
/usr/share/locale/as/LC_MESSAGES/shutter.mo
/usr/share/locale/ast/LC_MESSAGES/shutter.mo
/usr/share/locale/bg/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/bg/LC_MESSAGES/shutter.mo
/usr/share/locale/bn/LC_MESSAGES/shutter.mo
/usr/share/locale/bs/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/bs/LC_MESSAGES/shutter.mo
/usr/share/locale/ca/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ca/LC_MESSAGES/shutter.mo
/usr/share/locale/cs/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/cs/LC_MESSAGES/shutter.mo
/usr/share/locale/da/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/da/LC_MESSAGES/shutter.mo
/usr/share/locale/de/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/de/LC_MESSAGES/shutter.mo
/usr/share/locale/el/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/el/LC_MESSAGES/shutter.mo
/usr/share/locale/en_CA/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/en_CA/LC_MESSAGES/shutter.mo
/usr/share/locale/en_GB/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/en_GB/LC_MESSAGES/shutter.mo
/usr/share/locale/es/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/es/LC_MESSAGES/shutter.mo
/usr/share/locale/et/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/et/LC_MESSAGES/shutter.mo
/usr/share/locale/eu/LC_MESSAGES/shutter.mo
/usr/share/locale/fi/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/fi/LC_MESSAGES/shutter.mo
/usr/share/locale/fo/LC_MESSAGES/shutter.mo
/usr/share/locale/fr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/fr/LC_MESSAGES/shutter.mo
/usr/share/locale/gl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/gl/LC_MESSAGES/shutter.mo
/usr/share/locale/he/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/he/LC_MESSAGES/shutter.mo
/usr/share/locale/hr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/hr/LC_MESSAGES/shutter.mo
/usr/share/locale/hu/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/hu/LC_MESSAGES/shutter.mo
/usr/share/locale/id/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/id/LC_MESSAGES/shutter.mo
/usr/share/locale/it/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/it/LC_MESSAGES/shutter.mo
/usr/share/locale/ja/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ja/LC_MESSAGES/shutter.mo
/usr/share/locale/kk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/kk/LC_MESSAGES/shutter.mo
/usr/share/locale/ko/LC_MESSAGES/shutter.mo
/usr/share/locale/lt/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/lt/LC_MESSAGES/shutter.mo
/usr/share/locale/lv/LC_MESSAGES/shutter.mo
/usr/share/locale/ms/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ms/LC_MESSAGES/shutter.mo
/usr/share/locale/nb/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/nb/LC_MESSAGES/shutter.mo
/usr/share/locale/nl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/nl/LC_MESSAGES/shutter.mo
/usr/share/locale/nn/LC_MESSAGES/shutter.mo
/usr/share/locale/oc/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/oc/LC_MESSAGES/shutter.mo
/usr/share/locale/pl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pl/LC_MESSAGES/shutter.mo
/usr/share/locale/pt/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pt/LC_MESSAGES/shutter.mo
/usr/share/locale/pt_BR/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/pt_BR/LC_MESSAGES/shutter.mo
/usr/share/locale/ro/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ro/LC_MESSAGES/shutter.mo
/usr/share/locale/ru/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ru/LC_MESSAGES/shutter.mo
/usr/share/locale/sk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sk/LC_MESSAGES/shutter.mo
/usr/share/locale/sl/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sl/LC_MESSAGES/shutter.mo
/usr/share/locale/sr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sr/LC_MESSAGES/shutter.mo
/usr/share/locale/sv/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/sv/LC_MESSAGES/shutter.mo
/usr/share/locale/te/LC_MESSAGES/shutter.mo
/usr/share/locale/th/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/th/LC_MESSAGES/shutter.mo
/usr/share/locale/tr/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/tr/LC_MESSAGES/shutter.mo
/usr/share/locale/uk/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/uk/LC_MESSAGES/shutter.mo
/usr/share/locale/ur/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/ur/LC_MESSAGES/shutter.mo
/usr/share/locale/vi/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/vi/LC_MESSAGES/shutter.mo
/usr/share/locale/zh_CN/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/zh_CN/LC_MESSAGES/shutter.mo
/usr/share/locale/zh_TW/LC_MESSAGES/shutter-plugins.mo
/usr/share/locale/zh_TW/LC_MESSAGES/shutter.mo
/usr/share/man/man1/shutter.1.gz
/usr/share/pixmaps/shutter.png
/usr/share/shutter/resources
/usr/share/shutter/update-notifier-shutter
/usr/share/shutter/resources/conf
/usr/share/shutter/resources/credits
/usr/share/shutter/resources/icons
/usr/share/shutter/resources/license
/usr/share/shutter/resources/po
/usr/share/shutter/resources/system
/usr/share/shutter/resources/conf/shape.conf
/usr/share/shutter/resources/credits/art
/usr/share/shutter/resources/credits/dev
/usr/share/shutter/resources/icons/Image.svg
/usr/share/shutter/resources/icons/Normal.cur
/usr/share/shutter/resources/icons/desktop.svg
/usr/share/shutter/resources/icons/document-send.svg
/usr/share/shutter/resources/icons/draw.svg
/usr/share/shutter/resources/icons/drawing_tool
/usr/share/shutter/resources/icons/executable.svg
/usr/share/shutter/resources/icons/fullscreen.svg
/usr/share/shutter/resources/icons/logo-imagebanana.png
/usr/share/shutter/resources/icons/logo-imageshack.png
/usr/share/shutter/resources/icons/lpi-bug.png
/usr/share/shutter/resources/icons/lpi-help.png
/usr/share/shutter/resources/icons/lpi-translate.png
/usr/share/shutter/resources/icons/notify.svg
/usr/share/shutter/resources/icons/sel_window.svg
/usr/share/shutter/resources/icons/sel_window_active.svg
/usr/share/shutter/resources/icons/sel_window_menu.svg
/usr/share/shutter/resources/icons/sel_window_section.svg
/usr/share/shutter/resources/icons/sel_window_tooltip.svg
/usr/share/shutter/resources/icons/selection.svg
/usr/share/shutter/resources/icons/shutter_cursor.png
/usr/share/shutter/resources/icons/shutter_cursor_frame.png
/usr/share/shutter/resources/icons/throbber.gif
/usr/share/shutter/resources/icons/throbber_16x16.gif
/usr/share/shutter/resources/icons/web_image.svg
/usr/share/shutter/resources/icons/drawing_tool/cursor
/usr/share/shutter/resources/icons/drawing_tool/draw-arrow.png
/usr/share/shutter/resources/icons/drawing_tool/draw-callouts.png
/usr/share/shutter/resources/icons/drawing_tool/draw-censor.png
/usr/share/shutter/resources/icons/drawing_tool/draw-ellipse.png
/usr/share/shutter/resources/icons/drawing_tool/draw-eraser.png
/usr/share/shutter/resources/icons/drawing_tool/draw-freehand.png
/usr/share/shutter/resources/icons/drawing_tool/draw-highlighter.png
/usr/share/shutter/resources/icons/drawing_tool/draw-image.svg
/usr/share/shutter/resources/icons/drawing_tool/draw-line.png
/usr/share/shutter/resources/icons/drawing_tool/draw-locked.png
/usr/share/shutter/resources/icons/drawing_tool/draw-lower.png
/usr/share/shutter/resources/icons/drawing_tool/draw-number.png
/usr/share/shutter/resources/icons/drawing_tool/draw-pixelize.png
/usr/share/shutter/resources/icons/drawing_tool/draw-pointer.png
/usr/share/shutter/resources/icons/drawing_tool/draw-raise.png
/usr/share/shutter/resources/icons/drawing_tool/draw-rectangle.png
/usr/share/shutter/resources/icons/drawing_tool/draw-text.png
/usr/share/shutter/resources/icons/drawing_tool/draw-unlocked.png
/usr/share/shutter/resources/icons/drawing_tool/objects
/usr/share/shutter/resources/icons/drawing_tool/transform-crop.png
/usr/share/shutter/resources/icons/drawing_tool/cursor/arrow
/usr/share/shutter/resources/icons/drawing_tool/cursor/censor
/usr/share/shutter/resources/icons/drawing_tool/cursor/ellipse
/usr/share/shutter/resources/icons/drawing_tool/cursor/freehand
/usr/share/shutter/resources/icons/drawing_tool/cursor/line
/usr/share/shutter/resources/icons/drawing_tool/cursor/number
/usr/share/shutter/resources/icons/drawing_tool/cursor/pixelize
/usr/share/shutter/resources/icons/drawing_tool/cursor/rect
/usr/share/shutter/resources/icons/drawing_tool/cursor/text
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library
/usr/share/shutter/resources/icons/drawing_tool/objects/apply.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/cssed.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/error-round.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/important-red.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/information-red.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/information-yellow.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/notice.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/question.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/star.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/stop-hand.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/tux.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/warning.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Alternate.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Diagonal Resize 1.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Diagonal Resize 2.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Handwriting.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Help.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Horizontal Resize.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Link.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Move.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Normal.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Precision.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Text.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Unavailable.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Cursors/Vertical Resize.cur
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_circle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_cloud_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rectangle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_round_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_rounded_rectangle_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_segmented_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_star_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_center_bottom.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_center_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_left_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Forms/Callouts/Callout_ubuntu_right_top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/address-book-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/appointment-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/bookmark-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/contact-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-open.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-print-preview.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-print.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-properties.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-save-as.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/document-save.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-clear.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-copy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-cut.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-delete.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-find-replace.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-find.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-paste.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-redo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-select-all.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/edit-undo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/folder-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-indent-less.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-indent-more.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-center.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-fill.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-left.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-justify-right.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-bold.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-italic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-strikethrough.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/format-text-underline.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-bottom.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-down.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-first.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-home.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-jump.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-last.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-next.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-previous.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-top.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/go-up.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/list-add.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/list-remove.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-mark-junk.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-message-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-reply-all.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-reply-sender.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/mail-send-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-eject.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-pause.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-start.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-playback-stop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-record.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-seek-backward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-seek-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-skip-backward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/media-skip-forward.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/process-stop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-lock-screen.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-log-out.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-search.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/system-shutdown.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/tab-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/view-fullscreen.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/view-refresh.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Actions/window-new.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-calculator.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-character-map.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/accessories-text-editor.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/help-browser.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-group-chat.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-mail.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-news-reader.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/internet-web-browser.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/office-calendar.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-accessibility.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-assistive-technology.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-font.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-keyboard-shortcuts.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-locale.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-multimedia.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-remote-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-screensaver.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-theme.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-wallpaper.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-network-proxy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-session.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-system-windows.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-file-manager.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-installer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-software-update.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/system-users.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/utilities-system-monitor.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/utilities-terminal.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-accessories.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-development.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-games.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-graphics.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-internet.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-multimedia.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-office.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-other.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/applications-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-desktop-peripherals.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Categories/preferences-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/audio-card.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/audio-input-microphone.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/battery.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/camera-photo.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/camera-video.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/computer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-harddisk.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-optical.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/drive-removable-media.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-gaming.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-keyboard.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/input-mouse.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-flash.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-floppy.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/media-optical.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/multimedia-player.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/network-wired.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/network-wireless.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/printer.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Devices/video-display.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-favorite.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-important.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-photos.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-readonly.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-symbolic-link.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-system.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emblems/emblem-unreadable.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-angel.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-crying.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-devilish.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-glasses.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-grin.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-kiss.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-monkey.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-plain.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-sad.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-smile-big.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-smile.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-surprise.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Emotes/face-wink.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/application-certificate.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/application-x-executable.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/audio-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/font-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/image-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/package-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-html.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-generic-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/text-x-script.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/video-x-generic.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-address-book.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-calendar.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-document-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-document.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-drawing-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-drawing.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-presentation-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-presentation.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-spreadsheet-template.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/MimeTypes/x-office-spreadsheet.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder-remote.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder-saved-search.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/folder.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/network-server.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/network-workgroup.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/start-here.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-desktop.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-home.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Places/user-trash.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-high.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-low.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-medium.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/audio-volume-muted.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/battery-caution.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-information.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/dialog-warning.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-drag-accept.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-drag-accept.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-open.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-visiting.icon
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/folder-visiting.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/image-loading.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/image-missing.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/mail-attachment.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-idle.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-offline.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-transmit-receive.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-transmit.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/network-wireless-encrypted.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/printer-error.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/software-update-available.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/software-update-urgent.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/user-trash-full.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-clear-night.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-clear.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-few-clouds-night.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-few-clouds.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-overcast.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-severe-alert.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-showers-scattered.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-showers.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-snow.svg
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Status/weather-storm.svg
/usr/share/shutter/resources/license/gplv3
/usr/share/shutter/resources/license/gplv3_hint
/usr/share/shutter/resources/po/shutter
/usr/share/shutter/resources/po/shutter-plugins
/usr/share/shutter/resources/po/shutter/af.po
/usr/share/shutter/resources/po/shutter/ar.po
/usr/share/shutter/resources/po/shutter/as.po
/usr/share/shutter/resources/po/shutter/ast.po
/usr/share/shutter/resources/po/shutter/bg.po
/usr/share/shutter/resources/po/shutter/bn.po
/usr/share/shutter/resources/po/shutter/bs.po
/usr/share/shutter/resources/po/shutter/ca.po
/usr/share/shutter/resources/po/shutter/cs.po
/usr/share/shutter/resources/po/shutter/da.po
/usr/share/shutter/resources/po/shutter/de.po
/usr/share/shutter/resources/po/shutter/el.po
/usr/share/shutter/resources/po/shutter/en_CA.po
/usr/share/shutter/resources/po/shutter/en_GB.po
/usr/share/shutter/resources/po/shutter/es.po
/usr/share/shutter/resources/po/shutter/et.po
/usr/share/shutter/resources/po/shutter/eu.po
/usr/share/shutter/resources/po/shutter/fi.po
/usr/share/shutter/resources/po/shutter/fo.po
/usr/share/shutter/resources/po/shutter/fr.po
/usr/share/shutter/resources/po/shutter/gl.po
/usr/share/shutter/resources/po/shutter/he.po
/usr/share/shutter/resources/po/shutter/hr.po
/usr/share/shutter/resources/po/shutter/hu.po
/usr/share/shutter/resources/po/shutter/id.po
/usr/share/shutter/resources/po/shutter/it.po
/usr/share/shutter/resources/po/shutter/ja.po
/usr/share/shutter/resources/po/shutter/kk.po
/usr/share/shutter/resources/po/shutter/ko.po
/usr/share/shutter/resources/po/shutter/lt.po
/usr/share/shutter/resources/po/shutter/lv.po
/usr/share/shutter/resources/po/shutter/ms.po
/usr/share/shutter/resources/po/shutter/nb.po
/usr/share/shutter/resources/po/shutter/nl.po
/usr/share/shutter/resources/po/shutter/nn.po
/usr/share/shutter/resources/po/shutter/oc.po
/usr/share/shutter/resources/po/shutter/pl.po
/usr/share/shutter/resources/po/shutter/pt.po
/usr/share/shutter/resources/po/shutter/pt_BR.po
/usr/share/shutter/resources/po/shutter/ro.po
/usr/share/shutter/resources/po/shutter/ru.po
/usr/share/shutter/resources/po/shutter/shutter.pot
/usr/share/shutter/resources/po/shutter/sk.po
/usr/share/shutter/resources/po/shutter/sl.po
/usr/share/shutter/resources/po/shutter/sr.po
/usr/share/shutter/resources/po/shutter/sv.po
/usr/share/shutter/resources/po/shutter/te.po
/usr/share/shutter/resources/po/shutter/th.po
/usr/share/shutter/resources/po/shutter/tr.po
/usr/share/shutter/resources/po/shutter/uk.po
/usr/share/shutter/resources/po/shutter/ur.po
/usr/share/shutter/resources/po/shutter/vi.po
/usr/share/shutter/resources/po/shutter/zh_CN.po
/usr/share/shutter/resources/po/shutter/zh_TW.po
/usr/share/shutter/resources/po/shutter-plugins/ar.po
/usr/share/shutter/resources/po/shutter-plugins/bg.po
/usr/share/shutter/resources/po/shutter-plugins/bs.po
/usr/share/shutter/resources/po/shutter-plugins/ca.po
/usr/share/shutter/resources/po/shutter-plugins/cs.po
/usr/share/shutter/resources/po/shutter-plugins/da.po
/usr/share/shutter/resources/po/shutter-plugins/de.po
/usr/share/shutter/resources/po/shutter-plugins/el.po
/usr/share/shutter/resources/po/shutter-plugins/en_CA.po
/usr/share/shutter/resources/po/shutter-plugins/en_GB.po
/usr/share/shutter/resources/po/shutter-plugins/es.po
/usr/share/shutter/resources/po/shutter-plugins/et.po
/usr/share/shutter/resources/po/shutter-plugins/fi.po
/usr/share/shutter/resources/po/shutter-plugins/fr.po
/usr/share/shutter/resources/po/shutter-plugins/gl.po
/usr/share/shutter/resources/po/shutter-plugins/he.po
/usr/share/shutter/resources/po/shutter-plugins/hr.po
/usr/share/shutter/resources/po/shutter-plugins/hu.po
/usr/share/shutter/resources/po/shutter-plugins/id.po
/usr/share/shutter/resources/po/shutter-plugins/it.po
/usr/share/shutter/resources/po/shutter-plugins/ja.po
/usr/share/shutter/resources/po/shutter-plugins/kk.po
/usr/share/shutter/resources/po/shutter-plugins/lt.po
/usr/share/shutter/resources/po/shutter-plugins/ms.po
/usr/share/shutter/resources/po/shutter-plugins/nb.po
/usr/share/shutter/resources/po/shutter-plugins/nl.po
/usr/share/shutter/resources/po/shutter-plugins/oc.po
/usr/share/shutter/resources/po/shutter-plugins/pl.po
/usr/share/shutter/resources/po/shutter-plugins/pt.po
/usr/share/shutter/resources/po/shutter-plugins/pt_BR.po
/usr/share/shutter/resources/po/shutter-plugins/ro.po
/usr/share/shutter/resources/po/shutter-plugins/ru.po
/usr/share/shutter/resources/po/shutter-plugins/shutter-plugins.pot
/usr/share/shutter/resources/po/shutter-plugins/sk.po
/usr/share/shutter/resources/po/shutter-plugins/sl.po
/usr/share/shutter/resources/po/shutter-plugins/sr.po
/usr/share/shutter/resources/po/shutter-plugins/sv.po
/usr/share/shutter/resources/po/shutter-plugins/th.po
/usr/share/shutter/resources/po/shutter-plugins/tr.po
/usr/share/shutter/resources/po/shutter-plugins/uk.po
/usr/share/shutter/resources/po/shutter-plugins/ur.po
/usr/share/shutter/resources/po/shutter-plugins/vi.po
/usr/share/shutter/resources/po/shutter-plugins/zh_CN.po
/usr/share/shutter/resources/po/shutter-plugins/zh_TW.po
/usr/share/shutter/resources/system/plugins
/usr/share/shutter/resources/system/plugins/perl
/usr/share/shutter/resources/system/plugins/shell
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3drotate
/usr/share/shutter/resources/system/plugins/perl/spbardistortion
/usr/share/shutter/resources/system/plugins/perl/spbordereffects
/usr/share/shutter/resources/system/plugins/perl/spnegate
/usr/share/shutter/resources/system/plugins/perl/sppolaroid
/usr/share/shutter/resources/system/plugins/perl/spresize
/usr/share/shutter/resources/system/plugins/perl/spsepia
/usr/share/shutter/resources/system/plugins/perl/spshadow
/usr/share/shutter/resources/system/plugins/perl/spwatermark
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/3Dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/3Drotate
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/sp3dreflection
/usr/share/shutter/resources/system/plugins/perl/sp3dreflection/sp3dreflection.svg
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/3Drotate
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/sp3drotate
/usr/share/shutter/resources/system/plugins/perl/sp3drotate/sp3drotate.png
/usr/share/shutter/resources/system/plugins/perl/spbardistortion/spbardistortion
/usr/share/shutter/resources/system/plugins/perl/spbardistortion/spbardistortion.png
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/bordereffects
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/spbordereffects
/usr/share/shutter/resources/system/plugins/perl/spbordereffects/spbordereffects.svg
/usr/share/shutter/resources/system/plugins/perl/spnegate/spnegate
/usr/share/shutter/resources/system/plugins/perl/spnegate/spnegate.svg
/usr/share/shutter/resources/system/plugins/perl/sppolaroid/sppolaroid
/usr/share/shutter/resources/system/plugins/perl/sppolaroid/sppolaroid.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/Locked.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/Unlocked.svg
/usr/share/shutter/resources/system/plugins/perl/spresize/spresize
/usr/share/shutter/resources/system/plugins/perl/spresize/spresize.svg
/usr/share/shutter/resources/system/plugins/perl/spsepia/spsepia
/usr/share/shutter/resources/system/plugins/perl/spsepia/spsepia.svg
/usr/share/shutter/resources/system/plugins/perl/spshadow/spshadow
/usr/share/shutter/resources/system/plugins/perl/spshadow/spshadow.svg
/usr/share/shutter/resources/system/plugins/perl/spwatermark/spwatermark
/usr/share/shutter/resources/system/plugins/perl/spwatermark/spwatermark.svg
/usr/share/shutter/resources/system/plugins/shell/spaddlogo
/usr/share/shutter/resources/system/plugins/shell/spgrayscale
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2
/usr/share/shutter/resources/system/plugins/shell/spoffset
/usr/share/shutter/resources/system/plugins/shell/spraise
/usr/share/shutter/resources/system/plugins/shell/spsoftedges
/usr/share/shutter/resources/system/plugins/shell/spsunk
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper
/usr/share/shutter/resources/system/plugins/shell/sptrim
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/shutter_branding.png
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/spaddlogo
/usr/share/shutter/resources/system/plugins/shell/spaddlogo/spaddlogo.svg
/usr/share/shutter/resources/system/plugins/shell/spgrayscale/spgrayscale
/usr/share/shutter/resources/system/plugins/shell/spgrayscale/spgrayscale.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/jigsaw
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw1
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw1.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw_1.png
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/jigsaw
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw2
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw2.svg
/usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw_2.png
/usr/share/shutter/resources/system/plugins/shell/spoffset/spoffset
/usr/share/shutter/resources/system/plugins/shell/spoffset/spoffset.svg
/usr/share/shutter/resources/system/plugins/shell/spraise/spraise
/usr/share/shutter/resources/system/plugins/shell/spraise/spraise.svg
/usr/share/shutter/resources/system/plugins/shell/spsoftedges/spsoftedges
/usr/share/shutter/resources/system/plugins/shell/spsoftedges/spsoftedges.svg
/usr/share/shutter/resources/system/plugins/shell/spsunk/spsunk
/usr/share/shutter/resources/system/plugins/shell/spsunk/spsunk.svg
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper/sptornedpaper
/usr/share/shutter/resources/system/plugins/shell/sptornedpaper/sptornedpaper.png
/usr/share/shutter/resources/system/plugins/shell/sptrim/sptrim
/usr/share/shutter/resources/system/plugins/shell/sptrim/sptrim.svg
/usr/share/sounds/freedesktop/stereo/camera-shutter.oga
/var/cache/apt/archives/shutter_0.87.2-0ubuntu1_all.deb
/var/lib/dpkg/info/shutter.list
/var/lib/dpkg/info/shutter.md5sums
/var/lib/dpkg/info/shutter.postinst
/var/lib/dpkg/info/shutter.postrm
```

**[COLOR=Red] /usr/share/applications/shutter.desktop[/COLOR]**

---

### Post by Rodney9 on 2011-11-04
Am I going crazy? 
As you so helpfully pointed out, locate shows 

```
/usr/share/applications/shutter.desktop
```

but in PCManFM I don't see shutter.desktop, I do have hidden to show
although good old faithful Midnight Commander does show it ???

anyway it doesn't appear in the menu either

```
[Desktop Entry]
Version=1.0
Name=Capture the current active window
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter --active
Icon=shutter
Terminal=false
Type=Application
Categories=Utility
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active
#OnlyShowIn=Unity
#NoDisplay=true
Categories=Accessories
```

I'm sorry to waste your time on this little thing, I'll just have to learn to live with it. Lubuntu is such a marvellous OS, none can be perfect.

Rodney

---

### Post by amjjawad on 2011-11-04
> **Rodney9 said:**
> Am I going crazy? 
As you so helpfully pointed out, locate shows 

```
/usr/share/applications/shutter.desktop
```but in PCManFM I don't see shutter.desktop, I do have hidden to show
although good old faithful Midnight Commander does show it ???

anyway it doesn't appear in the menu either


What does:

```
sudo leafpad /usr/share/applications/shutter.desktop
```show?


```
[Desktop Entry]
Version=1.0
Name=Capture the current active window
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter --active
Icon=shutter
Terminal=false
Type=Application
[COLOR=Red] Categories=Utility
[/COLOR]MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
[COLOR=Red]X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active
[/COLOR]#OnlyShowIn=Unity
#NoDisplay=true
[COLOR=Black]Categories=Accessories[/COLOR]
```So, how did you get that?
By the way, the red lines are unneeded IMHO. I'm not on Linux right.

> 
I'm sorry to waste your time on this little thing, I'll just have to learn to live with it. Lubuntu is such a marvellous OS, none can be perfect.
You are NOT wasting my time, please stop saying that :)
I'm here to help and support each one. If I help one user to fix his/her problem, that is an achievement :)

---

### Post by Rodney9 on 2011-11-04
> What does:

sudo leafpad /usr/share/applications/shutter.desktop
show?


```
[Desktop Entry]
Version=1.0
Name=Capture the current active window
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter --active
Icon=shutter
Terminal=false
Type=Application
#Categories=Utility
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
#X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active
#OnlyShowIn=Unity
#NoDisplay=true
Categories=Accessories
```

> So, how did you get that?
sudo leafpad /usr/share/applications/shutter.desktop

I'm not totally useless :)

But still not in the menu :(

Rodney

---

### Post by amjjawad on 2011-11-04
I need to switch machines and go to my Linux PC. Will check the file from there and post mine for you to compare. When I installed Shutter, I didn't have to do anything.

This is 11.10 right?

---

### Post by Rodney9 on 2011-11-04
> This is 11.10 right?  Yes

---

### Post by amjjawad on 2011-11-04
> **Rodney9 said:**
> Yes

I'm on 11.04 but that shouldn't be a problem IMHO.

Mine is:

```
[Desktop Entry]
Version=1.0
Name=Shutter
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter %F
Icon=shutter
Terminal=false
Type=Application
Categories=Utility;Application;
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active

[Select Shortcut Group]
Name=Capture an area of the screen
Exec=shutter --select
OnlyShowIn=Unity

[Screen Shortcut Group]
Name=Capture the entire screen
Exec=shutter --full
OnlyShowIn=Unity

[Window Shortcut Group]
Name=Select a window to capture
Exec=shutter --window
OnlyShowIn=Unity

[Active Shortcut Group]
Name=Capture the current active window
Exec=shutter --active
OnlyShowIn=Unity


```

---

### Post by Rodney9 on 2011-11-04
> **amjjawad said:**
> I'm on 11.04 but that shouldn't be a problem IMHO.

Mine is:

```
[Desktop Entry]
Version=1.0
Name=Shutter
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter %F
Icon=shutter
Terminal=false
Type=Application
Categories=Utility;Application;
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active

[Select Shortcut Group]
Name=Capture an area of the screen
Exec=shutter --select
OnlyShowIn=Unity

[Screen Shortcut Group]
Name=Capture the entire screen
Exec=shutter --full
OnlyShowIn=Unity

[Window Shortcut Group]
Name=Select a window to capture
Exec=shutter --window
OnlyShowIn=Unity

[Active Shortcut Group]
Name=Capture the current active window
Exec=shutter --active
OnlyShowIn=Unity


```

***[SIZE="4"]That worked ![/SIZE]***

Why is yours different ?

Did you install Alarm Clock, if so , can I see it's as well ?

Rodney

---

### Post by amjjawad on 2011-11-04
> **Rodney9 said:**
> ***[SIZE=4]That worked ![/SIZE]***
Fabulous :D


>  Why is yours different ?
I don't know, I didn't even touched it. As I mentioned, when I installed Shutter, it was there in my Menu already and didn't have to do anything. I must test that on 11.10 to see what is going on :)


>  Did you install Alarm Clock, if so , can I see it's as well ?
It's 8am and I'm still awake :D I told you, I have sleeping problems :P

I may do that later or soon, who knows? :P

---

### Post by Rodney9 on 2011-11-04
Rest, You have helped me enough for one day.

Thank You
Rodney

---

### Post by amjjawad on 2011-11-05
> **Rodney9 said:**
> Rest, You have helped me enough for one day.

Thank You
Rodney

We are in LOSG, remember? I can't let it go ;)

What is the name of the package? alarm-clock?

---

### Post by amjjawad on 2011-11-05
Will be in Menu > Accessories
 
```
[Desktop Entry]
Version=1.0
Name=Alarm Clock
Name[pl]=Budzik
Name[pt]=Relógio Despertador
Comment=Schedule your tasks
Comment[pl]=Budzik dla &#347;rodowiska GNOME
Comment[pt]=Agende as suas tarefas

Name[sr]=&#1041;&#1091;&#1076;&#1080;&#1083;&#1085;&#1080;&#1082;
Name[sr@latin]=Budilnik
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112;&#1090;&#1077; &#1042;&#1072;&#1096;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;
Comment[sr@latin]=Organizujte Va&#353;e vreme

Exec=alarmclock
Terminal=false
Type=Application
Categories=GNOME;GTK;Utility;
Icon=alarm-clock
StartupNotify=false[B][COLOR=Red]
#OnlyShowIn=GNOME;[/COLOR][/B]
```

---

### Post by Rodney9 on 2011-11-05
Thank You

Something funny in 11.10 ???

---

### Post by amjjawad on 2011-11-05
> **Rodney9 said:**
> Thank You

Something funny in 11.10 ???

I slept for 3 hours only :D

What do you mean something funny? sorry, I'm not following :)

Hey, I see everything is there :D good job!

---

### Post by Rodney9 on 2011-11-05
> What do you mean something funny? sorry, I'm not following

Well, in your Lubuntu 11.04 it works, the files are different in 11.10, but went I copy yours it works.

So something is funny/wrong/faulty/bug in 11.10

Rodney

---

### Post by amjjawad on 2011-11-05
> **Rodney9 said:**
> Well, in your Lubuntu 11.04 it works, the files are different in 11.10, but went I copy yours it works.

So something is funny/wrong/faulty/bug in 11.10

Rodney

I'm testing that on my other test PC. It has both 11.04 and 11.10 so I'll install Shutter and Alarm Clock and see what is going on :)

---

### Post by amjjawad on 2011-11-05
Shutter has lots of dependencies!

Downloading in progress ...

---

### Post by amjjawad on 2011-11-05
```
[Desktop Entry]
Version=1.0
Name=Alarm Clock
Name[pl]=Budzik
Name[pt]=Relógio Despertador
Comment=Schedule your tasks
Comment[pl]=Budzik dla &#347;rodowiska GNOME
Comment[pt]=Agende as suas tarefas

Name[sr]=&#1041;&#1091;&#1076;&#1080;&#1083;&#1085;&#1080;&#1082;
Name[sr@latin]=Budilnik
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112;&#1090;&#1077; &#1042;&#1072;&#1096;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;
Comment[sr@latin]=Organizujte Va&#353;e vreme

Exec=alarmclock
Terminal=false
Type=Application
Categories=GNOME;GTK;Utility;
Icon=alarm-clock
StartupNotify=false
OnlyShowIn=GNOME;

```

```
[Desktop Entry]
Version=1.0
Name=Shutter
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter %F
Icon=shutter
Terminal=false
Type=Application
Categories=Utility;Application;
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
X-Ayatana-Desktop-Shortcuts=Select;Screen;Window;Active

[Select Shortcut Group]
Name=Capture an area of the screen
Exec=shutter --select
OnlyShowIn=Unity

[Screen Shortcut Group]
Name=Capture the entire screen
Exec=shutter --full
OnlyShowIn=Unity

[Window Shortcut Group]
Name=Select a window to capture
Exec=shutter --window
OnlyShowIn=Unity

[Active Shortcut Group]
Name=Capture the current active window
Exec=shutter --active
OnlyShowIn=Unity


```

Edit:
I don't see any differences between my files on 11.04 and my files on 11.10 but I noticed that your Shutter's File on 11.10 is different than mine for some weird reason?!
How did you install it? have you updated your system before you do that?

```
sudo apt-get update
```
or
Reload from Synaptic?

---

### Post by Rodney9 on 2011-11-05
I don't know, I am up to date. 64bit maybe ? I'm guessing .

Rodney

---

### Post by amjjawad on 2011-11-05
> **Rodney9 said:**
> I don't know, I am up to date. 64bit maybe ? I'm guessing .

Rodney

No, that should not be a problem at all.
So, everything is working now? :)

---

### Post by Rodney9 on 2011-11-05
> So, everything is working now?

Yes, with your files.

Get 5 hours at least !

Sleep well

Rodney

---

### Post by amjjawad on 2011-11-05
> **Rodney9 said:**
> Yes, with your files.

Get those 5 hours at least !

Hahaha, I'm trying :D

---

### Post by Gracie4000 on 2011-12-12
#NoDisplay=true

Instead of remarking out the NoDisplay=true line, try changing it to 
NoDisplay=false (without the '#' of course).

Perhaps that will work?

---

### Post by GeForce 9500GT on 2012-10-09
Alacarte doesn't really work under Lubuntu is my experience. You better can use:
 
[LXMED]("http://sourceforge.net/projects/lxmed/") - **_LX_**DE **_M_**enu **_E_**ditor
 
I'm using another menu editor as well which has a better GUI lay-out. I'll check for you later what the name of that tool is.

---

### Post by Elfy on 2012-10-09
Old thread closed.

---

