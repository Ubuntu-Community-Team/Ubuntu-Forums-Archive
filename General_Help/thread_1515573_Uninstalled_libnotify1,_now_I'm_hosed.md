---
title: "Uninstalled libnotify1, now I'm hosed"
date: 2010-06-22
forum: General Help
---

### Post by busta_bird on 2010-06-22
I uninstalled libnotify1 because I "thought" that was the package with those annoying popups in it. After I uninstalled, I shut the laptop down (Thinkpad T400). Now I can attempt to login and it kicks me back to the login screen. I booted into a terminal and installed libnotify1, but it didn't install nearly a quarter of the packages as the uninstall did. What do I do from here?

10.04 32bit

---

### Post by Admiral Yi on 2010-06-22
All the packages that depend on libnotify1 have been removed, so you would need to find out what they were and reinstall them. I'm no expert, but I don't think there's an easy way to do that, so maybe reinstall? If you have a separate home partition you'll keep all your settings. Even if you don't, there are ways to set one up so you can keep your data.

Also, what popups? I've never had any popups using linux, and any you do get can be blocked via firefox addons.

---

### Post by busta_bird on 2010-06-22
I'm there with you. I believe that is the cause, but I can't find the information anywhere. Perhaps if someone were to at least load the dependency screen on the removal and screenshot it for me, that'd be great. You wouldn't have to uninstall it to get that far.

---

### Post by Admiral Yi on 2010-06-22
That I can do for you ;):

```
The following packages will be REMOVED
  autofsck empathy evolution evolution-couchdb evolution-exchange evolution-indicator evolution-plugins gnome-applets gnome-bluetooth gnome-control-center
  gnome-disk-utility gnome-panel gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-user-share gwibber gwibber-service
  indicator-applet indicator-applet-session indicator-me jockey-gtk libnotify1 libubuntuone-1.0-1 metacity nautilus-sendto-empathy network-manager-gnome
  python-notify python-ubuntuone python-ubuntuone-client rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store seahorse
  seahorse-plugins system-config-printer-gnome transmission-gtk ubuntu-desktop ubuntuone-client ubuntuone-client-gnome update-notifier vino zenity
0 upgraded, 0 newly installed, 45 to remove and 98 not upgraded.
```

Remember, some of them might be ones you didn't have before, and I may not have some that you did. However, all the vital stuff should be there.

---

### Post by mc4man on 2010-06-22
> doug@doug-laptop:~$ apt-cache rdepends libnotify1
libnotify1
Reverse Depends:
  vlc
  libexo-0.3-0
  epiphany-browser
  deja-dup
  transmission-gtk
  rhythmbox-plugins
  rhythmbox
  netbook-launcher
  nautilus-sendto-empathy
  gnome-settings-daemon
  gnome-screensaver
  evolution-plugins
  evolution
  empathy
  vlc
  ogmrip
  gnome-mplayer
  xulrunner-1.9.2-gnome-support
  xneur
  xfce4-volumed
  xfce4-smartpm-plugin
  xfce4-settings
  xfce4-power-manager
 |xchat
  vlc
  vagalume
  uget
  twitux
  tracker-search-tool
  syncmaildir-applet
  synce-trayicon
  setroubleshoot
  sensors-applet
  salasaga
  padevchooser
  packagekit-gnome
  osmo
  orage
  muine-plugin-trayicon
  minbar
  midori
  mail-notification
  lxmusic
  libnotifymm-1.0-7
  libnotify-bin
  libjava-gnome-jni
  libgtk2-notify-perl
  libexo-0.3-0
  krb5-auth-dialog
  kerneloops-applet
  ircp-tray
  ipwatchd-gnotify
  hornsey
  gwget
  gshutdown
  goobox
  gnunet-gtk
  gnomebaker
  gnome-gmail-notifier
  gnome-color-manager
  gnoemoe
  gir1.0-notify-0.4
  epiphany-browser
  ekiga
  deja-dup
  dalston
  collectd-core
  collectd
  claws-mail-multi-notifier
  bognor-regis
  balsa
  awn-applets-c-core
  artha
  ario
  alarm-clock-applet
  alarm-clock
  zenity
  xchat-gnome
  vino
  update-notifier
  transmission-gtk
  seahorse-plugins
  seahorse
  rhythmbox-plugins
  rhythmbox
  python-notify
  pidgin-libnotify
  notification-daemon
  network-manager-gnome
  netbook-launcher-efl
  netbook-launcher
  nautilus-sendto-empathy
  liferea
  libnotify-dev
  gnome-user-share
  gnome-settings-daemon
  gnome-screensaver
  gnome-power-manager
  gnome-disk-utility
  gnome-bluetooth
  gnome-applets
  evolution-plugins
  evolution-indicator
  evolution
  empathy

some of these may be install specific (mine that is

---

### Post by realzippy on 2010-06-22
Ok,simulate libnotify1 uninstall for you.It kicks also:

ubuntu-desktop		
gnome-power-manager		
python-notify		
metacity		
update-notifier		
python-ubuntuone-client		
system-config-printer-gnome		
gnome-applets		
ubuntuone-client		
network-manager-gnome		
zenity	
indicator-me		
gnome-disk-utility		
gnome-settings-daemon		
rhythmbox		
gnome-session		
transmission-gtk		
seahorse			
indicator-applet		
libnotify1		
indicator-applet-session		
libubuntuone-1.0-1		
vino		
rhythmbox-ubuntuone-music-store		
libnotify-dev		
gwibber-service			
gnome-screensaver		
jockey-gtk		
xulrunner-1.9.2-dev		
gnome-control-center		
ubuntuone-client-gnome		
gnome-panel		
gwibber		
rhythmbox-plugins		
xulrunner-dev		
python-ubuntuone

No good idea,but when you install these packages again,all will be fine.
(**sudo apt-get install *package1* *package2*** aso.)

---

### Post by busta_bird on 2010-06-22
Ah, hello Gnome. You guys are the bee's knees. Thanks for all of the quick responses.

---

