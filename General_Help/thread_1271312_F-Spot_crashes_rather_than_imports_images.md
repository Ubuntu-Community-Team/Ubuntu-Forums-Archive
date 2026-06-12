---
title: "F-Spot crashes rather than imports images"
date: 2009-09-20
forum: General Help
---

### Post by AngusM on 2009-09-20
I'm trying to import images from my camera into F-Spot, but as soon as I try, with the first file, I get:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129216&d=1253482223[/IMG]
So I cancel, and when I do, I get "Object reference not set to an instance of and object, followed by:
```
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
.NET Version: 2.0.50727.42

Assembly Version Information:

libgphoto2-sharp (1.0.3385.23088)
SmugMugExport (0.0.0.0)
CDExport (0.0.0.0)
FlickrExport (0.0.0.0)
GalleryExport (0.0.0.0)
FolderExport (0.0.0.0)
HashJob (0.0.0.0)
PicasaWebExport (0.0.0.0)
pango-sharp (2.12.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.12.0.0)
FSpot.JobScheduler (0.0.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Widgets (0.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
gdk-sharp (2.12.0.0)
gnome-vfs-sharp (2.24.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
Cms (0.0.0.0)
Mono.Posix (2.0.0.0)
System (2.0.0.0)
FSpot.Utils (0.0.0.0)
FSpot.Core (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
gnome-sharp (2.24.0.0)
f-spot (0.5.0.3)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-21-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
5.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"


```

This happens whether or not I have "Detect duplicates" checked, and there aren't any duplicates file names anyway. I tried following the process that [this guy]("http://ubuntuforums.org/showthread.php?t=1159830") did, but that didn't work.

If the solution involves going with another import software, that's fine. I don't think gThumb Photo Import Tool would be one, though, since I hear it's worse.

---

### Post by directhex on 2009-09-20
Looks like this bug here? [https://bugzilla.gnome.org/show_bug.cgi?id=539822](https://bugzilla.gnome.org/show_bug.cgi?id=539822)

Providing your screenshot and stack trace would help the F-Spot developers out

---

