---
title: "KDENlive Crashes Unexpectedly When Pausing/Starting a Video"
date: 2011-05-08
forum: General Help
---

### Post by elcotlo13 on 2011-05-08
**Not even 20 seconds into editing, I pause and restart a video a few  times to find the best place to cut, and the program crashes completely.**
 
**This is the error message I receive:**
 
*Executable: kdenlive PID: 11926 Signal: 11 (Segmentation fault)*
 

**What does this mean, and what can I do about it?**
 
**I ran kdesudo kdenlive in the terminal and received this list. The problem is at the end.**
 

[I]guthrie@JARVIS:~$ kdesudo kdenlive
project monitor connected
clip monitor connected
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kbuildsycoca4(2233) KBuildMimeTypeFactory::createEntry: Missing  field in "application/x-note.xml"
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/gcalctool.desktop" is not  compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry MimeType  in "/usr/share/applications/xfburn.desktop" is not compliant with XDG  standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/fiberlamp.desktop"  is not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/gltext.desktop" is  not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/glcells.desktop" is  not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/glmatrix.desktop" is  not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/fuzzyflakes.desktop"  is not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in  "/usr/share/applications/screensavers/antspotlight.desktop" is not  compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/hypertorus.desktop"  is not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/glblur.desktop" is  not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/glschool.desktop" is  not compliant with XDG standard (missing trailing semicolon).
kbuildsycoca4(2233) KConfigGroup::readXdgListEntry: List entry  Categories in "/usr/share/applications/screensavers/glslideshow.desktop"  is not compliant with XDG standard (missing trailing semicolon).
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kio_trash(2257)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
(2223)/ KStartupInfo::createNewStartupId: creating:  "JARVIS;1304867859;421384;2223_TIME0" : "unnamed app"
kbuildsycoca4 running...
[mpeg @ 0x95cf3d0]read_seek: 0 45000
[mpeg @ 0x95cf3d0]using cached pos_min=0x680e dts_min=45000
[mpeg @ 0x95cf3d0]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x95cf3d0]gen_seek: 0 45000
[mpeg @ 0x95cf3d0]pos=0x680e 45000<=45000<=48003
[mpeg @ 0x92b4260]read_seek: 0 45000
[mpeg @ 0x92b4260]using cached pos_min=0x680e dts_min=45000
[mpeg @ 0x92b4260]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x92b4260]gen_seek: 0 45000
[mpeg @ 0x92b4260]pos=0x680e 45000<=45000<=48003
[mpeg @ 0x92b5ea0]read_seek: 0 0
[mpeg @ 0x92b5ea0]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x92b5ea0]gen_seek: 0 0
[mpeg @ 0x92b5ea0]pos_min=0x80e pos_max=0x680e dts_min=41997 dts_max=45000
[mpeg @ 0x92b5ea0]2062 26638 26638 / 41997 45000 45000 target:0 limit:26638 start:2063 noc:1
[mpeg @ 0x92b5ea0]pos=0x80e 41997<=0<=45000
[mpeg @ 0x96c7050]read_seek: 0 45000
[mpeg @ 0x96c7050]using cached pos_min=0x680e dts_min=45000
[mpeg @ 0x96c7050]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x96c7050]gen_seek: 0 45000
[mpeg @ 0x96c7050]pos=0x680e 45000<=45000<=48003
[mpeg @ 0x96ea400]read_seek: 0 45000
[mpeg @ 0x96ea400]using cached pos_min=0x680e dts_min=45000
[mpeg @ 0x96ea400]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x96ea400]gen_seek: 0 45000
[mpeg @ 0x96ea400]pos=0x680e 45000<=45000<=48003
[mpeg @ 0x96f35d0]read_seek: 0 0
[mpeg @ 0x96f35d0]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x96f35d0]gen_seek: 0 0
[mpeg @ 0x96f35d0]pos_min=0x80e pos_max=0x680e dts_min=41997 dts_max=45000
[mpeg @ 0x96f35d0]2062 26638 26638 / 41997 45000 45000 target:0 limit:26638 start:2063 noc:1
[mpeg @ 0x96f35d0]pos=0x80e 41997<=0<=45000
[mpeg @ 0x9932a90]read_seek: 0 45000
[mpeg @ 0x9932a90]using cached pos_min=0x580e dts_min=45000
[mpeg @ 0x9932a90]using cached pos_max=0x580e pos_limit=0x580e dts_max=45000
[mpeg @ 0x9932a90]gen_seek: 0 45000
[mpeg @ 0x9932a90]pos=0x580e 45000<=45000<=48003
[mpeg @ 0x98dfb80]read_seek: 0 45000
[mpeg @ 0x98dfb80]using cached pos_min=0x580e dts_min=45000
[mpeg @ 0x98dfb80]using cached pos_max=0x580e pos_limit=0x580e dts_max=45000
[mpeg @ 0x98dfb80]gen_seek: 0 45000
[mpeg @ 0x98dfb80]pos=0x580e 45000<=45000<=48003
[mpeg @ 0x98e8d50]read_seek: 0 0
[mpeg @ 0x98e8d50]using cached pos_max=0x580e pos_limit=0x580e dts_max=45000
[mpeg @ 0x98e8d50]gen_seek: 0 0
[mpeg @ 0x98e8d50]pos_min=0x80e pos_max=0x580e dts_min=41997 dts_max=45000
[mpeg @ 0x98e8d50]2062 22542 22542 / 41997 45000 45000 target:0 limit:22542 start:2063 noc:1
[mpeg @ 0x98e8d50]pos=0x80e 41997<=0<=45000
[mpeg @ 0x92b5ea0]read_seek: 0 1018062
[mpeg @ 0x92b5ea0]using cached pos_min=0x19c00e dts_min=318273
[mpeg @ 0x92b5ea0]using cached pos_max=0x55a80e pos_limit=0x55a80e dts_max=1084038
[mpeg @ 0x92b5ea0]gen_seek: 0 1018062
[mpeg @ 0x92b5ea0]pos_min=0x19c00e pos_max=0x55a80e dts_min=318273 dts_max=1084038
[mpeg @ 0x92b5ea0]1687566 5294094 5613582 / 318273 1038993 1084038 target:1018062 limit:5613582 start:5275328 noc:0
[mpeg @ 0x92b5ea0]pos_min=0x19c00e pos_max=0x50c80e dts_min=318273 dts_max=1038993
[mpeg @ 0x92b5ea0]1687566 5177358 5294094 / 318273 1020975 1038993 target:1018062 limit:5275327 start:5170587 noc:0
[mpeg @ 0x92b5ea0]pos_min=0x19c00e pos_max=0x4f000e dts_min=318273 dts_max=1020975
[mpeg @ 0x92b5ea0]1687566 5158926 5177358 / 318273 1017972 1020975 target:1018062 limit:5170586 start:5156119 noc:0
[mpeg @ 0x92b5ea0]pos_min=0x4eb80e pos_max=0x4f000e dts_min=1017972 dts_max=1020975
[mpeg @ 0x92b5ea0]5158926 5177358 5177358 / 1017972 1020975 1020975 target:1018062 limit:5170586 start:5158927 noc:1
[mpeg @ 0x92b5ea0]pos=0x4eb80e 1017972<=1018062<=1020975
[mpeg2video @ 0x92b7130]Missing picture start code
[mpeg @ 0x9a56de0]read_seek: 0 45000
[mpeg @ 0x9a56de0]using cached pos_min=0x680e dts_min=45000
[mpeg @ 0x9a56de0]using cached pos_max=0x680e pos_limit=0x680e dts_max=45000
[mpeg @ 0x9a56de0]gen_seek: 0 45000
[mpeg @ 0x9a56de0]pos=0x680e 45000<=45000<=48003
[mpeg @ 0x96f35d0]read_seek: 0 1648692
[mpeg @ 0x96f35d0]using cached pos_min=0x1a380e dts_min=318273
[mpeg @ 0x96f35d0]using cached pos_max=0x98c80e pos_limit=0x98c80e dts_max=1717671
[mpeg @ 0x96f35d0]gen_seek: 0 1648692
[mpeg @ 0x96f35d0]pos_min=0x1a380e pos_max=0x98c80e dts_min=318273 dts_max=1717671
[mpeg @ 0x96f35d0]1718286 9609230 10012686 / 318273 1651605 1717671 target:1648692 limit:10012686 start:9603839 noc:0
[mpeg @ 0x96f35d0]pos_min=0x1a380e pos_max=0x92a00e dts_min=318273 dts_max=1651605
[mpeg @ 0x96f35d0]1718286 9592846 9609230 / 318273 1648602 1651605 target:1648692 limit:9603838 start:9586598 noc:0
[mpeg @ 0x96f35d0]pos_min=0x92600e pos_max=0x92a00e dts_min=1648602 dts_max=1651605
[mpeg @ 0x96f35d0]9592846 9609230 9609230 / 1648602 1651605 1651605 target:1648692 limit:9603838 start:9592847 noc:1
[mpeg @ 0x96f35d0]pos=0x92600e 1648602<=1648692<=1651605
[mpeg @ 0x98e8d50]read_seek: 0 2009052
[mpeg @ 0x98e8d50]using cached pos_min=0x89600e dts_min=2008962
[mpeg @ 0x98e8d50]using cached pos_max=0x89780e pos_limit=0x89780e dts_max=2011965
[mpeg @ 0x98e8d50]gen_seek: 0 2009052
[mpeg @ 0x98e8d50]pos_min=0x89600e pos_max=0x89780e dts_min=2008962 dts_max=2011965
[mpeg @ 0x98e8d50]9003022 9009166 9009166 / 2008962 2011965 2011965 target:2009052 limit:9009166 start:9003206 noc:1
[mpeg @ 0x98e8d50]pos_min=0x89600e pos_max=0x89780e dts_min=2008962 dts_max=2011965
[mpeg @ 0x98e8d50]9003022 9009166 9009166 / 2008962 2011965 2011965 target:2009052 limit:9003205 start:9003113 noc:2
[mpeg @ 0x98e8d50]pos_min=0x89600e pos_max=0x89780e dts_min=2008962 dts_max=2011965
[mpeg @ 0x98e8d50]9003022 9009166 9009166 / 2008962 2011965 2011965 target:2009052 limit:9003112 start:9003023 noc:3
[mpeg @ 0x98e8d50]pos=0x89600e 2008962<=2009052<=2011965
[mpeg2video @ 0x991a350]Missing picture start code
    Last message repeated 16 times
