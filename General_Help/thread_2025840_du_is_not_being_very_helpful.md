---
title: "du is not being very helpful"
date: 2012-07-14
forum: General Help
---

### Post by OMJD on 2012-07-14
I have an issue with one of my servers running Ubuntu. MySQL is not working because the disk is "full". 

I checked the root directory and there's 218GB of data in there but the du command won't tell me where it's all located. (unless I've missed something!) 

Also, I don't know why I'm using 218gb of data all of a sudden because I've not put more than 15GB of data on it myself, including the OS.

Output:

du -h
```

32K	./Desktop/misc/st temp/do_not_upload/rewrite/apache2
44K	./Desktop/misc/st temp/do_not_upload/rewrite
84K	./Desktop/misc/st temp/do_not_upload/blog
64K	./Desktop/misc/st temp/do_not_upload/cms
120K	./Desktop/misc/st temp/do_not_upload/forum
412K	./Desktop/misc/st temp/do_not_upload
1.8G	./Desktop/misc/st temp
1.8G	./Desktop/misc
4.0K	./Desktop/upload
4.0K	./Desktop/st temp/cpmove-richm/mms
4.0K	./Desktop/st temp/cpmove-richm/vad
8.0K	./Desktop/st temp/cpmove-richm/vf
20K	./Desktop/st temp/cpmove-richm/mysql-timestamps
529M	./Desktop/st temp/cpmove-richm/mysql
4.0K	./Desktop/st temp/cpmove-richm/psql
4.0K	./Desktop/st temp/cpmove-richm/interchange
4.0K	./Desktop/st temp/cpmove-richm/sslkeys
4.0K	./Desktop/st temp/cpmove-richm/cron
12K	./Desktop/st temp/cpmove-richm/va
4.0M	./Desktop/st temp/cpmove-richm/logs
8.0K	./Desktop/st temp/cpmove-richm/cp
4.0K	./Desktop/st temp/cpmove-richm/logaholic
4.0K	./Desktop/st temp/cpmove-richm/domainkeys/private
4.0K	./Desktop/st temp/cpmove-richm/domainkeys/public
12K	./Desktop/st temp/cpmove-richm/domainkeys
16K	./Desktop/st temp/cpmove-richm/resellerconfig
4.0K	./Desktop/st temp/cpmove-richm/counters
16K	./Desktop/st temp/cpmove-richm/userdata
4.0K	./Desktop/st temp/cpmove-richm/suspendinfo
20K	./Desktop/st temp/cpmove-richm/meta
4.0K	./Desktop/st temp/cpmove-richm/mma/pub
4.0K	./Desktop/st temp/cpmove-richm/mma/priv
12K	./Desktop/st temp/cpmove-richm/mma
4.0K	./Desktop/st temp/cpmove-richm/locale
4.0K	./Desktop/st temp/cpmove-richm/mm
4.0K	./Desktop/st temp/cpmove-richm/userconfig
4.0K	./Desktop/st temp/cpmove-richm/resellerpackages
8.0K	./Desktop/st temp/cpmove-richm/dnszones
4.0K	./Desktop/st temp/cpmove-richm/suspended
4.0K	./Desktop/st temp/cpmove-richm/resellerfeatures
4.0K	./Desktop/st temp/cpmove-richm/httpfiles
4.0K	./Desktop/st temp/cpmove-richm/sslcerts
27M	./Desktop/st temp/cpmove-richm/bandwidth
4.0K	./Desktop/st temp/cpmove-richm/homedir
12K	./Desktop/st temp/cpmove-richm/fp/sites
16K	./Desktop/st temp/cpmove-richm/fp
1009M	./Desktop/st temp/cpmove-richm
4.0K	./Desktop/st temp/cf1/upload/images
8.0K	./Desktop/st temp/cf1/upload
116K	./Desktop/st temp/cf1/PSD
636K	./Desktop/st temp/cf1
8.0K	./Desktop/st temp/do_not_upload/rewrite/iis7
8.0K	./Desktop/st temp/do_not_upload/rewrite/apache2/blog
8.0K	./Desktop/st temp/do_not_upload/rewrite/apache2/cms
8.0K	./Desktop/st temp/do_not_upload/rewrite/apache2/forum
32K	./Desktop/st temp/do_not_upload/rewrite/apache2
44K	./Desktop/st temp/do_not_upload/rewrite
84K	./Desktop/st temp/do_not_upload/blog
64K	./Desktop/st temp/do_not_upload/cms
120K	./Desktop/st temp/do_not_upload/forum
412K	./Desktop/st temp/do_not_upload
1.8G	./Desktop/st temp
3.5G	./Desktop
4.0K	./.config/ibus/bus
8.0K	./.config/ibus
4.0K	./.config/gnome-disk-utility/ata-smart-ignore
8.0K	./.config/gnome-disk-utility
8.0K	./.config/Thunar
8.0K	./.config/software-center
16K	./.config/gedit
4.0K	./.config/transmission/torrents
4.0K	./.config/transmission/blocklists
4.0K	./.config/transmission/resume
20K	./.config/transmission
4.0K	./.config/goa-1.0
4.0K	./.config/gnome-session/saved-session
8.0K	./.config/gnome-session
8.0K	./.config/compiz-1/compizconfig
12K	./.config/compiz-1
8.0K	./.config/desktop-couch
20K	./.config/dconf
4.0K	./.config/xfce4/xfwm4
44K	./.config/xfce4/xfconf/xfce-perchannel-xml
48K	./.config/xfce4/xfconf
8.0K	./.config/xfce4/panel/launcher-12
8.0K	./.config/xfce4/panel/launcher-10
8.0K	./.config/xfce4/panel/launcher-11
8.0K	./.config/xfce4/panel/launcher-9
36K	./.config/xfce4/panel
8.0K	./.config/xfce4/desktop
100K	./.config/xfce4
8.0K	./.config/eog
4.0K	./.config/enchant
8.0K	./.config/autostart
4.0K	./.config/ubuntuone
8.0K	./.config/nautilus
276K	./.config
4.0K	./.pulse
4.0K	./Public
4.0K	./bfd-1.5/files/tmp
76K	./bfd-1.5/files/rules
112K	./bfd-1.5/files
184K	./bfd-1.5
704K	./.local/share/zeitgeist/fts.index
2.1M	./.local/share/zeitgeist
8.0K	./.local/share/telepathy/mission-control
12K	./.local/share/telepathy
16K	./.local/share/applications
8.0K	./.local/share/icc
8.0K	./.local/share/Trash/info
4.0K	./.local/share/Trash/expunged
4.0K	./.local/share/Trash/files/D
8.0K	./.local/share/Trash/files
24K	./.local/share/Trash
20K	./.local/share/desktop-couch/.contacts_design
20K	./.local/share/desktop-couch/.notes_design
20K	./.local/share/desktop-couch/.bookmarks_design
76K	./.local/share/desktop-couch/.management_design
4.0K	./.local/share/desktop-couch/.delete
272K	./.local/share/desktop-couch
24K	./.local/share/webkit/icondatabase
28K	./.local/share/webkit
196K	./.local/share/gvfs-metadata
2.7M	./.local/share
2.7M	./.local
168K	./.Skype/shared_dynco
40K	./.Skype/shared_httpfe
8.0K	./.Skype/pawelszuszkiewicz/httpfe
4.0K	./.Skype/pawelszuszkiewicz/voicemail
8.0K	./.Skype/pawelszuszkiewicz/chatsync/3a
8.0K	./.Skype/pawelszuszkiewicz/chatsync/88
12K	./.Skype/pawelszuszkiewicz/chatsync/6e
32K	./.Skype/pawelszuszkiewicz/chatsync
232K	./.Skype/pawelszuszkiewicz
500K	./.Skype
4.0K	./Documents
16K	./.aptitude
4.0K	./.mysqlgui/administrator
8.0K	./.mysqlgui
8.0K	./.gconf/apps/shotwell/video
8.0K	./.gconf/apps/shotwell/preferences/slideshow
8.0K	./.gconf/apps/shotwell/preferences/slideshow_transition
8.0K	./.gconf/apps/shotwell/preferences/files
8.0K	./.gconf/apps/shotwell/preferences/window
8.0K	./.gconf/apps/shotwell/preferences/editing
8.0K	./.gconf/apps/shotwell/preferences/ui
52K	./.gconf/apps/shotwell/preferences
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.transitions.slide
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.transitions.crumble
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.picasa
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.yandex-fotki
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.transitions.fade
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.facebook
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.piwigo
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.flickr
8.0K	./.gconf/apps/shotwell/plugins/org.yorba.shotwell.publishing.youtube
76K	./.gconf/apps/shotwell/plugins
8.0K	./.gconf/apps/shotwell/sharing/picasa
8.0K	./.gconf/apps/shotwell/sharing/flickrubuntu
8.0K	./.gconf/apps/shotwell/sharing/org.yorba.shotwell.publishing.yandex-fotki
8.0K	./.gconf/apps/shotwell/sharing/org.yorba.shotwell.publishing.piwigo
8.0K	./.gconf/apps/shotwell/sharing/facebook
8.0K	./.gconf/apps/shotwell/sharing/youtube
56K	./.gconf/apps/shotwell/sharing
8.0K	./.gconf/apps/shotwell/printing
204K	./.gconf/apps/shotwell
8.0K	./.gconf/apps/vinagre
8.0K	./.gconf/apps/blueman/plugins/PulseAudio
8.0K	./.gconf/apps/blueman/plugins/SerialManager
8.0K	./.gconf/apps/blueman/plugins/Headset
8.0K	./.gconf/apps/blueman/plugins/RecentConns
8.0K	./.gconf/apps/blueman/plugins/DiscvManager
8.0K	./.gconf/apps/blueman/plugins/KillSwitch
8.0K	./.gconf/apps/blueman/plugins/StatusIcon
60K	./.gconf/apps/blueman/plugins
8.0K	./.gconf/apps/blueman/transfer
76K	./.gconf/apps/blueman
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/general/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/general/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/general
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/expo
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/animation
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/obs
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wall
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/composite
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/scale
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/cube
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/clone
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/snap
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/fade
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/session
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/blur
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/grid
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/water
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0/options
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/core
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/detection
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/place
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/move
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/decor
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0/options
20K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0
24K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/commands
8.0K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0/options
12K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0
16K	./.gconf/apps/compizconfig-1/profiles/Default/plugins/resize
660K	./.gconf/apps/compizconfig-1/profiles/Default/plugins
680K	./.gconf/apps/compizconfig-1/profiles/Default
684K	./.gconf/apps/compizconfig-1/profiles
692K	./.gconf/apps/compizconfig-1
8.0K	./.gconf/apps/seahorse/listing
12K	./.gconf/apps/seahorse
8.0K	./.gconf/apps/brasero/config
8.0K	./.gconf/apps/brasero/display
8.0K	./.gconf/apps/brasero/filter
8.0K	./.gconf/apps/brasero/drives
36K	./.gconf/apps/brasero
8.0K	./.gconf/apps/nm-applet
8.0K	./.gconf/apps/gnome-system-log
8.0K	./.gconf/apps/file-roller/dialogs/extract
8.0K	./.gconf/apps/file-roller/dialogs/add
8.0K	./.gconf/apps/file-roller/dialogs/batch-add
8.0K	./.gconf/apps/file-roller/dialogs/last_output
36K	./.gconf/apps/file-roller/dialogs
8.0K	./.gconf/apps/file-roller/general
8.0K	./.gconf/apps/file-roller/listing
8.0K	./.gconf/apps/file-roller/ui
64K	./.gconf/apps/file-roller
8.0K	./.gconf/apps/totem/plugins/opensubtitles
12K	./.gconf/apps/totem/plugins
16K	./.gconf/apps/totem
8.0K	./.gconf/apps/gnome-terminal/profiles/Default
12K	./.gconf/apps/gnome-terminal/profiles
16K	./.gconf/apps/gnome-terminal
8.0K	./.gconf/apps/onboard/icon_palette
16K	./.gconf/apps/onboard
8.0K	./.gconf/apps/notify-osd
8.0K	./.gconf/apps/update-notifier
8.0K	./.gconf/apps/evince
8.0K	./.gconf/apps/compiz-1/general/screen0/options
12K	./.gconf/apps/compiz-1/general/screen0
16K	./.gconf/apps/compiz-1/general
8.0K	./.gconf/apps/compiz-1/plugins/gnomecompat/screen0/options
12K	./.gconf/apps/compiz-1/plugins/gnomecompat/screen0
16K	./.gconf/apps/compiz-1/plugins/gnomecompat
20K	./.gconf/apps/compiz-1/plugins
40K	./.gconf/apps/compiz-1
8.0K	./.gconf/apps/evolution/calendar/notify
16K	./.gconf/apps/evolution/calendar
20K	./.gconf/apps/evolution
8.0K	./.gconf/apps/eog/view
8.0K	./.gconf/apps/eog/ui
20K	./.gconf/apps/eog
8.0K	./.gconf/apps/empathy/conversation
8.0K	./.gconf/apps/empathy/notifications
8.0K	./.gconf/apps/empathy/sounds
8.0K	./.gconf/apps/empathy/hints
8.0K	./.gconf/apps/empathy/ui
8.0K	./.gconf/apps/empathy/location
8.0K	./.gconf/apps/empathy/contacts
64K	./.gconf/apps/empathy
8.0K	./.gconf/apps/gedit-2/preferences/syntax_highlighting
8.0K	./.gconf/apps/gedit-2/preferences/print/fonts
8.0K	./.gconf/apps/gedit-2/preferences/print/page
20K	./.gconf/apps/gedit-2/preferences/print
8.0K	./.gconf/apps/gedit-2/preferences/search_highlighting
8.0K	./.gconf/apps/gedit-2/preferences/encodings
8.0K	./.gconf/apps/gedit-2/preferences/editor/wrap_mode
8.0K	./.gconf/apps/gedit-2/preferences/editor/auto_indent
8.0K	./.gconf/apps/gedit-2/preferences/editor/save
8.0K	./.gconf/apps/gedit-2/preferences/editor/right_margin
8.0K	./.gconf/apps/gedit-2/preferences/editor/line_numbers
8.0K	./.gconf/apps/gedit-2/preferences/editor/bracket_matching
8.0K	./.gconf/apps/gedit-2/preferences/editor/current_line
8.0K	./.gconf/apps/gedit-2/preferences/editor/font
8.0K	./.gconf/apps/gedit-2/preferences/editor/colors
8.0K	./.gconf/apps/gedit-2/preferences/editor/smart_home_end
8.0K	./.gconf/apps/gedit-2/preferences/editor/undo
8.0K	./.gconf/apps/gedit-2/preferences/editor/cursor_position
8.0K	./.gconf/apps/gedit-2/preferences/editor/tabs
108K	./.gconf/apps/gedit-2/preferences/editor
8.0K	./.gconf/apps/gedit-2/preferences/ui/bottom_panel
8.0K	./.gconf/apps/gedit-2/preferences/ui/toolbar
8.0K	./.gconf/apps/gedit-2/preferences/ui/statusbar
8.0K	./.gconf/apps/gedit-2/preferences/ui/recents
8.0K	./.gconf/apps/gedit-2/preferences/ui/side_pane
44K	./.gconf/apps/gedit-2/preferences/ui
200K	./.gconf/apps/gedit-2/preferences
8.0K	./.gconf/apps/gedit-2/plugins
212K	./.gconf/apps/gedit-2
8.0K	./.gconf/apps/deja-dup/s3
8.0K	./.gconf/apps/deja-dup/ssh
8.0K	./.gconf/apps/deja-dup/file
32K	./.gconf/apps/deja-dup
8.0K	./.gconf/apps/gnome_settings_daemon/keybindings
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/sound
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/xsettings
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/smartcard
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/a11y-keyboard
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/keybindings
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/background
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/keyboard
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/housekeeping
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/font
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/mouse
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/xrandr
8.0K	./.gconf/apps/gnome_settings_daemon/plugins/clipboard
100K	./.gconf/apps/gnome_settings_daemon/plugins
8.0K	./.gconf/apps/gnome_settings_daemon/xrandr
120K	./.gconf/apps/gnome_settings_daemon
8.0K	./.gconf/apps/nautilus/preferences
12K	./.gconf/apps/nautilus
8.0K	./.gconf/apps/update-manager
8.0K	./.gconf/apps/panel/global
12K	./.gconf/apps/panel
8.0K	./.gconf/apps/metacity/general
8.0K	./.gconf/apps/metacity/global_keybindings
8.0K	./.gconf/apps/metacity/window_keybindings
28K	./.gconf/apps/metacity
8.0K	./.gconf/apps/indicator-session
1.8M	./.gconf/apps
8.0K	./.gconf/system/smb
8.0K	./.gconf/system/http_proxy
8.0K	./.gconf/system/proxy
28K	./.gconf/system
8.0K	./.gconf/desktop/gnome/nautilus-sendto
8.0K	./.gconf/desktop/gnome/applications/calendar
8.0K	./.gconf/desktop/gnome/applications/terminal
8.0K	./.gconf/desktop/gnome/applications/tasks
8.0K	./.gconf/desktop/gnome/applications/at
36K	./.gconf/desktop/gnome/applications
8.0K	./.gconf/desktop/gnome/lockdown
8.0K	./.gconf/desktop/gnome/sound
8.0K	./.gconf/desktop/gnome/thumbnail_cache
8.0K	./.gconf/desktop/gnome/interface
8.0K	./.gconf/desktop/gnome/accessibility/keyboard
8.0K	./.gconf/desktop/gnome/accessibility/mouse
20K	./.gconf/desktop/gnome/accessibility
8.0K	./.gconf/desktop/gnome/peripherals/smartcard
8.0K	./.gconf/desktop/gnome/peripherals/keyboard/general
8.0K	./.gconf/desktop/gnome/peripherals/keyboard/kbd
8.0K	./.gconf/desktop/gnome/peripherals/keyboard/indicator
8.0K	./.gconf/desktop/gnome/peripherals/keyboard/preview
36K	./.gconf/desktop/gnome/peripherals/keyboard
8.0K	./.gconf/desktop/gnome/peripherals/mouse
8.0K	./.gconf/desktop/gnome/peripherals/touchpad
64K	./.gconf/desktop/gnome/peripherals
8.0K	./.gconf/desktop/gnome/keybindings
8.0K	./.gconf/desktop/gnome/background
8.0K	./.gconf/desktop/gnome/remote_access
8.0K	./.gconf/desktop/gnome/font_rendering
8.0K	./.gconf/desktop/gnome/thumbnailers
208K	./.gconf/desktop/gnome
8.0K	./.gconf/desktop/pgp/recipients
8.0K	./.gconf/desktop/pgp/keyservers
24K	./.gconf/desktop/pgp
236K	./.gconf/desktop
2.0M	./.gconf
8.0K	./.mission-control/accounts
12K	./.mission-control
4.0K	./.macromedia/Flash_Player/#SharedObjects/7X53N92U/skype.com/#user
4.0K	./.macromedia/Flash_Player/#SharedObjects/7X53N92U/skype.com/#ui
12K	./.macromedia/Flash_Player/#SharedObjects/7X53N92U/skype.com
16K	./.macromedia/Flash_Player/#SharedObjects/7X53N92U
20K	./.macromedia/Flash_Player/#SharedObjects
8.0K	./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skype.com
16K	./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
20K	./.macromedia/Flash_Player/macromedia.com/support/flashplayer
24K	./.macromedia/Flash_Player/macromedia.com/support
28K	./.macromedia/Flash_Player/macromedia.com
52K	./.macromedia/Flash_Player
56K	./.macromedia
218G	.
```
root@neptune:~# 

