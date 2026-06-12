---
title: "Fonts not rendering properly in KDE applications"
date: 2010-01-25
forum: General Help
---

### Post by spiritofelric on 2010-01-25
I've seen a few people are having this issue, so i wanted to start a main thread.

:frown: My problem started...
-----------------------------
After installing qt4-designer onto my Ubuntu 9.10 Gnome OS, the fonts in certain applications looked distorted like enlarged bitmaps.  I tried uninstalling designer, reinstalling components, using qt4-config to restore fonts, but nothing has fixed this issue.

:shock: Scope...
------------------
The issue seems to be specific to KDE applications such as: qt4-config, Amarok v2.2.0, skype, akonaditray, ktorrent, etc. Also, in qt4-config it seems to be specific to fonts between the sizes 9 to 12 inclusive for all font faces. All other font sizes seem to be okay.

I've attached some examples.

:-k Cause...
----------------
When i first tried to install qt4-designer, it indicated the following dependancies: fontconfig-config libfontconfig1 libfontconfig1-dev
When i try to remove fontconfig-config, it indicates that it is dependent on nearly every application in my system (including drivers and xscreen). Hence, I would need to uninstall everything and reinstall everything!?

[-o< Fix...
-------------
I've logged a bug report with QT: [http://bugreports.qt.nokia.com/browse/QTBUG-7543](http://bugreports.qt.nokia.com/browse/QTBUG-7543)

Not sure where else to look.

---

### Post by Michalxo on 2010-01-25
I think that cause is something with fontconfig. For me works this, but I am unable to set subpixles for LCD screen :-(

Try this:
create
```

gedit ~/.fonts.conf

```
and paste to it for instance this:
```

<?xml version='1.0'?>
 <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
 <fontconfig>
  <match target="font" >
   <edit mode="assign" name="rgba" >
    <const>rgb</const>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hinting" >
    <bool>true</bool>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hintstyle" >
    <const>hintslight</const>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="antialias" >
    <bool>true</bool>
   </edit>
  </match>
 </fontconfig>

```

There are more possibilities of variables (hintslight / hintmedium / hintfull...)
I am stuck for more info about this. And I think this is more bigger bug then just in "firefox-3.6" and vlc like in my case.
btw, I am using Karmic (9.10) 32bit

Search for similar codes on forum to get more specific settings. I found 2 "similar" threads around, which I don't have link for now...

maybe this can be the cause:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761)
[http://ubuntuforums.org/showthread.php?t=1128929&page=7](http://ubuntuforums.org/showthread.php?t=1128929&page=7)

---

### Post by spiritofelric on 2010-01-26
Thanks!  That actually works for all the applications I see being impacted.

---

