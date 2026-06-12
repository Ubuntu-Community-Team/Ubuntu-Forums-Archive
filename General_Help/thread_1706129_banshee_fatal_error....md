---
title: "banshee fatal error..."
date: 2011-03-13
forum: General Help
---

### Post by xen_ on 2011-03-13
hey everyone...
m new to ubuntu and to this forum also...
i installed banshee on my ubuntu 10.10, and then tried installing the lyrics plugin for it...
Now its like, everytime i try to play a song through banshee i get this fatal error... the song keeps playing in the background, but the banshee window hangs completely... And then i'll have to Force Quit it..
I tried uninstalling banshee through sudo apt-remove banshee command and also deleted the linked directories(found using the whereis cmd)...
Next i tried installing banshee again, but the same problem still persists...

The Error description is something like this mentioned below...

An unhandled exception was thrown: Object reference not set to an instance of an object

at Banshee.Plugins.Lyrics.LyricsPlugin.OnPlayerEngineEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x00060>
at (wrapper delegate-invoke) Banshee.MediaEngine.PlayerEventHandler.invoke_void__this___PlayerEventArgs (Banshee.MediaEngine.PlayerEventArgs) <0x0003d>
at (wrapper delegate-invoke) Banshee.MediaEngine.PlayerEventHandler.invoke_void__this___PlayerEventArgs (Banshee.MediaEngine.PlayerEventArgs) <0x00067>
at Banshee.MediaEngine.PlayerEngine.RaiseEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x0001f>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x000cb>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEvent) <0x0002d>
at Banshee.GStreamer.PlayerEngine.OnNextTrackStarting (intptr) <0x0004f>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnNextTrackStarting (intptr) <0x00054>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x0000a>
at Banshee.Gui.GtkBaseClient.Run () <0x00054>
at Banshee.Gui.GtkBaseClient.Startup () <0x0003f>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x00089>


.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.35.27

Assembly Version Information:

taglib-sharp (2.0.3.7)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Zeroconf.Providers.AvahiDBus (4.0.0.90)
Mono.Zeroconf (4.0.0.90)
Mtp (1.8.0.0)
Banshee.Dap.Mtp (1.8.0.0)
karma-sharp (0.0.0.0)
Banshee.Dap.Karma (1.8.0.0)
libgpod-sharp (1.0.3937.13502)
Banshee.Dap.AppleDevice (1.8.0.0)
Banshee.Dap.MassStorage (1.8.0.0)
Banshee.Audiobook (1.8.0.0)
Banshee.InternetArchive (1.8.0.0)
Banshee.MiroGuide (1.8.0.0)
Banshee.AmazonMp3.Store (1.8.0.0)
Banshee.FileSystemQueue (1.8.0.0)
Banshee.InternetRadio (1.8.0.0)
Banshee.PlayQueue (1.8.0.0)
gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (1.8.0.0)
Banshee.CoverArt (1.8.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.8.0.0)
Banshee.AmazonMp3 (1.8.0.0)
Banshee.Lyrics (0.0.0.0)
Banshee.Daap (1.8.0.0)
Banshee.LastfmStreaming (1.8.0.0)
Lastfm (1.8.0.0)
Banshee.Dap (1.8.0.0)
Migo (1.8.0.0)
Banshee.Podcasting (1.8.0.0)
Banshee.LibraryWatcher (1.8.0.0)
Banshee.MultimediaKeys (1.8.0.0)
Banshee.Bpm (1.8.0.0)
Banshee.WebBrowser (1.8.0.0)
Banshee.Wikipedia (1.8.0.0)
Banshee.Lastfm (1.8.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (1.8.0.0)
Banshee.Widgets (1.8.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (1.8.0.0)
Banshee.GStreamer (1.8.0.0)
Mono.Media (1.8.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.8.0.0)
Banshee.NowPlaying (1.8.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.8.0.0)
System.Xml (2.0.0.0)
Banshee.Core (1.8.0.0)
Hyena.Data.Sqlite (1.8.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.8.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.8.0.0)
Nereid (1.8.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Hyena (1.8.0.0)
System (2.0.0.0)
Banshee.Services (1.8.0.0)
Banshee (1.8.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.35-27-generic-pae i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

[/etc/debian_version]
squeeze/sid

---

### Post by cap10Ibraim on 2011-03-13
is the plugin from 
banshee-community-extensions ?

---

### Post by xen_ on 2011-03-13
err i actually dont remember from where i downloaded it... just googled it and went for the one tat came up first...

the install.sh file contains the following..
#!/bin/sh
PLUGINDIR=`pkg-config --variable=bansheedir banshee-1-core`
echo "installing to $PLUGINDIR"
sudo cp Banshee.Lyrics.dll $PLUGINDIR
echo "done"

i guess removing this plugin should be the solution...
any ideas abt hw i do it.??
thnxx in advance... :)

---

### Post by xen_ on 2011-03-13
aha... i got it working finally...
here is wat u need to do if u ever come across such a situation...

#!/bin/bash
PLUGINDIR=`pkg-config --variable=bansheedir banshee-1-core`
sudo rm $PLUGINDIR/Banshee.Lyrics.dll
echo "Removed from $PLUGINDIR/Banshee.Lyrics.dll"

copy and paste the above lines in an empty file and rename it to test.sh
and then bash test.sh from the terminal.. :)

---

### Post by directhex on 2011-03-13
Um... the lyrics plugin is in the distro. Why break your system with weirdo installs?

---

