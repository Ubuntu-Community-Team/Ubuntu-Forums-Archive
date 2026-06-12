---
title: "install tar packages?"
date: 2009-07-31
forum: General Help
---

### Post by stlsaint on 2009-07-31
i downloaded a open source tar package from sourceforge but once i extract it i cannot figure out how to install it!!

---

### Post by jerome1232 on 2009-07-31
What is it. You have a link? Is there a README or INSTALL file or some such in there? Did you read said file?

---

### Post by Tclarkie on 2009-07-31
install giftwrap in add/remove and then select the .tar

---

### Post by stlsaint on 2009-07-31
> **jerome1232 said:**
> What is it. You have a link? Is there a README or INSTALL file or some such in there? Did you read said file?


the info file gives nothing!!
heres what ls -la gives me from inside the directory containing the tar...


stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13/CS_MinInstaller_5_13$ ls -la
total 84
drwxr-xr-x 11 stlsaint stlsaint 4096 2009-07-31 19:48 .
drwxr-xr-x  3 stlsaint stlsaint 4096 2009-07-31 19:46 ..
drwxr-xr-x  4 stlsaint stlsaint 4096 2009-03-04 20:05 com
-rw-r--r--  1 stlsaint stlsaint   58 2009-07-28 19:13 customData
-rw-r--r--  1 stlsaint stlsaint   82 2009-07-28 19:13 dynvariables
-rw-r--r--  1 stlsaint stlsaint  440 2009-07-28 19:13 GUIPrefs
drwxr-xr-x  2 stlsaint stlsaint 4096 2009-02-28 00:34 img
-rw-r--r--  1 stlsaint stlsaint  804 2009-07-28 19:13 info
-rw-r--r--  1 stlsaint stlsaint   58 2009-07-28 19:13 installerrequirements
drwxr-xr-x  2 stlsaint stlsaint 4096 2009-07-31 19:46 langpacks
-rw-r--r--  1 stlsaint stlsaint   64 2009-07-28 19:13 langpacks.info
drwxr-xr-x  3 stlsaint stlsaint 4096 2009-03-04 20:05 META-INF
drwxr-xr-x  2 stlsaint stlsaint 4096 2009-07-31 19:46 native
drwxr-xr-x  3 stlsaint stlsaint 4096 2009-03-04 20:05 net
drwxr-xr-x  3 stlsaint stlsaint 4096 2009-03-04 20:05 org
drwxr-xr-x  2 stlsaint stlsaint 4096 2009-07-31 19:48 packs
-rw-r--r--  1 stlsaint stlsaint 1316 2009-07-28 19:15 packs.info
-rw-r--r--  1 stlsaint stlsaint  926 2009-07-28 19:13 panelsOrder
drwxr-xr-x  2 stlsaint stlsaint 4096 2009-07-31 19:46 res
-rw-r--r--  1 stlsaint stlsaint   82 2009-07-28 19:13 rules
-rw-r--r--  1 stlsaint stlsaint  253 2009-07-28 19:13 vars

---

### Post by stlsaint on 2009-07-31
> **Tclarkie said:**
> install giftwrap in add/remove and then select the .tar



what is giftwrap...its not in add/remove nor sudo apt-get

---

### Post by stlsaint on 2009-07-31
Sorry my mistake i meant a _jar_ package!!

---

### Post by jerome1232 on 2009-07-31
You don't extract the jar, you run it with java.

Make sure suns java jre is installed (look in synaptic)

Then run it with

```
java -jar /path/to/jar
```

---

### Post by stlsaint on 2009-07-31
yea after 8hours i finally figured that out like a fool...ubuntu was telling me what to do the whole time i was just blind!! so i used java and got this error towards the end of install...

/bin/chmod: cannot access '/usr/local/churchsoftware/install_linux_fonts.sh

then i hit ok and get this...

java.io.IOException: Cannot run program "/usr/local/churchsoftware/install linux fonts.sh": java.io.IOException: error=2, No such file or directory

whats all this because i see the file in my usr/local folder??!!

---

### Post by jerome1232 on 2009-07-31
Looks to me like the installer failed while trying to change permissions on that file, saying it could not access it.

One thing that strikes me as odd is it's listed as two different file names.

First it's install_linux_fonts.sh
then it's install linux fonts.sh

What are the permissions on that file and what is it actually named?

---

### Post by stlsaint on 2009-07-31
> **jerome1232 said:**
> Looks to me like the installer failed while trying to change permissions on that file, saying it could not access it.

One thing that strikes me as odd is it's listed as two different file names.

First it's install_linux_fonts.sh
then it's install linux fonts.sh

What are the permissions on that file and what is it actually named?


permissions for package
stlsaint@stlsaint-laptop:~/churchsoftware$ ls -l
total 134860
-rw-r--r-- 1 stlsaint stlsaint 137956231 2009-07-31 20:55 CS_MinInstaller_5_13.jar
stlsaint@stlsaint-laptop:~/churchsoftware$

---

### Post by jerome1232 on 2009-07-31
I meant on /usr/local/churchsoftware/install linux fonts.sh

or

/usr/local/churchsoftware/install_linux_fonts.sh

whatever it's named.

---

### Post by stlsaint on 2009-07-31
honestly i cant find it!!

---

### Post by stlsaint on 2009-07-31
what if i just gave the whole folder permissions...you think that would work?

---

### Post by stlsaint on 2009-07-31
heres ls of that dir


stlsaint@stlsaint-laptop:/usr/local/churchsoftware$ ls
backup
bgobj.db
bibleconvertor
bibles
brp.prop
celebrations.ref
church_background.jpg
church_calendar
church_db
church.jar
church.png
Church-Software-1249092602028.desktop
Church-Software-1249093528863.desktop
Church-Software-1249093528999.desktop
countries.txt
ctxhelper
currencies.txt
defaultfontstyle.prop
default.m3u
docs
essentials_linux
favorites
icons
install.log
Install_V5.13_20090731210922_2368026955050238608.log
Install_V5.13_20090731211452_791236470949633576.log
Install_V5.13_20090731211946_3979794863301496656.log
Install_V5.13_20090731212123_6136964755977684388.log
IzPackLocaleEnabledXdgDesktopIconScript.sh
jlgui.ini
jmf.properties
language_defaults.prop
language.prop
lib
library
licenses
log4j.xml
logs
menus
MessagesBundle.properties
native
plugins
preferences
settings
skins
soundbank.gm
source_code.tar.gz
start.sh
swui.prop
temp
templates
theme.properties
themes.xml
topics
transitions.xml
transliteration
Uninstaller
Uninstaller-1249092602133.desktop
Uninstaller-1249093528956.desktop
Uninstaller-1249093529086.desktop
User-Guide-1249092602075.desktop
User-Guide-1249093528916.desktop
User-Guide-1249093529046.desktop
xsl

---

### Post by br4d on 2009-07-31
Perhaps the log file can tell something. What is the content of install.log?

---

### Post by stlsaint on 2009-07-31
here is log...hope your ready....


