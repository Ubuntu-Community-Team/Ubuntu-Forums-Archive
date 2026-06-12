---
title: "Fspot encounter fatal error"
date: 2010-04-03
forum: General Help
---

### Post by Spleah on 2010-04-03
I'm new to Ubuntu and altogether a complete moron when it comes to computers.  I can't download pictures from my camera in F-Spot.  Please help!!!  ;) Here's the error I get.

An unhandled exception was thrown: Object reference not set to an instance of an object

  at FileImportBackend.Prepare () [0x00000] 
  at ImportCommand.DoImport (.ImportBackend imp) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags, Boolean copy) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags) [0x00000] 
  at FSpot.CameraFileSelectionDialog.ImportFiles () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at FSpot.Core+ImportCommand.Execute () [0x00000] 
  at FSpot.Core.Import (System.String path) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

gio-sharp (2.14.0.0)
SemWeb (0.7.1.0)
libgphoto2-sharp (1.0.3597.18580)
ScreensaverConfig (0.0.0.0)
CDExport (0.0.0.0)
FlickrExport (0.0.0.0)
GalleryExport (0.0.0.0)
FolderExport (0.0.0.0)
HashJob (0.0.0.0)
PicasaWebExport (0.0.0.0)
SmugMugExport (0.0.0.0)
glade-sharp (2.12.0.0)
System.Core (3.5.0.0)
FSpot.Bling (0.0.0.0)
pango-sharp (2.12.0.0)
gtk-sharp-beans (2.14.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Widgets (0.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.5)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-20-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

