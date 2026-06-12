---
title: "Gnome-Do Error"
date: 2009-07-12
forum: General Help
---

### Post by Jor_727 on 2009-07-12
Hello everyone!
I recently installed Gnome-Do v0.8.2 in the hopes that it would be a better dock, although I'm getting this error.

```

jord@Lolcano:~$ gnome-do

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Do.Platform.Services.Initialize () [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000]

```

Unfortunately I cannot find a proper fix for it, and if anybody could give me some advice I would be extremely grateful.  Thanks!

---

### Post by Jor_727 on 2009-07-13
Bump

---

### Post by Jor_727 on 2009-07-14
...Bump

---

### Post by kogger on 2009-07-14
Try re-installing it? I don't use gnome do, so I'm not sure what would cause that problem.

---

### Post by Jor_727 on 2009-07-14
I've tried re-installing it several times only to get the same bloody error.  Thanks for the reply though.

---

### Post by 3rdalbum on 2009-07-14
No idea, but Gnome-Do is not a dock.

IIRC, Gnome-Do is available from [www.getdeb.net](www.getdeb.net) as a Debian/Ubuntu package.

---

### Post by Jor_727 on 2009-07-15
Unfortunately I don't think it will be availble packages for Karmic Beta.  On the other hand, there is a Karmic PPA key that they allow on the site ([https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)).  That's how I originally installed the program.

---

### Post by scaine on 2009-07-16
Got a similar error (see attached - lots of info).  It seems to happen during a regular background task, which causes a system exception, many times over, before finally failing with the "unhandled exception".

I think I'll end up logging a bug, but I'm going to try clearing my settings first - I think you can delete ~/.gconf/apps/gnome-do and then restart gnome-do for a "clean" refresh.

[EDIT : It would seem that the correct path is ~/.local/share/gnome-do, and it also seems that certain settings are stored in the gconf-editor, since deleting both of those directories and then restarting gnome-do still remembered certain things, such as my gnome-do key, which I changed from super+space, and also my zoom and icon sizes]

Also interested if you're running 0.8.2 from the gnome-do core ppa, or whether it's still 0.8.1 from the official ubuntu repos.

Anyway, will try to post back once I've tried the delete option.

---

### Post by scaine on 2009-07-16
Quick update before I get some shut-eye.  It's been 40 minutes since deleting my config (both directories I mentioned in my previous post).  No crashes, but I did have to go through the hassle of telling Gnome-Do what apps I like to use again (hotkey gnome-do into existence, type a couple of letters of the app I want, then hit the + sign next to its icon).  That took about 5 minutes.

I also had to tick the extensions I like using - another minute.

I'm about to add one I think may have been related to the crash - the twitter post extension.  Actually, I don't have any evidence it's related to the crashes, but it's the only extension I use that requires me to provide login details.  Fingers crossed and I hope the "delete your config" route helps you out.

---

### Post by Jor_727 on 2009-07-16
I've tried deleting those files that scaine mentioned, although only to this this error:

```

jord@Lolcano:~$ sudo rm -rf  ~/.gconf/apps/gnome-do
[sudo] password for jord: 
jord@Lolcano:~$ sudo rm -rf ~/.local/share/gnome-do
jord@Lolcano:~$ gnome-do
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.AnimationBase.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.Classic.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.Docky.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.GlassFrame.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.HUD.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.Mini.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Linux.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Interface.Wink.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Platform.Linux.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Platform.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.Universe.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/Do.exe
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Alias.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Banshee.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/BatteryMonitor.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Bibtex.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/CPUMonitorDocklet.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Confluence.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Dropbox.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/EOG-Slideshow.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Emesene.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: evolution-sharp, Version=5.0.0.0, Culture=neutral, PublicKeyToken=c46a23b774189844
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Evolution.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Exaile.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/File.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Firefox.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Flickr.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/GNOME-Session.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/GoogleCalendar.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: Google.GData.Contacts, Version=1.4.0.2, Culture=neutral, PublicKeyToken=7e065189dd4b982f
Assembly not found: Google.GData.Extensions, Version=1.4.0.2, Culture=neutral, PublicKeyToken=0b4c5df2ebf20876
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/GoogleContacts.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/GoogleDocs.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/GoogleSearch.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/ImageShack.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/JIRA.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Microblog.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Pastebin.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Pidgin.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/PingFM.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/RSS.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/RTM.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/RemindMe.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/RequestTracker.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Rhythmbox.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Skype.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/SqueezeCenter.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/SwitcherDocklet.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/SystemServices.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Tasque.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Tomboy.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/TrackerSearch.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Translate.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/VolumeDocklet.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/WeatherDocklet.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: wnck-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/WindowManager.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/Woof.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: Google.GData.YouTube, Version=1.4.0.2, Culture=neutral, PublicKeyToken=af04a32718ae8833
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/YouTube.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: Could not scan file: /usr/lib/gnome-do/plugins/del.icio.us.dll
Assembly not found: Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Assembly not found: gnome-vfs-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gconf-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: The add-in 'Do.Riptide,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.VolumeControl,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.VirtualBox,1.3' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.VirtualBox,1.3' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Zim,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Zim,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Thunderbird,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GNOMEScreenshot,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GNOMEScreenshot,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.NX,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.NX,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.OpenSearch,1.2' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Epiphany,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Opera,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.LocateFiles,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.VinagreVNC,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.VinagreVNC,1.1' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.xmms2,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.xmms2,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.ManPages,1.2' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.ClawsMail,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Archive,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Cl.ickable,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Cl.ickable,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.SSH,1.1' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.SSH,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GNOMETerminal,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GNOMETerminal,1.1' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Putty,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Putty,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Launchpad,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.StockQuote,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.MPD,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GoogleCalculator,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GNOMEDictionary,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.GoogleMaps,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Shelf,1.2' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Shelf,1.2' is trying to extend '/Do/Action', but there iWARNING: The add-in 'Do.Wordnet,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.AptURL,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.TerminalServerClient,1.1' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Text,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.DiskMounter,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.DiskMounter,1.0' is trying to extend '/Do/ItemSource', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.Quote,1.1' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point
WARNING: The add-in 'Do.TinyUrl,1.0' is trying to extend '/Do/Action', but there isn't any add-in defining this extension point

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Do.Platform.Services.Initialize () [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

```

