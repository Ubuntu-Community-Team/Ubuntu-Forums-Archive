---
title: "UMPlayer Not Working"
date: 2012-07-29
forum: General Help
---

### Post by Dylan1473 on 2012-07-29
So, I'm having some trouble with _[UMPlayer]("http://www.umplayer.com/")_ and I'm not sure why. My problem is this: it does not play videos. Seeing as UMPlayer is a video player, this is a rather serious problem.

The program starts up fine and the GUI is there, but no video or sound plays and the bar showing the time of the video does not move. I've tried with a number of different videos in a number of different formats with no change. Playing the very same videos in SMPlayer or Totem (or even just regular MPlayer) works fine. I only recently got UMPlayer and it worked at first, broke after a couple days. Though not 100% certain, I don't believe UMPlayer was updated at any point after I got it (I install updates from the terminal and generally read the list so I think I probably would've noticed). Changing desktop environments does not help - I've tried it in Enlightenment, Openbox and XFCE with no luck. I don't think I changed any options from their defaults.

I have tried uninstalling (including with purge) and reinstalling it and even manually installing it from source with no luck. I'd note that even after purging it it still remembered a short video history and my position in these videos though, so I'm not entirely sure the purge got rid of everything.

I don't know how widely used UMPlayer is so I'm hoping there's someone around that knows what might be wrong here. I realize there's not a lot to go on but I'll happily provide any other necessary information. Any help would be appreciated.

---

### Post by andrew.46 on 2012-07-30
First thing to look at are the logs for MPlayer and UMPlayer which you will see under Options --> View Logs.

---

### Post by Dylan1473 on 2012-08-01
Well, the MPlayer log accessible from UMPlayer appears to be empty, not sure what that means. The UMPlayer log looks like this:

```
  p, li { white-space: pre-wrap; }  [00:03:05:023] main: lock_file: /home/dylan/.config/umplayer/umplayer_init.lock
 [00:03:05:024] global_init
 [00:03:05:024] global_init: config file: '/home/dylan/.config/umplayer/umplayer.ini'
 [00:03:05:024] Preferences::load
 [00:03:05:025] AssStyles::load
 [00:03:05:029] Translator::loadCatalog: can't load qt_en_US from /usr/share/umplayer/translations
 [00:03:05:030] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
 [00:03:05:030] Translator::loadCatalog: successfully loaded umplayer_en_US from /usr/share/umplayer/translations
 [00:03:05:030] This is UMPlayer v. 0.97 running on Linux
 [00:03:05:030] Compiled with Qt v. 4.7.4, using 4.8.1
 [00:03:05:030]  * application path: '/usr/bin'
 [00:03:05:030]  * data path: '/usr/share/umplayer'
 [00:03:05:030]  * translation path: '/usr/share/umplayer/translations'
 [00:03:05:030]  * doc path: '/usr/share/doc/umplayer'
 [00:03:05:030]  * themes path: '/usr/share/umplayer/themes'
 [00:03:05:030]  * shortcuts path: '/usr/share/umplayer/shortcuts'
 [00:03:05:030]  * config path: '/home/dylan/.config/umplayer'
 [00:03:05:030]  * ini path: '/home/dylan/.config/umplayer'
 [00:03:05:030]  * file for subtitles' styles: '/home/dylan/.config/umplayer/styles.***'
 [00:03:05:030]  * current path: '/home/dylan'
 [00:03:05:030] UMPlayer::processArgs: arguments: 1
 [00:03:05:030] UMPlayer::processArgs: 0 = umplayer
 [00:03:05:030] UMPlayer::processArgs: files_to_play: count: 0
 [00:03:05:030] MyClient::MyClient
 [00:03:05:030] UMPlayer::processArgs: trying to connect to port 45544
 [00:03:05:031] UMPlayer::gui: changed working directory to app path
 [00:03:05:031] UMPlayer::gui: current directory: /usr/bin
 [00:03:05:075] Core::changeFileSettingsMethod: hash
 [00:03:05:079] MplayerLayer::setRepaintBackground: 0
 [00:03:05:079] Preferences::monitor_aspect_double
 [00:03:05:079]  warning: monitor_aspect couldn't be parsed!
 [00:03:05:079]  monitor_aspect set to 0
 [00:03:05:098] Playlist::setModified: 0
 [00:03:05:134] Playlist::loadSettings
 [00:03:05:134] Playlist::addItem: '/home/dylan/Videos/StarForge - First Playable Release - YouTube [360p].flv'
 [00:03:05:134] Playlist::setModified: 0
 [00:03:05:134] Playlist::updateView
 [00:03:05:134] Playlist::updateView: name: 'StarForge - First Playable Release - YouTube [360p].flv'
 [00:03:05:148] Style name: 'windows'
 [00:03:05:148] Style class name: 'QWindowsStyle'
 [00:03:05:211] Favorites::load
 [00:03:05:211] TVList::parse_channels_conf
 [00:03:05:211] VList::parse_channels_conf: /home/dylan/.mplayer/channels.conf.ter doesn't exist
 [00:03:05:211] TVList::parse_channels_conf: can't open /home/dylan/.mplayer/channels.conf
 [00:03:05:211] Favorites::load
 [00:03:05:211] TVList::parse_channels_conf
 [00:03:05:211] VList::parse_channels_conf: /home/dylan/.mplayer/channels.conf.ter doesn't exist
 [00:03:05:211] TVList::parse_channels_conf: can't open /home/dylan/.mplayer/channels.conf
 [00:03:05:215] BaseGui::initializeMenus
 [00:03:05:236] BaseGui::initializeMenus
 [00:03:05:236] BaseGui::updateRecents
 [00:03:05:236] BaseGui::updateWidgets
 [00:03:05:236] Core::visualizeMotionVectors: 1
 [00:03:05:236] Core::changeSubVisilibity: 1
 [00:03:05:236] Core::tellmp: 'sub_visibility 1'
 [00:03:05:236] WARNING:  tellmp: no process running: sub_visibility 1
 [00:03:05:236] Core::displayMessage
 [00:03:05:237] BaseGui::setStayOnTop: 0
 [00:03:05:237] BaseGui::setStayOnTop: nothing to do
 [00:03:05:237] BaseGui::updateWidgets
 [00:03:05:237] BaseGui::updateWidgets
 [00:03:05:237] BaseGui::updateRecents
 [00:03:05:237] Preferences::save
 [00:03:05:237] AssStyles::save
 [00:03:05:239] BaseGui::initializeGui: server running on port 40237
 [00:03:05:356] BaseGui::initializeMenus
 [00:03:05:356] BaseGui::updateRecents
 [00:03:05:356] BaseGui::updateWidgets
 [00:03:05:356] BaseGuiPlus::loadConfig
 [00:03:05:356] DefaultGui::createStatusBar
 [00:03:05:358] DefaultGui::createActions
 [00:03:05:358] DefaultGui::createControlWidget
 [00:03:05:362] DefaultGui::createControlWidgetMini
 [00:03:05:363] TimeSlider::setDragDelay: 100
 [00:03:05:372] BaseGui::initializeMenus
 [00:03:05:372] BaseGui::updateRecents
 [00:03:05:372] DefaultGui::updateWidgets
 [00:03:05:372] BaseGui::updateWidgets
 [00:03:05:373] DefaultGui::loadConfig
 [00:03:05:373] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1366 h:768
 [00:03:05:373] Helper::qtVersion: 4801
 [00:03:05:373] DefaultGui::loadConfig: playlist visible: 0
 [00:03:05:373] DefaultGui::loadConfig: playlist position: 0, 0
 [00:03:05:373] DefaultGui::loadConfig: playlist size: 210 x 120
 [00:03:05:373] DefaultGui::updateWidgets
 [00:03:05:373] BaseGui::updateWidgets
 [00:03:05:374] Skins::file: main.css
 [00:03:05:396] Core::setVolume: 50
 [00:03:05:452] BaseGui::showEvent
 [00:03:05:452] main: remove_lock: /home/dylan/.config/umplayer/umplayer_init.lock
 [00:03:05:473] BaseGui::loadActions
 [00:03:05:473] ActionsEditor::loadFromConfig
 [00:03:05:580] BaseGui::initializeMenus
 [00:03:05:581] BaseGui::updateRecents
 [00:03:05:582] DefaultGui::updateWidgets
 [00:03:05:582] BaseGui::updateWidgets
 [00:03:05:638] WARNING: content-type missing in HTTP POST, defaulting to application/octet-stream
 [00:03:09:626] BaseGui::showLog

```

---