Any ideas?

---

### Post by papibe on 2012-07-14
Try 'df' first.

Could you post the result of this command?
```
df -h
```
Regards.

---

### Post by OMJD on 2012-07-14
> **papibe said:**
> Try 'df' first.

Could you post the result of this command?
```
df -h
```
Regards.

root@neptune:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       231G  230G     0 100% /
udev            973M  4.0K  973M   1% /dev
tmpfs           393M  876K  392M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            982M     0  982M   0% /run/shm
overflow        1.0M  4.0K 1020K   1% /tmp

---

### Post by plucky on 2012-07-14
And also post long lists between [noparse]```
your text
```[/noparse] brackets

Good Luck

---

### Post by diesch on 2012-07-14
What's the output of
```
ls -lh .
```

---

### Post by OMJD on 2012-07-14
> **diesch said:**
> What's the output of
```
ls -lh .
```

```

root@neptune:~# ls -lh
total 20K
drw-r--r-- 3 root root 4.0K Jan  9  2012 bfd-1.5
drwxr-xr-x 5 root root 4.0K Jun 24 19:28 Desktop
drwxr-xr-x 2 root root 4.0K Apr 17 21:25 Documents
drwxr-xr-x 2 root root 4.0K Jun  6 23:08 Downloads
drwxr-xr-x 2 root root 4.0K Apr 17 21:25 Public
root@neptune:~# 

```

---

### Post by papibe on 2012-07-14
> **OMJD said:**
> /dev/sda1       231G  230G     0 100% /
I see it.

You can use the program 'Disk Usage Analizer' to navigate to the directory and files that are taking that much space.

If that won't open. You use du, but directory by directory. Let's assume the space is mainly used by your user files. For example, to see which directory is using more space on your home:
```
du -s * .* | sort -n | tail -n 20
```
Let us know how it goes.
Regards.

---

### Post by diesch on 2012-07-14
> **OMJD said:**
> ```

root@neptune:~# ls -lh
total 20K
drw-r--r-- 3 root root 4.0K Jan  9  2012 bfd-1.5
drwxr-xr-x 5 root root 4.0K Jun 24 19:28 Desktop
drwxr-xr-x 2 root root 4.0K Apr 17 21:25 Documents
drwxr-xr-x 2 root root 4.0K Jun  6 23:08 Downloads
drwxr-xr-x 2 root root 4.0K Apr 17 21:25 Public
root@neptune:~# 

```

Sorry, that should be
```
ls -alh .
```

---