At the end you can notice the same error I had originally.  Right after finishing this I tried restarting Gnome-Do again, but I got this:

```

jord@Lolcano:~$ gnome-do

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Do.Platform.Services.Initialize () [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

```

The very same as the original error.  Unfortunately, it seems that I still need help.

---

### Post by scaine on 2009-07-17
Do you definitely have gnome-do-plugins installed?  And are you using the PPA version?

Seems you might want to remove those files completely (again), then do a "completely remove" of everything gnome-do in synaptic and then re-install it again.

Worth a try anyway.

---

### Post by Jor_727 on 2009-07-21
I completely removed it like you said through Synaptic.  Here's me installing it afterwards:

```

jord@Lolcano:~$ sudo aptitude install gnome-do
[sudo] password for jord: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  gnome-do gnome-do-docklets{a} gnome-do-plugins{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 4004kB of archives. After unpacking 8147kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://ppa.launchpad.net karmic/main gnome-do 0.8.2+dfsg-0~9.10~ppa1 [494kB]
Get:2 http://ppa.launchpad.net karmic/main gnome-do-docklets 0.8.2-0~9.10~ppa1 [47.1kB]
Get:3 http://ppa.launchpad.net karmic/main gnome-do-plugins 0.8.2+dfsg-0~9.10~ppa2 [3463kB]
Fetched 4004kB in 12s (318kB/s)                                                 
Selecting previously deselected package gnome-do.
(Reading database ... 388619 files and directories currently installed.)
Unpacking gnome-do (from .../gnome-do_0.8.2+dfsg-0~9.10~ppa1_i386.deb) ...
Selecting previously deselected package gnome-do-docklets.
Unpacking gnome-do-docklets (from .../gnome-do-docklets_0.8.2-0~9.10~ppa1_all.deb) ...
Selecting previously deselected package gnome-do-plugins.
Unpacking gnome-do-plugins (from .../gnome-do-plugins_0.8.2+dfsg-0~9.10~ppa2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up gnome-do (0.8.2+dfsg-0~9.10~ppa1) ...

Setting up gnome-do-docklets (0.8.2-0~9.10~ppa1) ...
Setting up gnome-do-plugins (0.8.2+dfsg-0~9.10~ppa2) ...
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

jord@Lolcano:~$ gnome-do

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Do.Platform.Services.Initialize () [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

```

---

### Post by fouserge on 2009-07-26
I got this error after I installed mono and logged out.


- EDIT

Alright if you got this error same way I did:
Gnome-do working -> install MonoDevelop -> Reboot -> Gnome-do AND MonoDevelop broken.

I fixed it by installing mono-gmcs and now both work.

---

### Post by scaine on 2009-07-26
Might also be worth trying just "completely removing" Gnome-Do from Synaptic, then remove the PPA for Gnome-Do, then reload and re-install the stock Gnome-Do from Karmic (0.8.1, I think).

@fouserge, I'm not sure what you mean by "installing mono", since it's installed by default in Ubuntu.  Is it the developer environment you're talking about?

---

### Post by fouserge on 2009-07-26
I meant MonoDevelop

---

### Post by Jor_727 on 2009-07-29
```

jord@Lolcano:~$ sudo apt-get install mono-gmcs
[sudo] password for jord: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mono-gmcs is already the newest version.
mono-gmcs set to manually installed.

```

Unfortunately, that fix didn't work either.  I'll try the complete removal next; I'll post when I'm done.

---