[mpeg @ 0x9b5c8a0]read_seek: 0 45000
[mpeg @ 0x9b5c8a0]using cached pos_min=0x580e dts_min=45000
[mpeg @ 0x9b5c8a0]using cached pos_max=0x580e pos_limit=0x580e dts_max=45000
[mpeg @ 0x9b5c8a0]gen_seek: 0 45000
[mpeg @ 0x9b5c8a0]pos=0x580e 45000<=45000<=48003
[mpeg @ 0x96f35d0]read_seek: 0 0
[mpeg @ 0x96f35d0]using cached pos_max=0x80e pos_limit=0x80e dts_max=41997
[mpeg @ 0x96f35d0]gen_seek: 0 0
[mpeg @ 0x96f35d0]pos=0x80e 41997<=0<=45000
[mpeg @ 0x96fd150]read_seek: 0 84039
[mpeg @ 0x96fd150]using cached pos_min=0x6480e dts_min=84039
[mpeg @ 0x96fd150]using cached pos_max=0x6480e pos_limit=0x6480e dts_max=84039
[mpeg @ 0x96fd150]gen_seek: 0 84039
[mpeg @ 0x96fd150]pos=0x6480e 84039<=84039<=87042
: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
KCrash: Application 'kdenlive' crashing...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/drkonqi
Unable to start Dr. Konqi
guthrie@JARVIS:~$ [/I]

---