/usr/local/churchsoftware/templates/Pink Painted Border on Green.jpg
/usr/local/churchsoftware/templates/[Animated]_123-1.gif
/usr/local/churchsoftware/templates/Digits.jpg
/usr/local/churchsoftware/icons/Default/menus/global.gif
/usr/local/churchsoftware/icons/Default/flags/bg.gif
/usr/local/churchsoftware/icons/Default/menus/opensong.gif
/usr/local/churchsoftware/templates/Guitar (Pencil Design).jpg
/usr/local/churchsoftware/templates/Repent At Cross.jpg
/usr/local/churchsoftware/native/jmmpegv.dll
/usr/local/churchsoftware/lib/junit-3.8.1.jar
/usr/local/churchsoftware/licenses/english_bibles/gw-copyright.txt
/usr/local/churchsoftware/menus/tamil.ui
/usr/local/churchsoftware/icons/Default/flags/ge.gif
/usr/local/churchsoftware/icons/Default/menus/lyrics.gif
/usr/local/churchsoftware/icons/Default/flags/pf.gif
/usr/local/churchsoftware/brp.prop
/usr/local/churchsoftware/native/jmvh263.dll
/usr/local/churchsoftware/icons/Default/flags/si.gif
/usr/local/churchsoftware/templates/Light Blue Center Gradient.jpg
/usr/local/churchsoftware/icons/big/bigLoad.gif
/usr/local/churchsoftware/licenses/softwares/apache-1.1.txt
/usr/local/churchsoftware/icons/Default/flags/st.gif
/usr/local/churchsoftware/templates/Red Background.jpg
/usr/local/churchsoftware/icons/big/bigPlay.gif
/usr/local/churchsoftware/templates/Rainbow (God's Covenant with every living creature).jpg
/usr/local/churchsoftware/menus/korean.ui
/usr/local/churchsoftware/icons/Default/menus/songs2.gif
/usr/local/churchsoftware/ctxhelper/live_templates/special_song.html
/usr/local/churchsoftware/templates/Blue Sky (Clouds).jpg
/usr/local/churchsoftware/native/libjmgsm.so
/usr/local/churchsoftware/ctxhelper/live_templates/church_timings.html
/usr/local/churchsoftware/icons/little/littleShuffle.gif
/usr/local/churchsoftware/lib/chardet.jar
/usr/local/churchsoftware/lib/serializer.jar
/usr/local/churchsoftware/native/libjmcvid.so
/usr/local/churchsoftware/templates/Eagle Wings.jpg
/usr/local/churchsoftware/bibleconvertor/html/about.html
/usr/local/churchsoftware/icons/Default/flags/mz.gif
/usr/local/churchsoftware/templates/White DesignBorder On Blue.jpg
/usr/local/churchsoftware/default.m3u
/usr/local/churchsoftware/licenses/lang_bibles/wbtc-copyright.txt
/usr/local/churchsoftware/menus/chinesesimplified.ui
/usr/local/churchsoftware/icons/Default/menus/delgroup.gif
/usr/local/churchsoftware/icons/Default/flags/tz.gif
/usr/local/churchsoftware/icons/big/bigRepeat.gif
/usr/local/churchsoftware/templates/Blank Screen.png
/usr/local/churchsoftware/icons/Default/flags/cr.gif
/usr/local/churchsoftware/icons/Default/menus/camerasettings.gif
/usr/local/churchsoftware/icons/Default/flags/sg.gif
/usr/local/churchsoftware/icons/Default/menus/parallel.gif
/usr/local/churchsoftware/icons/Default/flags/kg.gif
/usr/local/churchsoftware/icons/Default/flags/pk.gif
/usr/local/churchsoftware/icons/Default/misc/ring_preview.gif
/usr/local/churchsoftware/templates/Black Border on White.jpg
/usr/local/churchsoftware/icons/Default/flags/cn.gif
/usr/local/churchsoftware/templates/Waterfall (DarkGray).jpg
/usr/local/churchsoftware/lib/jxl.jar
/usr/local/churchsoftware/icons/Default/buttons/lyrics.gif
/usr/local/churchsoftware/icons/Default/flags/yt.gif
/usr/local/churchsoftware/menus/norwegian.ui
/usr/local/churchsoftware/templates/Flower (Gray Background).jpg
/usr/local/churchsoftware/xsl/cswing/simple.xsl
/usr/local/churchsoftware/icons/Default/flags/mc.gif
/usr/local/churchsoftware/icons/Default/menus/restore.gif
/usr/local/churchsoftware/bibleconvertor/thml/testament.head
/usr/local/churchsoftware/icons/Default/menus/fonts.gif
/usr/local/churchsoftware/icons/Default/menus/calendar.gif
/usr/local/churchsoftware/templates/Pink Border.jpg
/usr/local/churchsoftware/icons/Default/flags/rw.gif
/usr/local/churchsoftware/icons/Default/flags/mn.gif
/usr/local/churchsoftware/icons/Default/flags/gl.gif
/usr/local/churchsoftware/lib/multiplayer_linux.jar
/usr/local/churchsoftware/bibleconvertor/thml/chapter.head
/usr/local/churchsoftware/licenses/english_bibles/bbe-copyright.txt
/usr/local/churchsoftware/templates/Bible Reading (Blue).jpg
/usr/local/churchsoftware/icons/Default/flags/im.gif
/usr/local/churchsoftware/templates/Music (Pink background).jpg
/usr/local/churchsoftware/licenses/lang_bibles/bssa-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/topics.gif
/usr/local/churchsoftware/templates/Praying Hands (Brown Background).jpg
/usr/local/churchsoftware/templates/Butterfly and Blue Background.jpg
/usr/local/churchsoftware/icons/Default/buttons/edit.gif
/usr/local/churchsoftware/templates/Blue Styled Border.jpg
/usr/local/churchsoftware/lib/looks-1.3.2.jar
/usr/local/churchsoftware/icons/Default/flags/ee.gif
/usr/local/churchsoftware/icons/big/bigClear.gif
/usr/local/churchsoftware/icons/cs_icon.ico
/usr/local/churchsoftware/icons/little/littleClear.gif
/usr/local/churchsoftware/menus/hindi.ui
/usr/local/churchsoftware/templates/Blue Globe.jpg
/usr/local/churchsoftware/licenses/softwares/jmf-2.1.1.txt
/usr/local/churchsoftware/icons/Default/menus/display.gif
/usr/local/churchsoftware/menus/danish.ui
/usr/local/churchsoftware/templates/White DesignBorder On DarkGreen.jpg
/usr/local/churchsoftware/lib/icu4j-4_0_1.jar
/usr/local/churchsoftware/icons/left_right.gif
/usr/local/churchsoftware/menus/turkish.ui
/usr/local/churchsoftware/menus/english.ui
/usr/local/churchsoftware/bibleconvertor/html/chapter.toc.html.foot
/usr/local/churchsoftware/icons/Default/menus/adduser.gif
/usr/local/churchsoftware/licenses/english_bibles/ajkv-copyright.txt
/usr/local/churchsoftware/bibleconvertor/html/book.toc.html.foot
/usr/local/churchsoftware/icons/Default/flags/ml.gif
/usr/local/churchsoftware/icons/Default/flags/az.gif
/usr/local/churchsoftware/icons/Default/flags/pt.gif
/usr/local/churchsoftware/bibleconvertor/html/toc.hhc.book.head
/usr/local/churchsoftware/icons/Default/menus/update.gif
/usr/local/churchsoftware/templates/Note (Green).jpg
/usr/local/churchsoftware/backup/README.txt
/usr/local/churchsoftware/icons/Default/flags/td.gif
/usr/local/churchsoftware/icons/Default/flags/la.gif
/usr/local/churchsoftware/licenses/websites/gpl-3.0.html
/usr/local/churchsoftware/icons/k5nCal/Search24.gif
/usr/local/churchsoftware/bibleconvertor/sword/title
/usr/local/churchsoftware/templates/Ocean.jpg
/usr/local/churchsoftware/templates/Red Back Design.jpg
/usr/local/churchsoftware/icons/Default/flags/at.gif
/usr/local/churchsoftware/icons/Default/menus/bible.gif
/usr/local/churchsoftware/icons/Default/flags/vn.gif
/usr/local/churchsoftware/icons/Default/menus/text.gif
/usr/local/churchsoftware/licenses/english_bibles/net-copyright.html
/usr/local/churchsoftware/icons/k5nCal/k5nCal-256x256.png
/usr/local/churchsoftware/templates/Red Flower on Greed Background.jpg
/usr/local/churchsoftware/icons/Default/buttons/login.gif
/usr/local/churchsoftware/bibleconvertor/html/html.title
/usr/local/churchsoftware/icons/Default/flags/it.gif
/usr/local/churchsoftware/menus/japanese.ui
/usr/local/churchsoftware/ctxhelper/first_use/gbc.zip
/usr/local/churchsoftware/icons/splash.jpg
/usr/local/churchsoftware/templates/Cross (Crystal Background).jpg
/usr/local/churchsoftware/icons/Default/flags/hm.gif
/usr/local/churchsoftware/lib/jmf_linux.jar
/usr/local/churchsoftware/icons/Default/menus/logs.gif
/usr/local/churchsoftware/icons/Default/flags/pw.gif
/usr/local/churchsoftware/templates/Praise God (Yellow Background).jpg
/usr/local/churchsoftware/icons/Default/flags/zm.gif
/usr/local/churchsoftware/icons/k5nCal/k5nCal-128x128.png
/usr/local/churchsoftware/templates/DarkBlue Line Border.jpg
/usr/local/churchsoftware/templates/Blue Background.jpg
/usr/local/churchsoftware/templates/Music (Harp).jpg
/usr/local/churchsoftware/menus/albanian.ui
/usr/local/churchsoftware/icons/Default/menus/o2e.gif
/usr/local/churchsoftware/templates/Music (Black Background).jpg
/usr/local/churchsoftware/licenses/websites-licidx.prop
/usr/local/churchsoftware/templates/Bible Reading (Green).jpg
/usr/local/churchsoftware/icons/little/littleEject.gif
/usr/local/churchsoftware/icons/k5nCal/k5nCal-256x256.xcf
/usr/local/churchsoftware/native/jmcvid.dll
/usr/local/churchsoftware/icons/Default/flags/cl.gif
/usr/local/churchsoftware/templates/Pink Flower (Gray Background).jpg
/usr/local/churchsoftware/icons/Default/menus/events.gif
/usr/local/churchsoftware/templates/Birthday Celebrations.jpg
/usr/local/churchsoftware/lib/icu4j-localespi-4_0_1.jar
/usr/local/churchsoftware/icons/little/littleLoad.gif
/usr/local/churchsoftware/icons/Default/flags/kn.gif
/usr/local/churchsoftware/icons/Default/flags/ch.gif
/usr/local/churchsoftware/icons/Default/flags/um.gif
/usr/local/churchsoftware/templates/Blue Back Design.jpg
/usr/local/churchsoftware/templates/Note (Gray).jpg
/usr/local/churchsoftware/icons/Default/flags/an.gif
/usr/local/churchsoftware/icons/Default/flags/nr.gif
/usr/local/churchsoftware/icons/Default/flags/ye.gif
/usr/local/churchsoftware/lib/poi-ooxml-3.5-beta4-20081128.jar
/usr/local/churchsoftware/icons/Default/flags/eh.gif
/usr/local/churchsoftware/icons/Default/flags/ad.gif
/usr/local/churchsoftware/icons/Default/flags/ga.gif
/usr/local/churchsoftware/jmf.properties
/usr/local/churchsoftware/templates/Violet Mold background.jpg
/usr/local/churchsoftware/icons/Default/flags/ma.gif
/usr/local/churchsoftware/lib/ooxml-schemas-1.0.jar
/usr/local/churchsoftware/icons/Default/flags/re.gif
/usr/local/churchsoftware/icons/Default/flags/tf.gif
/usr/local/churchsoftware/icons/Default/flags/is.gif
/usr/local/churchsoftware/icons/Default/flags/cy.gif
/usr/local/churchsoftware/icons/Default/flags/hk.gif
/usr/local/churchsoftware/templates/Tree - Winter.jpg
/usr/local/churchsoftware/icons/Default/flags/om.gif
/usr/local/churchsoftware/templates/Bible (Black & White).jpg
/usr/local/churchsoftware/icons/Default/flags/gb.gif
/usr/local/churchsoftware/icons/Default/menus/openlp.gif
/usr/local/churchsoftware/lib/mediaplayer_linux.jar
/usr/local/churchsoftware/menus/dutch.ui
/usr/local/churchsoftware/lib/fobs4jmf.jar
/usr/local/churchsoftware/church.jar
/usr/local/churchsoftware/templates/Balck Red Gradient.jpg
/usr/local/churchsoftware/icons/prev.gif
/usr/local/churchsoftware/licenses/softwares/lgpl-2.1.txt
/usr/local/churchsoftware/native/jmjpeg.dll
/usr/local/churchsoftware/icons/Default/flags/wf.gif
/usr/local/churchsoftware/icons/Default/flags/no.gif
/usr/local/churchsoftware/bibleconvertor/html/toc.hhc.chapter
/usr/local/churchsoftware/countries.txt
/usr/local/churchsoftware/bibleconvertor/html/chapter.toc.html.chapter
/usr/local/churchsoftware/icons/Default/flags/tl.gif
/usr/local/churchsoftware/native/jmacm.dll
/usr/local/churchsoftware/icons/Default/flags/bv.gif
/usr/local/churchsoftware/icons/Default/flags/tr.gif
/usr/local/churchsoftware/icons/Default/flags/ae.gif
/usr/local/churchsoftware/templates/Celebrations (Pink Waves).jpg
/usr/local/churchsoftware/icons/Default/flags/nu.gif
/usr/local/churchsoftware/icons/Default/flags/pm.gif
/usr/local/churchsoftware/icons/Default/flags/ar.gif
/usr/local/churchsoftware/icons/next.gif
/usr/local/churchsoftware/templates/White DesignBorder On Pink.jpg
/usr/local/churchsoftware/icons/Default/flags/tk.gif
/usr/local/churchsoftware/licenses/lang_bibles/ibs-copyright.txt
/usr/local/churchsoftware/native/jmgsm.dll
/usr/local/churchsoftware/icons/Default/flags/gd.gif
/usr/local/churchsoftware/lib/l2fprod-common-directorychooser.jar
/usr/local/churchsoftware/templates/Black to Blue HGradient.jpg
/usr/local/churchsoftware/icons/Default/flags/tt.gif
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.foot
/usr/local/churchsoftware/icons/Default/flags/gm.gif
/usr/local/churchsoftware/ctxhelper/live_templates/bible_reading.html
/usr/local/churchsoftware/licenses/english_bibles/eb-copyright.txt
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.verse
/usr/local/churchsoftware/celebrations.ref
/usr/local/churchsoftware/icons/Default/flags/sy.gif
/usr/local/churchsoftware/menus/vietnamese.ui
/usr/local/churchsoftware/icons/Default/menus/backup.gif
/usr/local/churchsoftware/templates/Flower Border.jpg
/usr/local/churchsoftware/lib/jsword-common-1.6.jar
/usr/local/churchsoftware/icons/Default/flags/qa.gif
/usr/local/churchsoftware/native/jmmpa.dll
/usr/local/churchsoftware/icons/Default/flags/ec.gif
/usr/local/churchsoftware/licenses/english_bibles/wbtc-copyright.txt
/usr/local/churchsoftware/templates/Guitar (Orange Design).jpg
/usr/local/churchsoftware/lib/soapui-1.0.3.jar
/usr/local/churchsoftware/icons/Default/flags/cx.gif
/usr/local/churchsoftware/icons/big/bigPause.gif
/usr/local/churchsoftware/icons/Default/menus/church_members.gif
/usr/local/churchsoftware/templates/Trees (Snow).jpg
/usr/local/churchsoftware/templates/Brown Border on Light Brown.jpg
/usr/local/churchsoftware/lib/jcalendar-1.3.2.jar
/usr/local/churchsoftware/icons/Default/flags/ne.gif
/usr/local/churchsoftware/icons/Default/flags/fr.gif
/usr/local/churchsoftware/templates/Christmas (Yellow Back) Left.jpg
/usr/local/churchsoftware/templates/Music (Guitar).jpg
/usr/local/churchsoftware/icons/Default/menus/import.gif
/usr/local/churchsoftware/lib/tritonus_gsm-0.3.6.jar
/usr/local/churchsoftware/lib/jave-1.0.1.jar
/usr/local/churchsoftware/icons/k5nCal/k5nCal.icns
/usr/local/churchsoftware/templates/Red Background (Curves).jpg
/usr/local/churchsoftware/icons/Default/flags/ro.gif
/usr/local/churchsoftware/templates/Note (Orange).jpg
/usr/local/churchsoftware/icons/Default/menus/lock.gif
/usr/local/churchsoftware/native/libjmfjawt.so
/usr/local/churchsoftware/icons/Default/menus/export.gif
/usr/local/churchsoftware/licenses/english_bibles/mkjv-copyright.txt
/usr/local/churchsoftware/icons/Default/buttons/save.gif
/usr/local/churchsoftware/templates/Lines Yellow Design (Wide).jpg
/usr/local/churchsoftware/icons/Default/misc/allowed.gif
/usr/local/churchsoftware/templates/Keyboard Bottom.jpg
/usr/local/churchsoftware/lib/dom4j-1.6.1.jar
/usr/local/churchsoftware/icons/Default/menus/langpack.gif
/usr/local/churchsoftware/lib/jflac-1.2.jar
/usr/local/churchsoftware/native/libjmutil.so
/usr/local/churchsoftware/bibleconvertor/html/html.head
/usr/local/churchsoftware/icons/Default/flags/py.gif
/usr/local/churchsoftware/icons/Default/flags/lv.gif
/usr/local/churchsoftware/icons/little/littlePrev.gif
/usr/local/churchsoftware/icons/Default/flags/th.gif
/usr/local/churchsoftware/templates/Sermon Preaching.jpg
/usr/local/churchsoftware/icons/Default/flags/pl.gif
/usr/local/churchsoftware/icons/Default/flags/sz.gif
/usr/local/churchsoftware/templates/Sea Evening View.jpg
/usr/local/churchsoftware/icons/Default/flags/mx.gif
/usr/local/churchsoftware/currencies.txt
/usr/local/churchsoftware/icons/Default/misc/search.gif
/usr/local/churchsoftware/icons/cs_logo.png
/usr/local/churchsoftware/templates/Mother's Love (Red Border).jpg
/usr/local/churchsoftware/icons/Default/flags/li.gif
/usr/local/churchsoftware/icons/Default/menus/scroll.gif
/usr/local/churchsoftware/menus/bulgarian.ui
/usr/local/churchsoftware/icons/little/littleRepeat.gif
/usr/local/churchsoftware/menus/slovakian.ui
/usr/local/churchsoftware/icons/Default/menus/switch.gif
/usr/local/churchsoftware/lib/xbean-2.1.0.jar
/usr/local/churchsoftware/templates/Keyboard Left.jpg
/usr/local/churchsoftware/templates/Autumn Leaves (Left).jpg
/usr/local/churchsoftware/templates/Christmas Tree (LightPink Background).jpg
/usr/local/churchsoftware/templates/Light Violet Center Gradient.jpg
/usr/local/churchsoftware/icons/Default/buttons/exit.gif
/usr/local/churchsoftware/icons/Default/flags/bo.gif
/usr/local/churchsoftware/lib/openxml4j-1.0-beta.jar
/usr/local/churchsoftware/lib/ojdbc14.jar
/usr/local/churchsoftware/templates/Snow House (White Background).jpg
/usr/local/churchsoftware/templates/White Shining on Violet.jpg
/usr/local/churchsoftware/lib/poi-scratchpad-3.5-beta4-20081128.jar
/usr/local/churchsoftware/icons/Default/buttons/open.gif
/usr/local/churchsoftware/lib/vorbisspi1.0.2.jar
/usr/local/churchsoftware/lib/k5nAccordion-1.0.1.jar
/usr/local/churchsoftware/church_calendar/cal_1379200863.ics
/usr/local/churchsoftware/menus/czech.ui
/usr/local/churchsoftware/licenses/lang_bibles/thai-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/grab.gif
/usr/local/churchsoftware/icons/Default/flags/jm.gif
/usr/local/churchsoftware/icons/Default/menus/keyboard.gif
/usr/local/churchsoftware/icons/Default/flags/eg.gif
/usr/local/churchsoftware/templates/Fish (Blue Bckground).jpg
/usr/local/churchsoftware/licenses/swmodules-licidx.prop
/usr/local/churchsoftware/MessagesBundle.properties
/usr/local/churchsoftware/icons/Default/flags/et.gif
/usr/local/churchsoftware/bibleconvertor/html/index.hhk.foot
/usr/local/churchsoftware/icons/big/bigInfo.gif
/usr/local/churchsoftware/templates/Christmas Tree (Black Background).jpg
/usr/local/churchsoftware/templates/Worship Service.jpg
/usr/local/churchsoftware/icons/Default/flags/gp.gif
/usr/local/churchsoftware/icons/Default/menus/detailed.gif
/usr/local/churchsoftware/templates/Sun (Hidden in Clouds).jpg
/usr/local/churchsoftware/lib/jsword-1.6.jar
/usr/local/churchsoftware/icons/cd.gif
/usr/local/churchsoftware/templates/Christmas Tree (White Background).jpg
/usr/local/churchsoftware/templates/Music (Drums).jpg
/usr/local/churchsoftware/lib/commons-lang-2.4.jar
/usr/local/churchsoftware/icons/Default/menus/budget.gif
/usr/local/churchsoftware/icons/Default/flags/pn.gif
/usr/local/churchsoftware/icons/Default/flags/lt.gif
/usr/local/churchsoftware/icons/Default/flags/bf.gif
/usr/local/churchsoftware/icons/big/bigSave.gif
/usr/local/churchsoftware/templates/Note (Blue).jpg
/usr/local/churchsoftware/templates/White DesignBorder On Black.jpg
/usr/local/churchsoftware/lib/buffa_utils.jar
/usr/local/churchsoftware/templates/Country Design.jpg
/usr/local/churchsoftware/icons/caps_lock.gif
/usr/local/churchsoftware/icons/Default/menus/chreport.gif
/usr/local/churchsoftware/templates/Cross (lines).jpg
/usr/local/churchsoftware/icons/Default/flags/ng.gif
/usr/local/churchsoftware/swui.prop
/usr/local/churchsoftware/icons/Default/flags/bm.gif
/usr/local/churchsoftware/icons/expandfolder.gif
/usr/local/churchsoftware/native/jsound.dll
/usr/local/churchsoftware/icons/Default/buttons/calendar.gif
/usr/local/churchsoftware/templates/Speed Border.jpg
/usr/local/churchsoftware/church.png
/usr/local/churchsoftware/lib/albumgrabber.jar
/usr/local/churchsoftware/icons/Default/flags/ai.gif
/usr/local/churchsoftware/templates/Shepherds on Christmas Night.jpg
/usr/local/churchsoftware/icons/Default/flags/mp.gif
/usr/local/churchsoftware/icons/Default/flags/kp.gif
/usr/local/churchsoftware/icons/Default/flags/se.gif
/usr/local/churchsoftware/icons/Default/menus/edituser.gif
/usr/local/churchsoftware/native/jmfjawt.dll
/usr/local/churchsoftware/icons/Default/flags/ca.gif
/usr/local/churchsoftware/icons/Default/flags/tp.gif
/usr/local/churchsoftware/templates/Lines Yellow Design (Narrow).jpg
/usr/local/churchsoftware/lib/commons-codec-1.3.jar
/usr/local/churchsoftware/templates/Communion (Maroon background).jpg
/usr/local/churchsoftware/templates/Keyboard Top.jpg
/usr/local/churchsoftware/templates/Black Green Gradient.jpg
/usr/local/churchsoftware/icons/Default/menus/olangbible.gif
/usr/local/churchsoftware/templates/City Boatyard.jpg
/usr/local/churchsoftware/licenses/softwares/ojdbc-otn.html
/usr/local/churchsoftware/lib/log4j-1.2.13.jar
/usr/local/churchsoftware/icons/little/littleStop.gif
/usr/local/churchsoftware/icons/Default/menus/searchsongs.gif
/usr/local/churchsoftware/icons/Default/flags/to.gif
/usr/local/churchsoftware/icons/Default/flags/es.gif
/usr/local/churchsoftware/ctxhelper/live_templates/meetings.html
/usr/local/churchsoftware/bibleconvertor/html/toc.hhc.head
/usr/local/churchsoftware/templates/Maroon Horizontal Border.jpg
/usr/local/churchsoftware/templates/Note (Pink).jpg
/usr/local/churchsoftware/icons/Default/flags/pg.gif
/usr/local/churchsoftware/icons/Default/flags/gs.gif
/usr/local/churchsoftware/icons/Default/flags/cz.gif
/usr/local/churchsoftware/icons/Default/menus/memorize.gif
/usr/local/churchsoftware/icons/Default/flags/Thumbs.db
/usr/local/churchsoftware/icons/Default/flags/za.gif
/usr/local/churchsoftware/templates/Music (Sax).jpg
/usr/local/churchsoftware/bgobj.db
/usr/local/churchsoftware/icons/play.gif
/usr/local/churchsoftware/icons/Default/flags/mo.gif
/usr/local/churchsoftware/ctxhelper/live_templates/tithes_and_offering.html
/usr/local/churchsoftware/icons/Default/buttons/no.gif
/usr/local/churchsoftware/native/jmutil.dll
/usr/local/churchsoftware/icons/big/bigPrev.gif
/usr/local/churchsoftware/icons/k5nCal/Save24.gif
/usr/local/churchsoftware/icons/Default/flags/aq.gif
/usr/local/churchsoftware/icons/Default/buttons/readme.txt
/usr/local/churchsoftware/icons/Default/flags/de.gif
/usr/local/churchsoftware/ctxhelper/church_admin/annualchurch_report_english.html
/usr/local/churchsoftware/icons/Default/flags/sb.gif
/usr/local/churchsoftware/icons/Default/menus/usermgmt.gif
/usr/local/churchsoftware/icons/Default/flags/lk.gif
/usr/local/churchsoftware/templates/Yellow Green (Gradient).jpg
/usr/local/churchsoftware/templates/Shining on Blue Background.jpg
/usr/local/churchsoftware/icons/Default/flags/dm.gif
/usr/local/churchsoftware/icons/floppy.gif
/usr/local/churchsoftware/icons/Default/menus/password.gif
/usr/local/churchsoftware/templates/Christmas Seasons.png
/usr/local/churchsoftware/templates/Bible Reading (Yellow).jpg
/usr/local/churchsoftware/templates/Sun and Clouds.jpg
/usr/local/churchsoftware/lib/jaxen-1.1.1.jar
/usr/local/churchsoftware/icons/Default/buttons/yes.gif
/usr/local/churchsoftware/icons/Default/flags/co.gif
/usr/local/churchsoftware/icons/Default/flags/sa.gif
/usr/local/churchsoftware/icons/Default/flags/au.gif
/usr/local/churchsoftware/lib/fobs4jmf_mac.jar
/usr/local/churchsoftware/icons/Default/menus/compress.gif
/usr/local/churchsoftware/templates/White net on Red.jpg
/usr/local/churchsoftware/icons/big/bigEject.gif
/usr/local/churchsoftware/templates/[Animated]_Waterfall_1.gif
/usr/local/churchsoftware/icons/Default/flags/nc.gif
/usr/local/churchsoftware/lib/MacStuff.jar
/usr/local/churchsoftware/lib/jfreechart-1.0.0.jar
/usr/local/churchsoftware/bibleconvertor/monoon/verse.dat
/usr/local/churchsoftware/icons/Default/flags/tj.gif
/usr/local/churchsoftware/icons/Default/flags/mk.gif
/usr/local/churchsoftware/icons/Default/flags/ci.gif
/usr/local/churchsoftware/templates/Wedding (Two Hearts on Pink).jpg
/usr/local/churchsoftware/icons/Default/flags/iq.gif
/usr/local/churchsoftware/lib/gtkswing.jar
/usr/local/churchsoftware/native/libjmxlib.so
/usr/local/churchsoftware/icons/Default/flags/gf.gif
/usr/local/churchsoftware/icons/Default/flags/ni.gif
/usr/local/churchsoftware/icons/Default/menus/readme.txt
/usr/local/churchsoftware/templates/Christmas Tree.jpg
/usr/local/churchsoftware/templates/Christmas (Yellow Back) Right.jpg
/usr/local/churchsoftware/templates/Bible Reading (Pink).jpg
/usr/local/churchsoftware/bibleconvertor/monoon/title.dat
/usr/local/churchsoftware/templates/[Animated]_serenityimage.gif
/usr/local/churchsoftware/templates/White DesignBorder On LightGreen.jpg
/usr/local/churchsoftware/templates/Celebrations (Pink).jpg
/usr/local/churchsoftware/templates/Grass on Blue Background.jpg
/usr/local/churchsoftware/icons/disk.gif
/usr/local/churchsoftware/icons/Default/menus/esword.gif
/usr/local/churchsoftware/icons/Default/flags/id.gif
/usr/local/churchsoftware/menus/polish.ui
/usr/local/churchsoftware/icons/k5nCal/New24.gif
/usr/local/churchsoftware/icons/Default/flags/mq.gif
/usr/local/churchsoftware/licenses/lang_bibles/nuovariveduta-copyright.txt
/usr/local/churchsoftware/templates/Blue Line Border.jpg
/usr/local/churchsoftware/menus/thai.ui
/usr/local/churchsoftware/templates/Gifts (Blue Background).jpg
/usr/local/churchsoftware/icons/Default/menus/memberdb.gif
/usr/local/churchsoftware/icons/Default/menus/winamp.gif
/usr/local/churchsoftware/icons/Default/flags/gn.gif
/usr/local/churchsoftware/log4j.xml
/usr/local/churchsoftware/icons/Default/flags/in.gif
/usr/local/churchsoftware/ctxhelper/live_templates/communion.html
/usr/local/churchsoftware/icons/Default/menus/zxml.gif
/usr/local/churchsoftware/icons/Default/flags/sn.gif
/usr/local/churchsoftware/templates/Lines Green Design (Wide).jpg
/usr/local/churchsoftware/icons/Default/menus/instant.gif
/usr/local/churchsoftware/icons/Default/flags/sh.gif
/usr/local/churchsoftware/icons/Default/flags/kz.gif
/usr/local/churchsoftware/bibleconvertor/html/html.book
/usr/local/churchsoftware/xsl/cswing/index.txt
/usr/local/churchsoftware/icons/Default/flags/mr.gif
/usr/local/churchsoftware/licenses/softwares/cpl-v1.0.txt
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.title
/usr/local/churchsoftware/icons/Default/flags/bh.gif
/usr/local/churchsoftware/icons/Default/flags/mw.gif
/usr/local/churchsoftware/icons/Default/flags/mh.gif
/usr/local/churchsoftware/icons/Default/menus/ppt.gif
/usr/local/churchsoftware/menus/swedish.ui
/usr/local/churchsoftware/templates/Rising Sun.jpg
/usr/local/churchsoftware/icons/Default/flags/fk.gif
/usr/local/churchsoftware/icons/Default/flags/ke.gif
/usr/local/churchsoftware/bibleconvertor/thml/verse.head
/usr/local/churchsoftware/icons/Default/flags/ky.gif
/usr/local/churchsoftware/native/jmmci.dll
/usr/local/churchsoftware/icons/Default/flags/il.gif
/usr/local/churchsoftware/native/jmh261.dll
/usr/local/churchsoftware/lib/sqlitejdbc-v054.jar
/usr/local/churchsoftware/icons/Default/buttons/rename.gif
/usr/local/churchsoftware/ctxhelper/first_use/ppt_firstuse.html
/usr/local/churchsoftware/icons/Default/flags/kr.gif
/usr/local/churchsoftware/icons/Default/flags/vc.gif
/usr/local/churchsoftware/bibleconvertor/html/chapter.toc.html.chapter.foot
/usr/local/churchsoftware/icons/little/littlePause.gif
/usr/local/churchsoftware/licenses/english_bibles/amp-copyright.txt
/usr/local/churchsoftware/templates/Heart (Pink).jpg
/usr/local/churchsoftware/bibleconvertor/html/toc.hhc.foot
/usr/local/churchsoftware/lib/jakarta-regexp-1.2.jar
/usr/local/churchsoftware/icons/Default/menus/addgroup.gif
/usr/local/churchsoftware/bibleconvertor/html/converter.html
/usr/local/churchsoftware/bibleconvertor/monoon/ver.dat
/usr/local/churchsoftware/icons/Default/menus/deluser.gif
/usr/local/churchsoftware/icons/Default/menus/detect.gif
/usr/local/churchsoftware/icons/Default/menus/memrpt.gif
/usr/local/churchsoftware/icons/Default/flags/vu.gif
/usr/local/churchsoftware/templates/Light Green Center Gradient.jpg
/usr/local/churchsoftware/lib/poi-contrib-3.5-beta4-20081128.jar
/usr/local/churchsoftware/menus/chinesetraditional.ui
/usr/local/churchsoftware/templates/Mountain Path.jpg
/usr/local/churchsoftware/templates/Brown Border.jpg
/usr/local/churchsoftware/icons/Default/menus/factory.gif
/usr/local/churchsoftware/icons/Default/flags/lu.gif
/usr/local/churchsoftware/lib/mediaplayer.jar
/usr/local/churchsoftware/bibleconvertor/html/stop.txt
/usr/local/churchsoftware/icons/Default/flags/kw.gif
/usr/local/churchsoftware/icons/Default/flags/ki.gif
/usr/local/churchsoftware/licenses/softwares/gpl-1.0.txt
/usr/local/churchsoftware/native/libjmh261.so
/usr/local/churchsoftware/icons/Default/menus/attendance.gif
/usr/local/churchsoftware/templates/Flower (White Background).jpg
/usr/local/churchsoftware/icons/Default/flags/ms.gif
/usr/local/churchsoftware/licenses/english_bibles/hnv-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/projector.gif
/usr/local/churchsoftware/icons/Default/flags/nf.gif
/usr/local/churchsoftware/icons/Default/flags/lc.gif
/usr/local/churchsoftware/bibleconvertor/html/html.chapter
/usr/local/churchsoftware/licenses/softwares/gpl-2.0.txt
/usr/local/churchsoftware/ctxhelper/first_use/Collections.txt
/usr/local/churchsoftware/icons/Default/flags/mt.gif
/usr/local/churchsoftware/icons/Default/flags/gh.gif
/usr/local/churchsoftware/icons/Default/flags/lb.gif
/usr/local/churchsoftware/native/jmvfw.dll
/usr/local/churchsoftware/licenses/softwares/java.html
/usr/local/churchsoftware/icons/Default/flags/md.gif
/usr/local/churchsoftware/licenses/softwares/lgpl-3.0.html
/usr/local/churchsoftware/icons/Default/menus/pamphlet.gif
/usr/local/churchsoftware/icons/Default/buttons/play.gif
/usr/local/churchsoftware/transitions.xml
/usr/local/churchsoftware/native/jmdaud.dll
/usr/local/churchsoftware/icons/Default/flags/sj.gif
/usr/local/churchsoftware/icons/Default/flags/my.gif
/usr/local/churchsoftware/templates/Deer on River.jpg
/usr/local/churchsoftware/licenses/english_bibles/esv-copyright.txt
/usr/local/churchsoftware/templates/Fish Symbol.jpg
/usr/local/churchsoftware/templates/Note (Yellow).jpg
/usr/local/churchsoftware/defaultfontstyle.prop
/usr/local/churchsoftware/icons/Default/menus/e2o.gif
/usr/local/churchsoftware/icons/Default/flags/am.gif
/usr/local/churchsoftware/icons/Default/flags/sd.gif
/usr/local/churchsoftware/bibleconvertor/sword/verseex
/usr/local/churchsoftware/icons/Default/flags/io.gif
/usr/local/churchsoftware/icons/big/bigDelete.gif
/usr/local/churchsoftware/icons/Default/menus/logoff.gif
/usr/local/churchsoftware/icons/Default/misc/nophoto.png
/usr/local/churchsoftware/icons/Default/menus/gift.gif
/usr/local/churchsoftware/icons/Default/menus/biblestudy.gif
/usr/local/churchsoftware/icons/Default/menus/serviceplanner.gif
/usr/local/churchsoftware/icons/Default/menus/forum.gif
/usr/local/churchsoftware/lib/jogg-0.0.7.jar
/usr/local/churchsoftware/licenses/english_bibles/gnb-copyright.txt
/usr/local/churchsoftware/templates/White DesignBorder On Maroon.jpg
/usr/local/churchsoftware/icons/Default/flags/je.gif
/usr/local/churchsoftware/icons/Default/flags/ao.gif
/usr/local/churchsoftware/icons/Default/menus/postal.gif
/usr/local/churchsoftware/templates/Celebrations Youth.jpg
/usr/local/churchsoftware/menus/french.ui
/usr/local/churchsoftware/templates/Autumn Leaves (Bottom).jpg
/usr/local/churchsoftware/icons/Default/flags/ua.gif
/usr/local/churchsoftware/icons/k5nCal/Edit24.gif
/usr/local/churchsoftware/icons/Default/flags/as.gif
/usr/local/churchsoftware/templates/Green Trees.jpg
/usr/local/churchsoftware/icons/Default/flags/pa.gif
/usr/local/churchsoftware/templates/Brown.jpg
/usr/local/churchsoftware/icons/Default/menus/verseview.gif
/usr/local/churchsoftware/icons/Default/menus/photogallery.gif
/usr/local/churchsoftware/icons/Default/flags/ir.gif
/usr/local/churchsoftware/icons/Default/buttons/zoom_out.gif
/usr/local/churchsoftware/icons/Default/flags/va.gif
/usr/local/churchsoftware/church_calendar/calendars.xml
/usr/local/churchsoftware/lib/jspeex0.9.7.jar
/usr/local/churchsoftware/icons/Default/flags/ru.gif
/usr/local/churchsoftware/icons/Default/flags/lr.gif
/usr/local/churchsoftware/menus/german.ui
/usr/local/churchsoftware/icons/Default/menus/defaultbver.gif
/usr/local/churchsoftware/icons/Default/misc/notallowed.gif
/usr/local/churchsoftware/lib/BrowserLauncher2-10rc4.jar
/usr/local/churchsoftware/native/jmddraw.dll
/usr/local/churchsoftware/templates/Blue Crystals.jpg
/usr/local/churchsoftware/templates/Flower on Brown Background.jpg
/usr/local/churchsoftware/licenses/english_bibles/asv-copyright.txt
/usr/local/churchsoftware/licenses/lang_bibles/public-domain.html
/usr/local/churchsoftware/icons/Default/flags/mg.gif
/usr/local/churchsoftware/logs/church-software.log
/usr/local/churchsoftware/icons/Default/flags/tg.gif
/usr/local/churchsoftware/start.sh
/usr/local/churchsoftware/icons/Default/menus/recent.gif
/usr/local/churchsoftware/icons/little/littlePlay.gif
/usr/local/churchsoftware/licenses/swmodules/gobible.txt
/usr/local/churchsoftware/templates/Lines Green Design (Narrow).jpg
/usr/local/churchsoftware/templates/Cross Evening.jpg
/usr/local/churchsoftware/licenses/english_bibles/nkjv-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/exit.gif
/usr/local/churchsoftware/templates/Leaf (White Background).jpg
/usr/local/churchsoftware/lib/DatePicker-V0.99-2006.09.01.jar
/usr/local/churchsoftware/templates/Increase in Knowledge.jpg
/usr/local/churchsoftware/ctxhelper/first_use/photos_firstuse.html
/usr/local/churchsoftware/templates/Oval White on Blue.jpg
/usr/local/churchsoftware/menus/tagalog.ui
/usr/local/churchsoftware/icons/Default/flags/gt.gif
/usr/local/churchsoftware/licenses/softwares/jaxb-jrl.txt
/usr/local/churchsoftware/templates/Gospel Meeting.jpg
/usr/local/churchsoftware/icons/Default/menus/dnbibles.gif
/usr/local/churchsoftware/bibleconvertor/html/html.foot
/usr/local/churchsoftware/icons/Default/menus/biblereading.gif
/usr/local/churchsoftware/templates/Pray to Lord (Hands Above).jpg
/usr/local/churchsoftware/icons/Default/menus/bibleversions.gif
/usr/local/churchsoftware/templates/Lines White Design (Narrow).jpg
/usr/local/churchsoftware/lib/skinlf.jar
/usr/local/churchsoftware/icons/Default/menus/bug.gif
/usr/local/churchsoftware/lib/tritonus_share.jar
/usr/local/churchsoftware/icons/Default/flags/sk.gif
/usr/local/churchsoftware/icons/little/littleNext.gif
/usr/local/churchsoftware/templates/Pearls on Blue.jpg
/usr/local/churchsoftware/native/jmdaudc.dll
/usr/local/churchsoftware/bibleconvertor/sword/conf
/usr/local/churchsoftware/menus/slovenian.ui
/usr/local/churchsoftware/native/jmh263enc.dll
/usr/local/churchsoftware/icons/Default/flags/ps.gif
/usr/local/churchsoftware/icons/Default/flags/by.gif
/usr/local/churchsoftware/lib/jsr173_1.0_api.jar
/usr/local/churchsoftware/native/jmg723.dll
/usr/local/churchsoftware/icons/Default/menus/thml.gif
/usr/local/churchsoftware/lib/k5n-ical-0.4.5.jar
/usr/local/churchsoftware/soundbank.gm
/usr/local/churchsoftware/templates/Celebrations (White Background).jpg
/usr/local/churchsoftware/templates/[Animated]_jesus-animated-gif-image-0102.gif
/usr/local/churchsoftware/icons/Default/menus/biblesearch.gif
/usr/local/churchsoftware/native/libjmmpa.so
/usr/local/churchsoftware/icons/Default/flags/mu.gif
/usr/local/churchsoftware/licenses/langbibles-licidx.prop
/usr/local/churchsoftware/native/jmgdi.dll
/usr/local/churchsoftware/icons/Default/flags/do.gif
/usr/local/churchsoftware/templates/Yellow and Green Whirl.jpg
/usr/local/churchsoftware/icons/Default/flags/kh.gif
/usr/local/churchsoftware/icons/Default/menus/tools.gif
/usr/local/churchsoftware/xsl/cswing/simple2.xsl
/usr/local/churchsoftware/icons/little/littleDelete.gif
/usr/local/churchsoftware/icons/Default/flags/vi.gif
/usr/local/churchsoftware/templates/Windows Bliss.jpg
/usr/local/churchsoftware/icons/Default/flags/al.gif
/usr/local/churchsoftware/lib/xmlbeans-2.3.0.jar
/usr/local/churchsoftware/templates/Grass Background.jpg
/usr/local/churchsoftware/icons/Default/flags/ht.gif
/usr/local/churchsoftware/bibleconvertor/html/index.html
/usr/local/churchsoftware/licenses/softwares/gpl-3.0.html
/usr/local/churchsoftware/bibleconvertor/html/toc.hhc.book.foot
/usr/local/churchsoftware/icons/Default/flags/fm.gif
/usr/local/churchsoftware/icons/Default/flags/mm.gif
/usr/local/churchsoftware/icons/Default/flags/gu.gif
/usr/local/churchsoftware/menus/italian.ui
/usr/local/churchsoftware/templates/Personal Prayer.jpg
/usr/local/churchsoftware/lib/mysql-connector-java-3.1.12-bin.jar
/usr/local/churchsoftware/icons/big/bigStop.gif
/usr/local/churchsoftware/icons/Default/menus/settings.gif
/usr/local/churchsoftware/lib/l2fprod-common-fontchooser.jar
/usr/local/churchsoftware/templates/Blue Background (Curves).jpg
/usr/local/churchsoftware/native/libjmjpeg.so
/usr/local/churchsoftware/templates/Christmas Tree (LightBlue Background).jpg
/usr/local/churchsoftware/lib/derbynet.jar
/usr/local/churchsoftware/icons/Default/menus/help.gif
/usr/local/churchsoftware/templates/Green Border.jpg
/usr/local/churchsoftware/lib/J7Zip.jar
/usr/local/churchsoftware/language.prop
/usr/local/churchsoftware/icons/Default/buttons/fav.gif
/usr/local/churchsoftware/licenses/english_bibles/msg-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/id_card.gif
/usr/local/churchsoftware/icons/Default/flags/hr.gif
/usr/local/churchsoftware/icons/Default/menus/faq.gif
/usr/local/churchsoftware/icons/Default/flags/aw.gif
/usr/local/churchsoftware/icons/Default/flags/ba.gif
/usr/local/churchsoftware/templates/Christmas Gift.jpg
/usr/local/churchsoftware/icons/Default/menus/about.gif
/usr/local/churchsoftware/icons/Default/menus/switch_lang.gif
/usr/local/churchsoftware/templates/Boats (Blue Sky).jpg
/usr/local/churchsoftware/templates/Rose (Whote Background).jpg
/usr/local/churchsoftware/icons/Default/menus/gobible.gif
/usr/local/churchsoftware/icons/Default/flags/cc.gif
/usr/local/churchsoftware/lib/jmf_mac.jar
/usr/local/churchsoftware/icons/Default/menus/sword.gif
/usr/local/churchsoftware/native/jmvcm.dll
/usr/local/churchsoftware/icons/Default/flags/nl.gif
/usr/local/churchsoftware/lib/k5n-calendarpanel-0.4.5.jar
/usr/local/churchsoftware/licenses/softwares/apache-2.0.txt
/usr/local/churchsoftware/icons/Default/flags/er.gif
/usr/local/churchsoftware/icons/Default/flags/ck.gif
/usr/local/churchsoftware/icons/k5nCal/Delete24.gif
/usr/local/churchsoftware/licenses/english_bibles/vw-copyright.txt
/usr/local/churchsoftware/templates/Orange Back Design.jpg
/usr/local/churchsoftware/native/fobs4jmf.dll
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.chapter
/usr/local/churchsoftware/icons/Default/flags/sr.gif
/usr/local/churchsoftware/icons/Default/flags/gy.gif
/usr/local/churchsoftware/bibleconvertor/thml/book.head
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.book
/usr/local/churchsoftware/templates/Guitar (Red Design).jpg
/usr/local/churchsoftware/icons/Default/flags/gi.gif
/usr/local/churchsoftware/icons/pause.gif
/usr/local/churchsoftware/essentials_linux/libstdc++5.0-3.3.3-62745cl.i386.rpm
/usr/local/churchsoftware/icons/Default/flags/bb.gif
/usr/local/churchsoftware/licenses/swmodules/esword.txt
/usr/local/churchsoftware/templates/Black DesignBorder On White.jpg
/usr/local/churchsoftware/templates/Snow on Gray Background.jpg
/usr/local/churchsoftware/icons/Default/flags/tw.gif
/usr/local/churchsoftware/transliteration/transliterate_thai.prop
/usr/local/churchsoftware/icons/Default/flags/sl.gif
/usr/local/churchsoftware/bibleconvertor/thml/foot
/usr/local/churchsoftware/logs/church-software.log.2009-07-11
/usr/local/churchsoftware/icons/Default/flags/be.gif
/usr/local/churchsoftware/favorites/-------------- Favorites --------------
/usr/local/churchsoftware/icons/Default/menus/cs.gif
/usr/local/churchsoftware/lib/jdom.jar
/usr/local/churchsoftware/licenses/websites/wog.txt
/usr/local/churchsoftware/menus/finnish.ui
/usr/local/churchsoftware/bibleconvertor/html/book.toc.html.head
/usr/local/churchsoftware/lib/kj_dsp1.1.jar
/usr/local/churchsoftware/templates/Christmas Star.jpg
/usr/local/churchsoftware/templates/Fruit on Orange Background.jpg
/usr/local/churchsoftware/icons/Default/flags/bs.gif
/usr/local/churchsoftware/templates/Good Friday.jpg
/usr/local/churchsoftware/menus/russian.ui
/usr/local/churchsoftware/licenses/english_bibles/clv-copyright.txt
/usr/local/churchsoftware/templates/Seek God (Blue Background).jpg
/usr/local/churchsoftware/lib/jorbis-0.0.15.jar
/usr/local/churchsoftware/licenses/lang_bibles/hebrew-copyright.txt
/usr/local/churchsoftware/menus/ukrainian.ui
/usr/local/churchsoftware/icons/Default/flags/xx.gif
/usr/local/churchsoftware/ctxhelper/first_use/serviceplanner.html
/usr/local/churchsoftware/icons/Default/flags/tm.gif
/usr/local/churchsoftware/icons/Default/flags/bi.gif
/usr/local/churchsoftware/icons/Default/menus/pda.gif
/usr/local/churchsoftware/icons/Default/flags/bw.gif
/usr/local/churchsoftware/templates/Flowers on Blue Background.jpg
/usr/local/churchsoftware/licenses/softwares/jgoodies-bsd.txt
/usr/local/churchsoftware/jlgui.ini
/usr/local/churchsoftware/templates/[Animated]_fireg.gif
/usr/local/churchsoftware/icons/Default/menus/license.gif
/usr/local/churchsoftware/icons/Default/menus/lyrics_download.gif
/usr/local/churchsoftware/licenses/lang_bibles/schlachter-copyright.txt
/usr/local/churchsoftware/language_defaults.prop
/usr/local/churchsoftware/lib/jackcess-1.1.18.jar
/usr/local/churchsoftware/icons/Default/flags/tv.gif
/usr/local/churchsoftware/lib/derbyclient.jar
/usr/local/churchsoftware/templates/Blue Sky with Clouds.jpg
/usr/local/churchsoftware/templates/Celebrations (Red Background).jpg
/usr/local/churchsoftware/icons/Default/misc/rose.gif
/usr/local/churchsoftware/icons/Default/flags/nz.gif
/usr/local/churchsoftware/icons/Default/flags/ws.gif
/usr/local/churchsoftware/menus/hungarian.ui
/usr/local/churchsoftware/licenses/softwares-licidx.prop
/usr/local/churchsoftware/licenses/softwares/jspeex-bsd.txt
/usr/local/churchsoftware/menus/serbian.ui
/usr/local/churchsoftware/lib/jbcl.jar
/usr/local/churchsoftware/xsl/cswing/cutandpaste.xsl
/usr/local/churchsoftware/icons/Default/menus/karaoke.gif
/usr/local/churchsoftware/licenses/english_bibles/public-domain.txt
/usr/local/churchsoftware/ctxhelper/live_templates/final_blessing.html
/usr/local/churchsoftware/icons/Default/menus/editgroup.gif
/usr/local/churchsoftware/templates/Merry Christmas.jpg
/usr/local/churchsoftware/bibleconvertor/sword/line
/usr/local/churchsoftware/bibleconvertor/thml/verse
/usr/local/churchsoftware/lib/jlgui3.0.jar
/usr/local/churchsoftware/lib/icu4j-charsets-4_0_1.jar
/usr/local/churchsoftware/icons/Default/flags/cm.gif
/usr/local/churchsoftware/native/libjmh263enc.so
/usr/local/churchsoftware/bibleconvertor/html/index.hhk.head
/usr/local/churchsoftware/icons/Default/flags/hu.gif
/usr/local/churchsoftware/menus/portuguese.ui
/usr/local/churchsoftware/templates/Evening on Seashore.jpg
/usr/local/churchsoftware/icons/Default/menus/admin.gif
/usr/local/churchsoftware/templates/Gifts on Blue Background.jpg
/usr/local/churchsoftware/icons/Default/buttons/delfav.gif
/usr/local/churchsoftware/icons/Default/flags/sm.gif
/usr/local/churchsoftware/icons/Default/menus/ebooks.gif
/usr/local/churchsoftware/licenses/english_bibles/nlt-copyright.txt
/usr/local/churchsoftware/bibleconvertor/thml/title
/usr/local/churchsoftware/essentials_linux/libstdc++5_3.3.6-15_i386.deb
/usr/local/churchsoftware/templates/Light Pink Center Gradient.jpg
/usr/local/churchsoftware/menus/hebrew.ui
/usr/local/churchsoftware/theme.properties
/usr/local/churchsoftware/themes.xml
/usr/local/churchsoftware/icons/Default/flags/pr.gif
/usr/local/churchsoftware/icons/Default/flags/pe.gif
/usr/local/churchsoftware/icons/Default/flags/bd.gif
/usr/local/churchsoftware/menus/greek.ui
/usr/local/churchsoftware/icons/Default/flags/ly.gif
/usr/local/churchsoftware/menus/estonian.ui
/usr/local/churchsoftware/ctxhelper/live_templates/welcome_message.html
/usr/local/churchsoftware/icons/Default/flags/np.gif
/usr/local/churchsoftware/icons/Default/flags/gr.gif
/usr/local/churchsoftware/icons/Default/flags/br.gif
/usr/local/churchsoftware/bibleconvertor/sword/verse
/usr/local/churchsoftware/icons/Default/flags/na.gif
/usr/local/churchsoftware/licenses/lang_bibles/bsi-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/console.gif
/usr/local/churchsoftware/native/libjmmpegv.so
/usr/local/churchsoftware/icons/Default/flags/ve.gif
/usr/local/churchsoftware/icons/Default/flags/cd.gif
/usr/local/churchsoftware/bibleconvertor/thml/testament.foot
/usr/local/churchsoftware/menus/romanian.ui
/usr/local/churchsoftware/icons/Default/flags/hn.gif
/usr/local/churchsoftware/icons/Default/flags/dj.gif
/usr/local/churchsoftware/transliteration/transliterate.prop
/usr/local/churchsoftware/lib/jmf.jar
/usr/local/churchsoftware/icons/Default/buttons/zoom_in.gif
/usr/local/churchsoftware/icons/Default/flags/ie.gif
/usr/local/churchsoftware/icons/Default/menus/mediaplayer.gif
/usr/local/churchsoftware/icons/Default/misc/wysiwyg.gif
/usr/local/churchsoftware/icons/Default/flags/gw.gif
/usr/local/churchsoftware/native/libfobs4jmf.so
/usr/local/churchsoftware/templates/Christmas Tree Decorated on Blue.jpg
/usr/local/churchsoftware/xsl/cswing/cutandpaste2.xsl
/usr/local/churchsoftware/icons/folder.gif
/usr/local/churchsoftware/lib/jmactritonusspi1.74.jar
/usr/local/churchsoftware/icons/cs_logo_bw.png
/usr/local/churchsoftware/templates/Flower Pink Blossom.jpg
/usr/local/churchsoftware/ctxhelper/church_admin/financial_report_english.html
/usr/local/churchsoftware/icons/Default/flags/gg.gif
/usr/local/churchsoftware/icons/Default/flags/sv.gif
/usr/local/churchsoftware/icons/Default/flags/cu.gif
/usr/local/churchsoftware/icons/Default/misc/autoupdates.gif
/usr/local/churchsoftware/icons/Default/flags/vg.gif
/usr/local/churchsoftware/icons/Default/flags/so.gif
/usr/local/churchsoftware/native/libfobs4jmf.jnilib
/usr/local/churchsoftware/templates/Cross (Black Background).jpg
/usr/local/churchsoftware/icons/Default/flags/cv.gif
/usr/local/churchsoftware/templates/Shepherd (Evening Background).jpg
/usr/local/churchsoftware/icons/Default/menus/themes.gif
/usr/local/churchsoftware/icons/Default/flags/dz.gif
/usr/local/churchsoftware/icons/little/littleSave.gif
/usr/local/churchsoftware/icons/Default/flags/ug.gif
/usr/local/churchsoftware/icons/Default/menus/langbibles.gif
/usr/local/churchsoftware/bibleconvertor/thml/book.foot
/usr/local/churchsoftware/icons/Default/flags/uy.gif
/usr/local/churchsoftware/templates/Jesus Christ.jpg
/usr/local/churchsoftware/licenses/softwares/afl-2.1.txt
/usr/local/churchsoftware/icons/Default/flags/bz.gif
/usr/local/churchsoftware/icons/Default/flags/km.gif
/usr/local/churchsoftware/lib/liquidlnf.jar
/usr/local/churchsoftware/menus/lithuanian.ui
/usr/local/churchsoftware/icons/Default/flags/tn.gif
/usr/local/churchsoftware/icons/Default/menus/tree.gif
/usr/local/churchsoftware/menus/croatian.ui
/usr/local/churchsoftware/templates/Note (White).jpg
/usr/local/churchsoftware/icons/Default/misc/ring.gif
/usr/local/churchsoftware/icons/Default/flags/jo.gif
/usr/local/churchsoftware/icons/Default/flags/fi.gif
/usr/local/churchsoftware/templates/Lines White Design (Wide).jpg
/usr/local/churchsoftware/licenses/softwares/icu4j-ibm.html
/usr/local/churchsoftware/icons/Default/flags/cg.gif
/usr/local/churchsoftware/settings
/usr/local/churchsoftware/templates/Blue Mold background.jpg
/usr/local/churchsoftware/templates/Note (Violet).jpg
/usr/local/churchsoftware/bibleconvertor/html/book.toc.html.book
/usr/local/churchsoftware/templates/Celebrations (Balloons).jpg
/usr/local/churchsoftware/icons/Default/menus/multipane.gif
/usr/local/churchsoftware/icons/Default/flags/sc.gif
/usr/local/churchsoftware/icons/Default/flags/gq.gif
/usr/local/churchsoftware/icons/Default/flags/tc.gif
/usr/local/churchsoftware/lib/commons-logging-api.jar
/usr/local/churchsoftware/templates/Yellow Flower (Brown Background).jpg
/usr/local/churchsoftware/icons/Default/flags/mv.gif
/usr/local/churchsoftware/icons/Default/flags/ls.gif
/usr/local/churchsoftware/templates/[Animated]_bkstarani.gif
/usr/local/churchsoftware/icons/Default/flags/zw.gif
/usr/local/churchsoftware/licenses/english_bibles/litv-copyright.txt
/usr/local/churchsoftware/native/libjmmpx.so
/usr/local/churchsoftware/native/libjmv4l.so
/usr/local/churchsoftware/templates/Lines Red Design (Wide).jpg
/usr/local/churchsoftware/bibleconvertor/thml/verse.foot
/usr/local/churchsoftware/bibleconvertor/html/index.hhk.title
/usr/local/churchsoftware/icons/Default/flags/us.gif
/usr/local/churchsoftware/lib/poi-3.5-beta4-20081128.jar
/usr/local/churchsoftware/icons/Default/flags/ph.gif
/usr/local/churchsoftware/icons/little/littleInfo.gif
/usr/local/churchsoftware/licenses/english_bibles/kjv-copyright.txt
/usr/local/churchsoftware/native/libjmg723.so
/usr/local/churchsoftware/icons/Default/flags/af.gif
/usr/local/churchsoftware/templates/Pink Painted Border on Light Brown.jpg
/usr/local/churchsoftware/templates/Bluish Green Background.jpg
/usr/local/churchsoftware/lib/opencsv-1.8.jar
/usr/local/churchsoftware/licenses/websites/tamilchristian.txt
/usr/local/churchsoftware/templates/Autumn Leaves (Right).jpg
/usr/local/churchsoftware/templates/Church on Scenary.jpg
/usr/local/churchsoftware/icons/computer.png
/usr/local/churchsoftware/icons/Default/menus/link.gif
/usr/local/churchsoftware/lib/mp3spi1.9.4.jar
/usr/local/churchsoftware/icons/Default/flags/jp.gif
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.blank
/usr/local/churchsoftware/icons/Default/flags/cf.gif
/usr/local/churchsoftware/templates/Bible (Black Background).jpg
/usr/local/churchsoftware/icons/Default/flags/fo.gif
/usr/local/churchsoftware/licenses/english_bibles/niv-copyright.txt
/usr/local/churchsoftware/bibleconvertor/thml/head
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.head
/usr/local/churchsoftware/icons/Default/misc/print.gif
/usr/local/churchsoftware/church_background.jpg
/usr/local/churchsoftware/lib/jl1.0.jar
/usr/local/churchsoftware/icons/big/bigNext.gif
/usr/local/churchsoftware/bibleconvertor/html/chapter.toc.html.chapter.head
/usr/local/churchsoftware/native/libjmdaud.so
/usr/local/churchsoftware/templates/Snow on Blue Background.jpg
/usr/local/churchsoftware/templates/Black Orange Gradient.jpg
/usr/local/churchsoftware/lib/multiplayer.jar
/usr/local/churchsoftware/icons/Default/flags/fj.gif
/usr/local/churchsoftware/icons/Default/menus/audiorec.gif
/usr/local/churchsoftware/templates/Flower Pot (Brown).jpg
/usr/local/churchsoftware/lib/fobs4jmf_linux.jar
/usr/local/churchsoftware/icons/Default/menus/lang.gif
/usr/local/churchsoftware/bibleconvertor/html/html.blank
/usr/local/churchsoftware/menus/menus.xml
/usr/local/churchsoftware/templates/10 Commandments.jpg
/usr/local/churchsoftware/templates/Guitarist Playing.jpg
/usr/local/churchsoftware/bibleconvertor/rtf/rtf.page
/usr/local/churchsoftware/icons/cross.gif
/usr/local/churchsoftware/bibleconvertor/html/chapter.toc.html.head
/usr/local/churchsoftware/icons/Default/menus/camera.gif
/usr/local/churchsoftware/licenses/english_bibles/nasb-copyright.txt
/usr/local/churchsoftware/templates/Cross (Flowers).jpg
/usr/local/churchsoftware/bibleconvertor/html/index.toc.html
/usr/local/churchsoftware/lib/derby.jar
/usr/local/churchsoftware/licenses/engbibles-licidx.prop
/usr/local/churchsoftware/lib/basicplayer3.0.jar
/usr/local/churchsoftware/transliteration/transliterate_tamil.prop
/usr/local/churchsoftware/icons/Default/buttons/zoom_defaults.gif
/usr/local/churchsoftware/bibleconvertor/plain/verse
/usr/local/churchsoftware/templates/White DesignBorder On Orange.jpg
/usr/local/churchsoftware/icons/Default/menus/songs.gif
/usr/local/churchsoftware/templates/Christmas Trees.jpg
/usr/local/churchsoftware/templates/White on Brown Background.jpg
/usr/local/churchsoftware/icons/Default/flags/dk.gif
/usr/local/churchsoftware/lib/commons-logging-1.1.jar
/usr/local/churchsoftware/icons/Default/menus/report.gif
/usr/local/churchsoftware/icons/Default/menus/gui.gif
/usr/local/churchsoftware/essentials_linux/gcc-3.3-base_3.3.6-15_i386.deb
/usr/local/churchsoftware/bibleconvertor/thml/chapter.foot
/usr/local/churchsoftware/icons/Default/misc/rose_preview.gif
/usr/local/churchsoftware/licenses/english_bibles/cev-copyright.txt
/usr/local/churchsoftware/icons/Default/menus/financial_report.gif
/usr/local/churchsoftware/lib/napkinlaf-swingset2.jar
/usr/local/churchsoftware/menus/arabic.ui
/usr/local/churchsoftware/menus/spanish.ui
/usr/local/churchsoftware/icons/Default/flags/bn.gif
/usr/local/churchsoftware/icons/Default/flags/bt.gif
/usr/local/churchsoftware/icons/Default/flags/ag.gif
/usr/local/churchsoftware/licenses/english_bibles/kjv21-copyright.txt
/usr/local/churchsoftware/bibleconvertor/html/html.verse
/usr/local/churchsoftware/lib/customizer.jar
/usr/local/churchsoftware/icons/Default/menus/resize.gif
/usr/local/churchsoftware/icons/big/bigShuffle.gif
/usr/local/churchsoftware/icons/stop.gif
/usr/local/churchsoftware/templates/[Animated]_christmas-animated-gifs-06.gif
/usr/local/churchsoftware/templates/Flowers.jpg
/usr/local/churchsoftware/templates/Christmas Tree Decorated (Black Back).jpg
/usr/local/churchsoftware/native/jmam.dll
/usr/local/churchsoftware/icons/Default/flags/uz.gif
/usr/local/churchsoftware/lib/jcommon-1.0.0.jar
/usr/local/churchsoftware/icons/Default/flags/bj.gif
/usr/local/churchsoftware/menus/indonesian.ui
/usr/local/churchsoftware/bibleconvertor/html/bible.hhp
/usr/local/churchsoftware/church_db/seg0/c300.dat
/usr/local/churchsoftware/church_db/seg0/c29a0.dat
/usr/local/churchsoftware/church_db/seg0/c121.dat
/usr/local/churchsoftware/church_db/seg0/c2af0.dat
/usr/local/churchsoftware/church_db/seg0/c200.dat
/usr/local/churchsoftware/church_db/seg0/c2d0.dat
/usr/local/churchsoftware/church_db/seg0/c111.dat
/usr/local/churchsoftware/church_db/seg0/ca1.dat
/usr/local/churchsoftware/church_db/seg0/c180.dat
/usr/local/churchsoftware/church_db/seg0/c101.dat
/usr/local/churchsoftware/church_db/seg0/c2a71.dat
/usr/local/churchsoftware/church_db/seg0/cf0.dat
/usr/local/churchsoftware/church_db/seg0/c340.dat
/usr/local/churchsoftware/church_db/seg0/c2a11.dat
/usr/local/churchsoftware/church_db/seg0/c321.dat
/usr/local/churchsoftware/church_db/seg0/c3e1.dat
/usr/local/churchsoftware/church_db/seg0/c141.dat
/usr/local/churchsoftware/church_db/seg0/c2b21.dat
/usr/local/churchsoftware/church_db/seg0/c2a31.dat
/usr/local/churchsoftware/church_db/seg0/c2b1.dat
/usr/local/churchsoftware/church_db/seg0/c230.dat
/usr/local/churchsoftware/church_db/seg0/c331.dat
/usr/local/churchsoftware/church_db/seg0/c1f1.dat
/usr/local/churchsoftware/church_db/seg0/c90.dat
/usr/local/churchsoftware/church_db/seg0/c2971.dat
/usr/local/churchsoftware/church_db/seg0/c361.dat
/usr/local/churchsoftware/church_db/seg0/c391.dat
/usr/local/churchsoftware/church_db/log/logmirror.ctrl
/usr/local/churchsoftware/church_db/seg0/c241.dat
/usr/local/churchsoftware/church_db/log/log753.dat
/usr/local/churchsoftware/church_db/seg0/c2991.dat
/usr/local/churchsoftware/church_db/seg0/c3d1.dat
/usr/local/churchsoftware/church_db/seg0/c3c0.dat
/usr/local/churchsoftware/church_db/seg0/c271.dat
/usr/local/churchsoftware/church_db/seg0/c2a20.dat
/usr/local/churchsoftware/church_db/seg0/c2c1.dat
/usr/local/churchsoftware/church_db/seg0/cd1.dat
/usr/local/churchsoftware/church_db/seg0/c29b1.dat
/usr/local/churchsoftware/church_db/seg0/c130.dat
/usr/local/churchsoftware/church_db/seg0/c281.dat
/usr/local/churchsoftware/church_db/seg0/c41.dat
/usr/local/churchsoftware/church_db/seg0/c260.dat
/usr/local/churchsoftware/church_db/seg0/c2a40.dat
/usr/local/churchsoftware/church_db/seg0/c71.dat
/usr/local/churchsoftware/church_db/log/sample.txt
/usr/local/churchsoftware/church_db/seg0/c2ab0.dat
/usr/local/churchsoftware/church_db/seg0/cb1.dat
/usr/local/churchsoftware/church_db/seg0/c2980.dat
/usr/local/churchsoftware/church_db/seg0/c171.dat
/usr/local/churchsoftware/church_db/seg0/c2ac1.dat
/usr/local/churchsoftware/church_db/seg0/c10.dat
/usr/local/churchsoftware/church_db/seg0/c2f0.dat
/usr/local/churchsoftware/church_db/log/log.ctrl
/usr/local/churchsoftware/church_db/seg0/c2ad0.dat
/usr/local/churchsoftware/church_db/seg0/c2a1.dat
/usr/local/churchsoftware/church_db/seg0/c2ae1.dat
/usr/local/churchsoftware/church_db/seg0/ce1.dat
/usr/local/churchsoftware/church_db/seg0/c1a1.dat
/usr/local/churchsoftware/church_db/seg0/c2a80.dat
/usr/local/churchsoftware/church_db/seg0/c371.dat
/usr/local/churchsoftware/church_db/seg0/c3b1.dat
/usr/local/churchsoftware/church_db/seg0/c351.dat
/usr/local/churchsoftware/church_db/seg0/c2e1.dat
/usr/local/churchsoftware/church_db/seg0/c221.dat
/usr/local/churchsoftware/church_db/seg0/c1e0.dat
/usr/local/churchsoftware/church_db/seg0/c2a60.dat
/usr/local/churchsoftware/church_db/service.properties
/usr/local/churchsoftware/church_db/seg0/c29d1.dat
/usr/local/churchsoftware/church_db/seg0/c2a51.dat
/usr/local/churchsoftware/church_db/seg0/c191.dat
/usr/local/churchsoftware/church_db/seg0/c29e0.dat
/usr/local/churchsoftware/church_db/seg0/c380.dat
/usr/local/churchsoftware/church_db/seg0/c2b01.dat
/usr/local/churchsoftware/church_db/seg0/c2960.dat
/usr/local/churchsoftware/church_db/seg0/c161.dat
/usr/local/churchsoftware/church_db/seg0/c60.dat
/usr/local/churchsoftware/church_db/seg0/c31.dat
/usr/local/churchsoftware/church_db/seg0/c311.dat
/usr/local/churchsoftware/church_db/seg0/c51.dat
/usr/local/churchsoftware/church_db/seg0/c2b10.dat
/usr/local/churchsoftware/church_db/seg0/c1b1.dat
/usr/local/churchsoftware/church_db/seg0/c211.dat
/usr/local/churchsoftware/church_db/seg0/c81.dat
/usr/local/churchsoftware/church_db/seg0/c2aa1.dat
/usr/local/churchsoftware/church_db/seg0/c290.dat
/usr/local/churchsoftware/church_db/seg0/c20.dat
/usr/local/churchsoftware/church_db/seg0/c29c0.dat
/usr/local/churchsoftware/church_db/seg0/c3a1.dat
/usr/local/churchsoftware/church_db/seg0/c251.dat
/usr/local/churchsoftware/church_db/seg0/c1d1.dat
/usr/local/churchsoftware/church_db/seg0/c1c0.dat
/usr/local/churchsoftware/church_db/seg0/c29f1.dat
/usr/local/churchsoftware/church_db/seg0/c150.dat
/usr/local/churchsoftware/church_db/seg0/c3f1.dat
/usr/local/churchsoftware/church_db/seg0/c2a00.dat
/usr/local/churchsoftware/church_db/seg0/cc0.dat
/usr/local/churchsoftware/church_db/seg0/c2a90.dat
/usr/local/churchsoftware/topics/Wise as serpents
/usr/local/churchsoftware/topics/Gehenna
/usr/local/churchsoftware/topics/Pharisees
/usr/local/churchsoftware/topics/Prophecy - Duma
/usr/local/churchsoftware/topics/Grief
/usr/local/churchsoftware/topics/Diligence
/usr/local/churchsoftware/topics/Spiritual blindness
/usr/local/churchsoftware/topics/Earth, (God's future plan with)
/usr/local/churchsoftware/topics/Envy
/usr/local/churchsoftware/topics/Manna
/usr/local/churchsoftware/topics/Benedictions
/usr/local/churchsoftware/topics/Alcohol
/usr/local/churchsoftware/topics/Love your enemies
/usr/local/churchsoftware/topics/Heartily
/usr/local/churchsoftware/topics/Bravery
/usr/local/churchsoftware/topics/Heaven
/usr/local/churchsoftware/topics/Chastity
/usr/local/churchsoftware/topics/Jesus' miracles
/usr/local/churchsoftware/topics/Dress code at church
/usr/local/churchsoftware/topics/Wife abuse
/usr/local/churchsoftware/topics/Creditor
/usr/local/churchsoftware/topics/Preexistence
/usr/local/churchsoftware/topics/Second coming of Christ
/usr/local/churchsoftware/topics/Government, Obedience to
/usr/local/churchsoftware/topics/Profanity
/usr/local/churchsoftware/topics/Jesus' obedience
/usr/local/churchsoftware/topics/Israel - All nations gathered against
/usr/local/churchsoftware/topics/Glorifying God
/usr/local/churchsoftware/topics/Smoking tobacco
/usr/local/churchsoftware/topics/Last days
/usr/local/churchsoftware/topics/Jokes
/usr/local/churchsoftware/topics/Prudence
/usr/local/churchsoftware/topics/Affection
/usr/local/churchsoftware/topics/Prophecy - Dedan
/usr/local/churchsoftware/topics/Love for God
/usr/local/churchsoftware/topics/Promises of God
/usr/local/churchsoftware/topics/Reward
/usr/local/churchsoftware/topics/Bible memorization
/usr/local/churchsoftware/topics/Holy Spirit
/usr/local/churchsoftware/topics/Role models
/usr/local/churchsoftware/topics/Polygamy forbidden
/usr/local/churchsoftware/topics/Almsgiving
/usr/local/churchsoftware/topics/Children, How to deal with rebellious
/usr/local/churchsoftware/topics/Acknowledgment
/usr/local/churchsoftware/topics/Animals, Cruelty towards
/usr/local/churchsoftware/topics/Jesus, His literal return to the earth
/usr/local/churchsoftware/topics/Carnality
/usr/local/churchsoftware/topics/Creation of Man
/usr/local/churchsoftware/topics/Teamwork
/usr/local/churchsoftware/topics/Arrogance
/usr/local/churchsoftware/topics/Wicked
/usr/local/churchsoftware/topics/Appearance of Man, Outward
/usr/local/churchsoftware/topics/Meekness
/usr/local/churchsoftware/topics/Temple, Solomon's
/usr/local/churchsoftware/topics/False prophets
/usr/local/churchsoftware/topics/Deacons
/usr/local/churchsoftware/topics/Injury
/usr/local/churchsoftware/topics/Adultery (Spiritual)
/usr/local/churchsoftware/topics/Self-righteousness
/usr/local/churchsoftware/topics/Once saved, always saved fallacy
/usr/local/churchsoftware/topics/Shortest verse
/usr/local/churchsoftware/topics/Rude
/usr/local/churchsoftware/topics/Jesus' mission
/usr/local/churchsoftware/topics/Preparedness
/usr/local/churchsoftware/topics/Believing God
/usr/local/churchsoftware/topics/Gog & Magog
/usr/local/churchsoftware/topics/Time
/usr/local/churchsoftware/topics/Oppression
/usr/local/churchsoftware/topics/God's power
/usr/local/churchsoftware/topics/Buildings
/usr/local/churchsoftware/topics/Holiness
/usr/local/churchsoftware/topics/Elders (Church)
/usr/local/churchsoftware/topics/Eunuchs
/usr/local/churchsoftware/topics/Creation
/usr/local/churchsoftware/topics/Pregnancy
/usr/local/churchsoftware/topics/Reprobacy
/usr/local/churchsoftware/topics/Slaves
/usr/local/churchsoftware/topics/Assurance
/usr/local/churchsoftware/topics/Depression
/usr/local/churchsoftware/topics/Holy Spirit, Inspired by the
/usr/local/churchsoftware/topics/Circumcision
/usr/local/churchsoftware/topics/Jesus' kingship
/usr/local/churchsoftware/topics/Success, Secrets to
/usr/local/churchsoftware/topics/Mercy
/usr/local/churchsoftware/topics/Self defense
/usr/local/churchsoftware/topics/Excitement
/usr/local/churchsoftware/topics/Medicine
/usr/local/churchsoftware/topics/Church names
/usr/local/churchsoftware/topics/Bestiality
/usr/local/churchsoftware/topics/Prophecy - Hamath
/usr/local/churchsoftware/topics/Grave, The
/usr/local/churchsoftware/topics/Praise
/usr/local/churchsoftware/topics/Communion with God
/usr/local/churchsoftware/topics/Incest
/usr/local/churchsoftware/topics/Chosen people
/usr/local/churchsoftware/topics/Repentance
/usr/local/churchsoftware/topics/Speaking in tongues
/usr/local/churchsoftware/topics/Servants
/usr/local/churchsoftware/topics/Church discipline
/usr/local/churchsoftware/topics/Business
/usr/local/churchsoftware/topics/Slander
/usr/local/churchsoftware/topics/Depravity
/usr/local/churchsoftware/topics/Stress
/usr/local/churchsoftware/topics/Disarmament
/usr/local/churchsoftware/topics/Bribery
/usr/local/churchsoftware/topics/Sons of God
/usr/local/churchsoftware/topics/Crime
/usr/local/churchsoftware/topics/Athletics
/usr/local/churchsoftware/topics/Self-denial
/usr/local/churchsoftware/topics/Competition
/usr/local/churchsoftware/topics/Arabs
/usr/local/churchsoftware/topics/Death
/usr/local/churchsoftware/topics/Emotion
/usr/local/churchsoftware/topics/Betrothal
/usr/local/churchsoftware/topics/Rape
/usr/local/churchsoftware/topics/Healing diseases
/usr/local/churchsoftware/topics/Astronomy
/usr/local/churchsoftware/topics/Testimony
/usr/local/churchsoftware/topics/Mountains are symbols for kingdoms
/usr/local/churchsoftware/topics/Obesity
/usr/local/churchsoftware/topics/Murderers, Punishment of
/usr/local/churchsoftware/topics/Quarreling
/usr/local/churchsoftware/topics/Earth
/usr/local/churchsoftware/topics/Age
/usr/local/churchsoftware/topics/Prophecy - Ethiopia
/usr/local/churchsoftware/topics/Preaching
/usr/local/churchsoftware/topics/Judging, Hypocritical
/usr/local/churchsoftware/topics/Drugs, Illegal narcotics
/usr/local/churchsoftware/topics/Responding to God's call
/usr/local/churchsoftware/topics/Cheerfulness
/usr/local/churchsoftware/topics/Burial
/usr/local/churchsoftware/topics/Awe
/usr/local/churchsoftware/topics/Prophecy - Kir
/usr/local/churchsoftware/topics/Handicapped
/usr/local/churchsoftware/topics/Jews (Bless them and you'll be blessed)
/usr/local/churchsoftware/topics/Commitment
/usr/local/churchsoftware/topics/Greed
/usr/local/churchsoftware/topics/Orphans
/usr/local/churchsoftware/topics/Carnage
/usr/local/churchsoftware/topics/Commandmemts in Epistles
/usr/local/churchsoftware/topics/Trinity
/usr/local/churchsoftware/topics/Affluence, Dangers of
/usr/local/churchsoftware/topics/Jews as God's chosen people
/usr/local/churchsoftware/topics/Readiness
/usr/local/churchsoftware/topics/Tongues
/usr/local/churchsoftware/topics/Wife
/usr/local/churchsoftware/topics/Jealousy
/usr/local/churchsoftware/topics/Allegiance
/usr/local/churchsoftware/topics/Fortune tellers, Mediums
/usr/local/churchsoftware/topics/Miscarriage
/usr/local/churchsoftware/topics/Priorities in life
/usr/local/churchsoftware/topics/Salt, Covenant of
/usr/local/churchsoftware/topics/Complacency
/usr/local/churchsoftware/topics/Assistance
/usr/local/churchsoftware/topics/Nudity
/usr/local/churchsoftware/topics/Murder
/usr/local/churchsoftware/topics/Exorcism
/usr/local/churchsoftware/topics/Regeneration
/usr/local/churchsoftware/topics/Gospel, Sharing the
/usr/local/churchsoftware/topics/Prophecy - Elam
/usr/local/churchsoftware/topics/Salvation also an event in the future
/usr/local/churchsoftware/topics/Poverty
/usr/local/churchsoftware/topics/Atheism
/usr/local/churchsoftware/topics/Conduct towards God, Man's
/usr/local/churchsoftware/topics/Fatherless
/usr/local/churchsoftware/topics/Hospitality
/usr/local/churchsoftware/topics/Goals
/usr/local/churchsoftware/topics/Eucharist
/usr/local/churchsoftware/topics/Cynicism
/usr/local/churchsoftware/topics/Blindness (spiritual)
/usr/local/churchsoftware/topics/Holy Spirit gifts
/usr/local/churchsoftware/topics/Neighbor
/usr/local/churchsoftware/topics/Choice
/usr/local/churchsoftware/topics/Insanity
/usr/local/churchsoftware/topics/Peace
/usr/local/churchsoftware/topics/Salvation
/usr/local/churchsoftware/topics/Easter
/usr/local/churchsoftware/topics/Divorce
/usr/local/churchsoftware/topics/Prophecy - Damascus
/usr/local/churchsoftware/topics/Judging others
/usr/local/churchsoftware/topics/Prophecy - Greece
/usr/local/churchsoftware/topics/Enemies (personal)
/usr/local/churchsoftware/topics/Demons
/usr/local/churchsoftware/topics/Astrology
/usr/local/churchsoftware/topics/Disfellowship
/usr/local/churchsoftware/topics/Perseverance
/usr/local/churchsoftware/topics/Criminals
/usr/local/churchsoftware/topics/Laziness
/usr/local/churchsoftware/topics/Reliance upon God
/usr/local/churchsoftware/topics/Justice
/usr/local/churchsoftware/topics/Unfinished verse
/usr/local/churchsoftware/topics/Fruit of the Spirit
/usr/local/churchsoftware/topics/Elderly, The
/usr/local/churchsoftware/topics/Arguments
/usr/local/churchsoftware/topics/God's mercy
/usr/local/churchsoftware/topics/Homosexuality
/usr/local/churchsoftware/topics/Israel's boundaries
/usr/local/churchsoftware/topics/God's knowledge
/usr/local/churchsoftware/topics/Burden
/usr/local/churchsoftware/topics/Christian growth
/usr/local/churchsoftware/topics/Seven thunders
/usr/local/churchsoftware/topics/Inheritance, Receiving an
/usr/local/churchsoftware/topics/Spiritual desire
/usr/local/churchsoftware/topics/Israel - Chosen of God forever
/usr/local/churchsoftware/topics/Jesus, Prophecies by
/usr/local/churchsoftware/topics/Boasting
/usr/local/churchsoftware/topics/Prophecy - Edom
/usr/local/churchsoftware/topics/Jewish persecution
/usr/local/churchsoftware/topics/Conviction of sin
/usr/local/churchsoftware/topics/Indiscretion
/usr/local/churchsoftware/topics/Existence of God
/usr/local/churchsoftware/topics/Catholicism
/usr/local/churchsoftware/topics/Suffering
/usr/local/churchsoftware/topics/Partiality
/usr/local/churchsoftware/topics/Hypocrisy
/usr/local/churchsoftware/topics/Prayers answered
/usr/local/churchsoftware/topics/God's provision
/usr/local/churchsoftware/topics/Rulers
/usr/local/churchsoftware/topics/Sickness
/usr/local/churchsoftware/topics/Compassion
/usr/local/churchsoftware/topics/Prophecy - Arabia
/usr/local/churchsoftware/topics/Spouse abuse
/usr/local/churchsoftware/topics/Vanity (outward appearance)
/usr/local/churchsoftware/topics/Dependability
/usr/local/churchsoftware/topics/Baldness
/usr/local/churchsoftware/topics/Book of Life
/usr/local/churchsoftware/topics/Modesty
/usr/local/churchsoftware/topics/Roman Catholicism
/usr/local/churchsoftware/topics/Lucifer
/usr/local/churchsoftware/topics/Military participation and the Christian
/usr/local/churchsoftware/topics/Sin
/usr/local/churchsoftware/topics/Mohammed and Islam
/usr/local/churchsoftware/topics/Overconfidence
/usr/local/churchsoftware/topics/Saved, Is once saved always saved
/usr/local/churchsoftware/topics/Idleness
/usr/local/churchsoftware/topics/Cruelty against animals
/usr/local/churchsoftware/topics/Single, Remaining
/usr/local/churchsoftware/topics/Cooperation
/usr/local/churchsoftware/topics/Responsibility
/usr/local/churchsoftware/topics/Body as a temple, A believer's
/usr/local/churchsoftware/topics/Bad things happen to good people
/usr/local/churchsoftware/topics/Adultery
/usr/local/churchsoftware/topics/Prostitution
/usr/local/churchsoftware/topics/Mourning for the dead
/usr/local/churchsoftware/topics/Fasting
/usr/local/churchsoftware/topics/Patriotism
/usr/local/churchsoftware/topics/Prophecy - Bashan
/usr/local/churchsoftware/topics/Covetousness
/usr/local/churchsoftware/topics/Encouragement
/usr/local/churchsoftware/topics/Golden Rule
/usr/local/churchsoftware/topics/Curse, The
/usr/local/churchsoftware/topics/Christ our example
/usr/local/churchsoftware/topics/Hardness of heart
/usr/local/churchsoftware/topics/Jabez, Prayer of
/usr/local/churchsoftware/topics/Prophecy - Libya
/usr/local/churchsoftware/topics/Exercise, Usefulness of
/usr/local/churchsoftware/topics/Infidelity to God
/usr/local/churchsoftware/topics/Arson
/usr/local/churchsoftware/topics/Character
/usr/local/churchsoftware/topics/Christ as judge
/usr/local/churchsoftware/topics/Borrowing
/usr/local/churchsoftware/topics/Opportunity
/usr/local/churchsoftware/topics/Rainbow
/usr/local/churchsoftware/topics/Grudges
/usr/local/churchsoftware/topics/Annoying others
/usr/local/churchsoftware/topics/Jesus, Prayers of
/usr/local/churchsoftware/topics/Avarice
/usr/local/churchsoftware/topics/Animals, Fate of pets after death
/usr/local/churchsoftware/topics/Gentleness
/usr/local/churchsoftware/topics/Judges
/usr/local/churchsoftware/topics/Communication
/usr/local/churchsoftware/topics/Remarriage
/usr/local/churchsoftware/topics/Teaching your children
/usr/local/churchsoftware/topics/Dreams
/usr/local/churchsoftware/topics/Stewardship
/usr/local/churchsoftware/topics/Prayers of Jesus
/usr/local/churchsoftware/topics/Salvation not by works
/usr/local/churchsoftware/topics/Swear
/usr/local/churchsoftware/topics/Bad company leads to evil
/usr/local/churchsoftware/topics/Witchcraft
/usr/local/churchsoftware/topics/Man's nature
/usr/local/churchsoftware/topics/Unwed mothers
/usr/local/churchsoftware/topics/Mixed marriages
/usr/local/churchsoftware/topics/Embalming
/usr/local/churchsoftware/topics/Evangelism
/usr/local/churchsoftware/topics/Necromancy
/usr/local/churchsoftware/topics/Judgment
/usr/local/churchsoftware/topics/Annihilation
/usr/local/churchsoftware/topics/Evil
/usr/local/churchsoftware/topics/Conforming to the world
/usr/local/churchsoftware/topics/John the Baptizer
/usr/local/churchsoftware/topics/Spirit of man
/usr/local/churchsoftware/topics/Discipleship
/usr/local/churchsoftware/topics/Revelation of Jesus
/usr/local/churchsoftware/topics/Losing one's salvation
/usr/local/churchsoftware/topics/Leadership, Examples of
/usr/local/churchsoftware/topics/Commit oneself to God
/usr/local/churchsoftware/topics/Divination
/usr/local/churchsoftware/topics/Brotherly love
/usr/local/churchsoftware/topics/Death, Preparing for
/usr/local/churchsoftware/topics/Fellowship with God
/usr/local/churchsoftware/topics/Spiritual death
/usr/local/churchsoftware/topics/Masturbation
/usr/local/churchsoftware/topics/Separate, Keeping
/usr/local/churchsoftware/topics/Endurance
/usr/local/churchsoftware/topics/False doctrine
/usr/local/churchsoftware/topics/Discouragement
/usr/local/churchsoftware/topics/Dissension
/usr/local/churchsoftware/topics/Tattoos
/usr/local/churchsoftware/topics/Conceit
/usr/local/churchsoftware/topics/Freedom in Christ
/usr/local/churchsoftware/topics/Riches
/usr/local/churchsoftware/topics/God, Omnipotent
/usr/local/churchsoftware/topics/Census
/usr/local/churchsoftware/topics/Murmuring
/usr/local/churchsoftware/topics/Saints
/usr/local/churchsoftware/topics/Courage
/usr/local/churchsoftware/topics/Paid ministers
/usr/local/churchsoftware/topics/Prophecy - Jerusalem
/usr/local/churchsoftware/topics/Tax collectors
/usr/local/churchsoftware/topics/Superstition
/usr/local/churchsoftware/topics/Gluttony
/usr/local/churchsoftware/topics/Lusts of the flesh
/usr/local/churchsoftware/topics/Indignation, Righteous
/usr/local/churchsoftware/topics/Teasing
/usr/local/churchsoftware/topics/Kidding around
/usr/local/churchsoftware/topics/Friendship
/usr/local/churchsoftware/topics/Prayer in affliction
/usr/local/churchsoftware/topics/Submission to authority
/usr/local/churchsoftware/topics/Satan
/usr/local/churchsoftware/topics/Sheol
/usr/local/churchsoftware/topics/Parables
/usr/local/churchsoftware/topics/Grace
/usr/local/churchsoftware/topics/Angel
/usr/local/churchsoftware/topics/Prayers, Instances of bold
/usr/local/churchsoftware/topics/Spiritual gifts
/usr/local/churchsoftware/topics/Discipline
/usr/local/churchsoftware/topics/Witnessing to others of the Gospel
/usr/local/churchsoftware/topics/Self deception
/usr/local/churchsoftware/topics/Eclipse
/usr/local/churchsoftware/topics/Prophecy - Ammon
/usr/local/churchsoftware/topics/Temptation
/usr/local/churchsoftware/topics/Eternal death
/usr/local/churchsoftware/topics/Immortality
/usr/local/churchsoftware/topics/Women's apparel
/usr/local/churchsoftware/topics/Light
/usr/local/churchsoftware/topics/Sex before marriage
/usr/local/churchsoftware/topics/Relying upon God
/usr/local/churchsoftware/topics/Blood of Christ
/usr/local/churchsoftware/topics/Gifts of the Spirit
/usr/local/churchsoftware/topics/Prophecy - Egypt
/usr/local/churchsoftware/topics/Prayer, Examples of
/usr/local/churchsoftware/topics/Consolation
/usr/local/churchsoftware/topics/Lotteries, Jackpots, Raffles
/usr/local/churchsoftware/topics/Servanthood
/usr/local/churchsoftware/topics/Judgment, Eternal
/usr/local/churchsoftware/topics/Ability
/usr/local/churchsoftware/topics/Marked (or sealed) by God
/usr/local/churchsoftware/topics/Dedicating children to the Lord
/usr/local/churchsoftware/topics/Genealogy
/usr/local/churchsoftware/topics/Ego
/usr/local/churchsoftware/topics/Strife
/usr/local/churchsoftware/topics/Flattery
/usr/local/churchsoftware/topics/Disputes
/usr/local/churchsoftware/topics/Abundance
/usr/local/churchsoftware/topics/Nuisance, Becoming a
/usr/local/churchsoftware/topics/Menstruation
/usr/local/churchsoftware/topics/Salvation, Perseverance required for
/usr/local/churchsoftware/topics/Old Testament concerning the Messiah
/usr/local/churchsoftware/topics/Ecology
/usr/local/churchsoftware/topics/Revelations, visions
/usr/local/churchsoftware/topics/Romance
/usr/local/churchsoftware/topics/Persecution
/usr/local/churchsoftware/topics/Mary, Mother of Jesus
/usr/local/churchsoftware/topics/Moderation
/usr/local/churchsoftware/topics/Love
/usr/local/churchsoftware/topics/Wine
/usr/local/churchsoftware/topics/Haggling
/usr/local/churchsoftware/topics/Kingdom of God
/usr/local/churchsoftware/topics/Adaptability
/usr/local/churchsoftware/topics/Edification
/usr/local/churchsoftware/topics/Gangs
/usr/local/churchsoftware/topics/Keeping your word
/usr/local/churchsoftware/topics/Foreknowledge of the Messiah from Creation
/usr/local/churchsoftware/topics/Cares of this world
/usr/local/churchsoftware/topics/Christ as Priest
/usr/local/churchsoftware/topics/Lending
/usr/local/churchsoftware/topics/Walking in the Truth
/usr/local/churchsoftware/topics/Finding favor in God's sight
/usr/local/churchsoftware/topics/Boredom
/usr/local/churchsoftware/topics/Distress
/usr/local/churchsoftware/topics/Impenitence
/usr/local/churchsoftware/topics/Geology
/usr/local/churchsoftware/topics/Interracial marriages forbidden to Israelites
/usr/local/churchsoftware/topics/Unclean spirit
/usr/local/churchsoftware/topics/Gentiles
/usr/local/churchsoftware/topics/Assasination
/usr/local/churchsoftware/topics/Loyalty
/usr/local/churchsoftware/topics/Power
/usr/local/churchsoftware/topics/Clarity
/usr/local/churchsoftware/topics/Obedience
/usr/local/churchsoftware/topics/Jesus' birth
/usr/local/churchsoftware/topics/Privacy
/usr/local/churchsoftware/topics/Disabled persons
/usr/local/churchsoftware/topics/Cruelty against men
/usr/local/churchsoftware/topics/Cowardice
/usr/local/churchsoftware/topics/Dead, Talking with the
/usr/local/churchsoftware/topics/Prophecy - Gog
/usr/local/churchsoftware/topics/Lukewarm
/usr/local/churchsoftware/topics/Teenagers
/usr/local/churchsoftware/topics/Disease
/usr/local/churchsoftware/topics/Guilt
/usr/local/churchsoftware/topics/Confession of Christ
/usr/local/churchsoftware/topics/Jesus' humanity
/usr/local/churchsoftware/topics/Entertainment
/usr/local/churchsoftware/topics/Health, fitness
/usr/local/churchsoftware/topics/Conscientious objection to war
/usr/local/churchsoftware/topics/Stealing
/usr/local/churchsoftware/topics/Virginity, Woman losing her
/usr/local/churchsoftware/topics/Cultivation
/usr/local/churchsoftware/topics/Spiritual adoption
/usr/local/churchsoftware/topics/Mother, Honoring one's
/usr/local/churchsoftware/topics/Nazism
/usr/local/churchsoftware/topics/Betting
/usr/local/churchsoftware/topics/Adversity, affliction, hardship
/usr/local/churchsoftware/topics/Antichrist
/usr/local/churchsoftware/topics/Russia
/usr/local/churchsoftware/topics/Jesus insults his disciples
/usr/local/churchsoftware/topics/Protection
/usr/local/churchsoftware/topics/Deception
/usr/local/churchsoftware/topics/Marrying outside the faith prohibited
/usr/local/churchsoftware/topics/Capital punishment
/usr/local/churchsoftware/topics/Peer pressure
/usr/local/churchsoftware/topics/Divided heart
/usr/local/churchsoftware/topics/Prophecy - Babylon
/usr/local/churchsoftware/topics/Trials and difficulties
/usr/local/churchsoftware/topics/Consecration
/usr/local/churchsoftware/topics/Head coverings, Women and
/usr/local/churchsoftware/topics/Virgin Mary
/usr/local/churchsoftware/topics/Spiritual growth
/usr/local/churchsoftware/topics/Duty of citizens to governments
/usr/local/churchsoftware/topics/God's glory
/usr/local/churchsoftware/topics/Ascension of Jesus
/usr/local/churchsoftware/topics/Sadness
/usr/local/churchsoftware/topics/Altruism
/usr/local/churchsoftware/topics/Betrayal
/usr/local/churchsoftware/topics/Purity
/usr/local/churchsoftware/topics/Good old days
/usr/local/churchsoftware/topics/Christians as representatives of Jesus
/usr/local/churchsoftware/topics/Commandments of Christ
/usr/local/churchsoftware/topics/Polygamy tolerated
/usr/local/churchsoftware/topics/Vanity (futility)
/usr/local/churchsoftware/topics/Unmarried, The
/usr/local/churchsoftware/topics/Sluggards
/usr/local/churchsoftware/topics/Scoffing
/usr/local/churchsoftware/topics/Sin of omission
/usr/local/churchsoftware/topics/Discontent
/usr/local/churchsoftware/topics/Advice
/usr/local/churchsoftware/topics/Respecting others
/usr/local/churchsoftware/topics/Fellowship with Christ
/usr/local/churchsoftware/topics/Humility
/usr/local/churchsoftware/topics/Sexual relationships
/usr/local/churchsoftware/topics/Fool
/usr/local/churchsoftware/topics/Fellowship with believers
/usr/local/churchsoftware/topics/Oath
/usr/local/churchsoftware/topics/Citizenship
/usr/local/churchsoftware/topics/Leaven
/usr/local/churchsoftware/topics/Jesus' death
/usr/local/churchsoftware/topics/Prejudice
/usr/local/churchsoftware/topics/Salt
/usr/local/churchsoftware/topics/Worrying
/usr/local/churchsoftware/topics/Agony
/usr/local/churchsoftware/topics/Pride
/usr/local/churchsoftware/topics/Temperance
/usr/local/churchsoftware/topics/Gossip
/usr/local/churchsoftware/topics/Revenge
/usr/local/churchsoftware/topics/Status
/usr/local/churchsoftware/topics/Reproof
/usr/local/churchsoftware/topics/Sanctification
/usr/local/churchsoftware/topics/Resignation
/usr/local/churchsoftware/topics/Food, Not to judge others based on
/usr/local/churchsoftware/topics/Consequences
/usr/local/churchsoftware/topics/Church of Rome
/usr/local/churchsoftware/topics/Backbiting
/usr/local/churchsoftware/topics/Jesus' submission to his Father's will
/usr/local/churchsoftware/topics/Denominations
/usr/local/churchsoftware/topics/Courtesy
/usr/local/churchsoftware/topics/Persecution of the Jews
/usr/local/churchsoftware/topics/Jesus' compassion
/usr/local/churchsoftware/topics/Teenage pregnancy
/usr/local/churchsoftware/topics/Enthusiasm
/usr/local/churchsoftware/topics/God's promises
/usr/local/churchsoftware/topics/Prophecy - Amalek
/usr/local/churchsoftware/topics/Flesh, Lust of the
/usr/local/churchsoftware/topics/Communion
/usr/local/churchsoftware/topics/Messiah, Old Testament references concerning
/usr/local/churchsoftware/topics/Inheritance, Leaving an
/usr/local/churchsoftware/topics/Old Testament concerning Messiah's sufferings
/usr/local/churchsoftware/topics/Conscience
/usr/local/churchsoftware/topics/Family
/usr/local/churchsoftware/topics/Accountability
/usr/local/churchsoftware/topics/Sorrow
/usr/local/churchsoftware/topics/God the Creator
/usr/local/churchsoftware/topics/Women
/usr/local/churchsoftware/topics/Death bed experiences
/usr/local/churchsoftware/topics/Strangers
/usr/local/churchsoftware/topics/Women pastors
/usr/local/churchsoftware/topics/Prophecy - Medo-Persia
/usr/local/churchsoftware/topics/Proverbs
/usr/local/churchsoftware/topics/Symbols
/usr/local/churchsoftware/topics/Judgment Day
/usr/local/churchsoftware/topics/Overseer
/usr/local/churchsoftware/topics/Restitution
/usr/local/churchsoftware/topics/Despair
/usr/local/churchsoftware/topics/Predestination
/usr/local/churchsoftware/topics/Addiction
/usr/local/churchsoftware/topics/Divine punishment
/usr/local/churchsoftware/topics/Die, Wanting to
/usr/local/churchsoftware/topics/Tongue, Controlling one's
/usr/local/churchsoftware/topics/Education
/usr/local/churchsoftware/topics/Childlessness
/usr/local/churchsoftware/topics/Joy
/usr/local/churchsoftware/topics/Engagement
/usr/local/churchsoftware/topics/Salvation can be lost
/usr/local/churchsoftware/topics/Jesus thought to be insane
/usr/local/churchsoftware/topics/Devotions
/usr/local/churchsoftware/topics/Evil, The source of
/usr/local/churchsoftware/topics/Idolatry
/usr/local/churchsoftware/topics/Prophecy - Lebanon
/usr/local/churchsoftware/topics/Christians
/usr/local/churchsoftware/topics/Martyrdom
/usr/local/churchsoftware/topics/Worldliness
/usr/local/churchsoftware/topics/Prayer of wicked
/usr/local/churchsoftware/topics/God's name
/usr/local/churchsoftware/topics/New covenant
/usr/local/churchsoftware/topics/Brevity of life
/usr/local/churchsoftware/topics/Nakedness
/usr/local/churchsoftware/topics/Lawsuits
/usr/local/churchsoftware/topics/God's love
/usr/local/churchsoftware/topics/Body piercing
/usr/local/churchsoftware/topics/Wisdom
/usr/local/churchsoftware/topics/Resurrection of Christ
/usr/local/churchsoftware/topics/Christians and war
/usr/local/churchsoftware/topics/Role of Sisters, Women in the Church
/usr/local/churchsoftware/topics/Covenant
/usr/local/churchsoftware/topics/Widow
/usr/local/churchsoftware/topics/Singing
/usr/local/churchsoftware/topics/Christ's relationship to God
/usr/local/churchsoftware/topics/Fornication
/usr/local/churchsoftware/topics/Jeshurun
/usr/local/churchsoftware/topics/Worship
/usr/local/churchsoftware/topics/Disfigure
/usr/local/churchsoftware/topics/Abandonment
/usr/local/churchsoftware/topics/Happiness
/usr/local/churchsoftware/topics/Prosperity from the LORD
/usr/local/churchsoftware/topics/Kidnapping
/usr/local/churchsoftware/topics/Music
/usr/local/churchsoftware/topics/Pornography
/usr/local/churchsoftware/topics/Lies
/usr/local/churchsoftware/topics/Time management
/usr/local/churchsoftware/topics/Watchful
/usr/local/churchsoftware/topics/God, Omnipresent
/usr/local/churchsoftware/topics/Prophecy - Assyria
/usr/local/churchsoftware/topics/Pope, The
/usr/local/churchsoftware/topics/Prophecy - Memphis
/usr/local/churchsoftware/topics/House, Dedicating a new
/usr/local/churchsoftware/topics/Spiritual blessings
/usr/local/churchsoftware/topics/Zeal
/usr/local/churchsoftware/topics/Hair
/usr/local/churchsoftware/topics/Pre-marital sex
/usr/local/churchsoftware/topics/Contentment
/usr/local/churchsoftware/topics/Prayers by parents for their children
/usr/local/churchsoftware/topics/Benevolence
/usr/local/churchsoftware/topics/Brotherhood
/usr/local/churchsoftware/topics/Curses
/usr/local/churchsoftware/topics/Attendance
/usr/local/churchsoftware/topics/Lord's Prayer
/usr/local/churchsoftware/topics/Fellowship of the Righteous
/usr/local/churchsoftware/topics/Forgiving ones enemies
/usr/local/churchsoftware/topics/Excuses
/usr/local/churchsoftware/topics/Prophets
/usr/local/churchsoftware/topics/Integrity
/usr/local/churchsoftware/topics/Sadducees
/usr/local/churchsoftware/topics/Caution
/usr/local/churchsoftware/topics/Blindness (physical)
/usr/local/churchsoftware/topics/Brothers in Christ should not seek prominence
/usr/local/churchsoftware/topics/Crucifixion
/usr/local/churchsoftware/topics/Achievement
/usr/local/churchsoftware/topics/Thankfulness
/usr/local/churchsoftware/topics/Division amongst Christians
/usr/local/churchsoftware/topics/Punishment eternal
/usr/local/churchsoftware/topics/Baptism
/usr/local/churchsoftware/topics/Anxiety, Examples of
/usr/local/churchsoftware/topics/Criticism
/usr/local/churchsoftware/topics/Finances
/usr/local/churchsoftware/topics/Choosing to serve God
/usr/local/churchsoftware/topics/Abortion
/usr/local/churchsoftware/topics/Prayer
/usr/local/churchsoftware/topics/Blasphemy
/usr/local/churchsoftware/topics/Atonement
/usr/local/churchsoftware/topics/Christ's anger
/usr/local/churchsoftware/topics/Intercession
/usr/local/churchsoftware/topics/God's name, Taking in vain
/usr/local/churchsoftware/topics/Battle calls
/usr/local/churchsoftware/topics/Marriage
/usr/local/churchsoftware/topics/Eternity
/usr/local/churchsoftware/topics/Chance
/usr/local/churchsoftware/topics/Works
/usr/local/churchsoftware/topics/Breaking of bread
/usr/local/churchsoftware/topics/Eating disorders
/usr/local/churchsoftware/topics/Judging and examining ourselves
/usr/local/churchsoftware/topics/Sexual sins
/usr/local/churchsoftware/topics/Pregnancy before marriage
/usr/local/churchsoftware/topics/Dancing
/usr/local/churchsoftware/topics/Forgiving others
/usr/local/churchsoftware/topics/Diet
/usr/local/churchsoftware/topics/Self-examination
/usr/local/churchsoftware/topics/Resurrection
/usr/local/churchsoftware/topics/Birth control
/usr/local/churchsoftware/topics/Darkness
/usr/local/churchsoftware/topics/Espousal
/usr/local/churchsoftware/topics/Knowing Christ
/usr/local/churchsoftware/topics/Veils, coverings for women
/usr/local/churchsoftware/topics/Prophecies by Jesus
/usr/local/churchsoftware/topics/Leprosy
/usr/local/churchsoftware/topics/Hope
/usr/local/churchsoftware/topics/Bargains
/usr/local/churchsoftware/topics/Theft
/usr/local/churchsoftware/topics/Spiritual warfare
/usr/local/churchsoftware/topics/Clothing, Acceptable and unacceptable
/usr/local/churchsoftware/topics/Polygamy, Examples of
/usr/local/churchsoftware/topics/God revealed in nature
/usr/local/churchsoftware/topics/Husbands
/usr/local/churchsoftware/topics/Poor
/usr/local/churchsoftware/topics/Employee, Employer
/usr/local/churchsoftware/topics/Cremation
/usr/local/churchsoftware/topics/Images
/usr/local/churchsoftware/topics/Blessing
/usr/local/churchsoftware/topics/Backsliding
/usr/local/churchsoftware/topics/Sanitation
/usr/local/churchsoftware/topics/Aging, Life expectency
/usr/local/churchsoftware/topics/Prayer, Intercessory
/usr/local/churchsoftware/topics/Patience
/usr/local/churchsoftware/topics/Celebration
/usr/local/churchsoftware/topics/Law of Moses, How Christ fulfilled the Law
/usr/local/churchsoftware/topics/Beatitudes
/usr/local/churchsoftware/topics/Animal symbols represent kings, kingdoms
/usr/local/churchsoftware/topics/Earthquakes
/usr/local/churchsoftware/topics/Parents
/usr/local/churchsoftware/topics/Doubt
/usr/local/churchsoftware/topics/Childrearing
/usr/local/churchsoftware/topics/Nature of Christ
/usr/local/churchsoftware/topics/Bible study
/usr/local/churchsoftware/topics/Prodigal son, The
/usr/local/churchsoftware/topics/Sorrow for sin
/usr/local/churchsoftware/topics/Anger
/usr/local/churchsoftware/topics/Confidence
/usr/local/churchsoftware/topics/Infertility
/usr/local/churchsoftware/topics/Righteousness
/usr/local/churchsoftware/topics/Life, Enjoying
/usr/local/churchsoftware/topics/Doubleminded
/usr/local/churchsoftware/topics/Soberness
/usr/local/churchsoftware/topics/Drugs, Fertility
/usr/local/churchsoftware/topics/Signs
/usr/local/churchsoftware/topics/Taxes
/usr/local/churchsoftware/topics/Hell in the Old Testament
/usr/local/churchsoftware/topics/Conformity
/usr/local/churchsoftware/topics/Complaining
/usr/local/churchsoftware/topics/Church and State
/usr/local/churchsoftware/topics/Suicide
/usr/local/churchsoftware/topics/Anguish
/usr/local/churchsoftware/topics/Wealth
/usr/local/churchsoftware/topics/Bigotry
/usr/local/churchsoftware/topics/Ark of the Covenant
/usr/local/churchsoftware/topics/Foreordained
/usr/local/churchsoftware/topics/Apostasy
/usr/local/churchsoftware/topics/Jesus' second coming
/usr/local/churchsoftware/topics/Bereavement
/usr/local/churchsoftware/topics/Enticement
/usr/local/churchsoftware/topics/Armageddon
/usr/local/churchsoftware/topics/Missions
/usr/local/churchsoftware/topics/Birth, Childbirth
/usr/local/churchsoftware/topics/Charity
/usr/local/churchsoftware/topics/Elderly, Caring for the
/usr/local/churchsoftware/topics/Fruits of righteousness
/usr/local/churchsoftware/topics/Forgiveness of sins
/usr/local/churchsoftware/topics/Children
/usr/local/churchsoftware/topics/Gospel
/usr/local/churchsoftware/topics/Foundations (spiritual)
/usr/local/churchsoftware/topics/Examining self
/usr/local/churchsoftware/topics/Face Painting and Female Adornment
/usr/local/churchsoftware/topics/Bishop
/usr/local/churchsoftware/topics/Vengeance
/usr/local/churchsoftware/topics/Worldly care
/usr/local/churchsoftware/topics/Scorner
/usr/local/churchsoftware/topics/Unity
/usr/local/churchsoftware/topics/War
/usr/local/churchsoftware/topics/God's foreknowledge
/usr/local/churchsoftware/topics/Gambling
/usr/local/churchsoftware/topics/Spirit of God
/usr/local/churchsoftware/topics/Bankruptcy
/usr/local/churchsoftware/topics/Celibacy
/usr/local/churchsoftware/topics/Debtor
/usr/local/churchsoftware/topics/Jesus had brothers and sisters
/usr/local/churchsoftware/topics/Teaching
/usr/local/churchsoftware/topics/Racism
/usr/local/churchsoftware/topics/Temptation, Resisting
/usr/local/churchsoftware/topics/Mary Magdalene
/usr/local/churchsoftware/topics/Faith in God
/usr/local/churchsoftware/topics/Transformation
/usr/local/churchsoftware/topics/God's favor towards His chosen ones
/usr/local/churchsoftware/topics/Disagreement
/usr/local/churchsoftware/topics/Self-esteem, Improving low
/usr/local/churchsoftware/topics/Ignorance
/usr/local/churchsoftware/topics/Procrastination
/usr/local/churchsoftware/topics/Religion
/usr/local/churchsoftware/topics/Meditation
/usr/local/churchsoftware/topics/Madness
/usr/local/churchsoftware/topics/Call to service
/usr/local/churchsoftware/topics/Eternal life
/usr/local/churchsoftware/topics/Weddings
/usr/local/churchsoftware/topics/Cursing
/usr/local/churchsoftware/topics/Word of God
/usr/local/churchsoftware/topics/Collections, Giving money
/usr/local/churchsoftware/topics/Sabbath
/usr/local/churchsoftware/topics/Children, Teaching your
/usr/local/churchsoftware/topics/Confession of sin
/usr/local/churchsoftware/topics/Evolution
/usr/local/churchsoftware/topics/Unbelief
/usr/local/churchsoftware/topics/Israel - Prophecies of being dispersed (Diaspora)
/usr/local/churchsoftware/topics/Help those who need help
/usr/local/churchsoftware/topics/Audacity
/usr/local/churchsoftware/topics/Sunday
/usr/local/churchsoftware/topics/Hygiene
/usr/local/churchsoftware/topics/Prayer of Jabez
/usr/local/churchsoftware/topics/Youth
/usr/local/churchsoftware/topics/Deeds
/usr/local/churchsoftware/topics/Jesus, Names of
/usr/local/churchsoftware/topics/Bible
/usr/local/churchsoftware/topics/Vows
/usr/local/churchsoftware/topics/Exhumations
/usr/local/churchsoftware/topics/Impatience
/usr/local/churchsoftware/topics/Soul
/usr/local/churchsoftware/topics/Ten Commandments
/usr/local/churchsoftware/topics/Heart
/usr/local/churchsoftware/topics/Self-control
/usr/local/churchsoftware/topics/Success, Dangers of
/usr/local/churchsoftware/topics/Disguise
/usr/local/churchsoftware/topics/Seriousness
/usr/local/churchsoftware/topics/Elijah & John the Baptist
/usr/local/churchsoftware/topics/Chastening by God
/usr/local/churchsoftware/topics/Jesus sharply rebukes his disciples
/usr/local/churchsoftware/topics/Drunkenness
/usr/local/churchsoftware/topics/Female pastors, teachers
/usr/local/churchsoftware/topics/Holy Spirit, Outpouring of the
/usr/local/churchsoftware/topics/Penitent
/usr/local/churchsoftware/topics/Speech
/usr/local/churchsoftware/topics/Tabernacle
/usr/local/churchsoftware/topics/Authority
/usr/local/churchsoftware/topics/Apocalypse (great destruction)
/usr/local/churchsoftware/topics/Euthanasia
/usr/local/churchsoftware/topics/Action
/usr/local/churchsoftware/topics/Death penalty
/usr/local/churchsoftware/topics/Loneliness
/usr/local/churchsoftware/topics/Earth will not be annihilated at Christ's return
/usr/local/churchsoftware/topics/Faith in Christ
/usr/local/churchsoftware/topics/Pride of life
/usr/local/churchsoftware/topics/Overwhelmed, Feelings of being
/usr/local/churchsoftware/topics/Old age
/usr/local/churchsoftware/topics/Born again
/usr/local/churchsoftware/topics/God the Father
/usr/local/churchsoftware/topics/Fear, Overcoming
/usr/local/churchsoftware/topics/Denying Christ
/usr/local/churchsoftware/topics/Work
/usr/local/churchsoftware/topics/False witness
/usr/local/churchsoftware/topics/Stiffnecked
/usr/local/churchsoftware/topics/Passover
/usr/local/churchsoftware/topics/Fear of God
/usr/local/churchsoftware/topics/Earth on fire (figuratively speaking)
/usr/local/churchsoftware/topics/Justification
/usr/local/churchsoftware/topics/Ambition
/usr/local/churchsoftware/topics/Domestic violence
/usr/local/churchsoftware/topics/Beauty (physical)
/usr/local/churchsoftware/topics/Jury duty
/usr/local/churchsoftware/topics/Tithes
/usr/local/churchsoftware/topics/Perfection
/usr/local/churchsoftware/topics/Women's hair length
/usr/local/churchsoftware/topics/God, Infidelity to
/usr/local/churchsoftware/topics/Arthritis
/usr/local/churchsoftware/topics/Unclean food
/usr/local/churchsoftware/topics/Comfort
/usr/local/churchsoftware/topics/Fruits of sin
/usr/local/churchsoftware/topics/Jesus rebukes hypocritical religious leaders
/usr/local/churchsoftware/topics/Weather
/usr/local/churchsoftware/topics/Seven deadly sins, The
/usr/local/churchsoftware/plugins/albumGrabberPlugin.jar
/usr/local/churchsoftware/preferences/KaraokeCdg.properties
/usr/local/churchsoftware/preferences/defaultProgressBar.properties
/usr/local/churchsoftware/preferences/defaultKarMidiLyrics.properties
/usr/local/churchsoftware/skins/amarachthemepack.zip
/usr/local/churchsoftware/preferences/defaultAudioInfo.properties
/usr/local/churchsoftware/preferences/defaultAlbumGrabber.properties
/usr/local/churchsoftware/preferences/PlayList.properties
/usr/local/churchsoftware/plugins/basicPlugins.jar
/usr/local/churchsoftware/plugins/examplePlugins.jar
/usr/local/churchsoftware/preferences/defaultEqualizer.properties
/usr/local/churchsoftware/preferences/Equalizer.properties
/usr/local/churchsoftware/preferences/ProgressBar.properties
/usr/local/churchsoftware/plugins/cdgPlugin.jar
/usr/local/churchsoftware/preferences/AudioInfo.properties
/usr/local/churchsoftware/preferences/defaultPlaperbu.properties
/usr/local/churchsoftware/preferences/AlbumGrabber.properties
/usr/local/churchsoftware/preferences/defaultPlayList.properties
/usr/local/churchsoftware/preferences/KarMidiLyrics.properties
/usr/local/churchsoftware/preferences/defaultKaraokeCdg.properties
/usr/local/churchsoftware/preferences/Plaperbu.properties
/usr/share/fonts/truetype/Amharic_gfzemenu.ttf
/usr/share/fonts/truetype/Burmese_Parabaik20080421.ttf
/usr/share/fonts/truetype/General_ArialUnicodeMS.ttf
/usr/local/churchsoftware/bibles/englishkjv.jar
/usr/local/churchsoftware/docs/Migration_v5.1.pdf
/usr/local/churchsoftware/docs/Getting_Started_With_Source_Code.pdf
/usr/local/churchsoftware/docs/User_Guide_v5.1.pdf
/usr/local/churchsoftware/docs/Linux_Installation_Guide_v5.1.pdf
/usr/local/churchsoftware/docs/Mac_Installation_Guide_v5.1.pdf
/usr/local/churchsoftware/docs/Troubleshoot_v5.1.pdf
/usr/local/churchsoftware/docs/Music_Display_Guide_v5.1.pdf
/usr/local/churchsoftware/docs/Developer_Guide_v5.1.pdf
/usr/local/churchsoftware/docs/Design_Document.pdf
/usr/local/churchsoftware/docs/Windows_Installation_Guide_v5.1.pdf
/usr/local/churchsoftware/source_code.tar.gz
/usr/local/churchsoftware/Uninstaller/uninstaller.jar

---

### Post by stlsaint on 2009-07-31
is it necessary that i run from command line or can i just right click and select open with sun jave 6.0?

---

### Post by jerome1232 on 2009-08-01
Is there any documentation on the developers website? 

I can't be of much help since it seems to be an error with the installer. 

Perhaps you should contact the developer or seek help on the developers site as well.

edit: I think you can double click .jar's and they'll run, but you may need to run this installer as root.

---

### Post by stlsaint on 2009-08-01
does that mean i have to run in terminal?! man that sucks considering terminal is giving me a headache right now!

---

### Post by jerome1232 on 2009-08-01
> **stlsaint said:**
> does that mean i have to run in terminal?! man that sucks considering terminal is giving me a headache right now!

That's funny finding things to click in gui's gives me headache's :P

---

### Post by mc4man on 2009-08-01
Use the full 'pack' here (includes a install_linux_fonts.sh file
[http://www.churchsw.org/content/downloads](http://www.churchsw.org/content/downloads)

If you didn't wish the full whatever I guess you could try putting it in (after the dir is created and populated, before final 'steps'


install_linux_fonts.sh
```
#!/bin/sh

cd /usr/share/fonts/truetype
/usr/bin/mkfontscale && /usr/bin/mkfontdir
/usr/bin/fc-cache
```

edit :
read here
[http://www.churchsw.org/content/guides-and-documentations](http://www.churchsw.org/content/guides-and-documentations)

---

### Post by stlsaint on 2009-08-01
thanks i will try both!!

---

### Post by stlsaint on 2009-08-01
making file was to no avail...now downloading full pack!!

---

### Post by stlsaint on 2009-08-01
main pack gave me the same error but with a different file name!!

---

### Post by stlsaint on 2009-08-01
im thinking its the jar package!!

---

### Post by mc4man on 2009-08-01
> im thinking its the jar package!! 

Well it will go ahead and install and run though the install seems poorly implemented at best.

Did both the minimal and full, for minimal used a self written fonts script, worked fine if inserted when installer pauses at last few steps.

The error about not finding the mac font script is not fatal, you should be able to continue on (where it installs 2 .deb packages and finishes.

Small observations (noting I don't install jar stuff often

Didn't matter if installed from cli or right click, same results

Installed on hardy, switched my default java to java-6-sun before starting

The 3 files deposited on the desktop are pretty much worthless

The only way I saw to start without a java error was from the command line, it does open and work fine to the extent I tried

> doug@doug-laptop:~$ cd /usr/local/churchsoftware && sudo ./start.sh
[Please make sure have JAVA_HOME set. Trying to execute JAVA from PATH]
*********************************
    Church Software 5.14
    Build Date: 31-Jul-2009
    [www.churchsw.org](www.churchsw.org)
    Public Domain
*********************************
Using.. Java 1.6.0_14
Fobs4JMF - Native shared library found
Fobs4JMF - Native shared library found
Little Endian

At this point it's opened and running....

The launcher had this as an Exec= which doesn't work
java  -Xms64m -Xmx256m -Xss1m -jar /usr/local/churchsoftware/church.jar

I didn't do a java home export command

Note I had used the built-in updater to patch to 5.14
(( I think doing the patch had the effect of slightly borking firefox 3.5.1, - no use of bookmarks, history, ect. Was easily fixed by deleting a root owned file in my profile in ~/.mozilla

The installer, when installing the 2 .deb packages, forces a lower version if they're already installed  though the ubuntu versions are and would be fine. Not a big deal but doesn't seem right 

So I'd think you could get it running and maybe figure out the desktop launcher, help file, non admin. use ect.
(the launcher for the help file (pdf) is trying to use acroread...? 

What does work very smoothly is the uninstaller, which I'm going to avail myself of now
good luck

---

