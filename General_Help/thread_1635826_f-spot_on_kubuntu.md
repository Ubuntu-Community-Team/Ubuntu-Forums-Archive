---
title: "f-spot on kubuntu"
date: 2010-12-02
forum: General Help
---

### Post by RastaManPower on 2010-12-02
i tryed installing f-spot from KpackageKit and i am getting this error. what does it mean?

An unhandled exception was thrown: Object reference not set to an instance of an object

  at FSpot.Widgets.PhotoImageView.LoadErrorImage (System.Exception e) [0x00000] in <filename unknown>:0 
  at FSpot.Widgets.PhotoImageView.HandlePhotoItemChanged (System.Object sender, FSpot.Core.BrowsablePointerChangedEventArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) System.EventHandler`1<FSpot.Core.BrowsablePointerChangedEventArgs>:invoke_void__this___object_BrowsablePointerChangedEventArgs (object,FSpot.Core.BrowsablePointerChangedEventArgs)
  at FSpot.Core.BrowsablePointer.SetIndex (Int32 value, IBrowsableItemChanges changes) [0x00000] in <filename unknown>:0 
  at FSpot.Core.BrowsablePointer.HandleCollectionChanged (IBrowsableCollection collection) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) FSpot.Core.IBrowsableCollectionChangedHandler:invoke_void__this___IBrowsableCollection (FSpot.Core.IBrowsableCollection)
  at (wrapper delegate-invoke) FSpot.Core.IBrowsableCollectionChangedHandler:invoke_void__this___IBrowsableCollection (FSpot.Core.IBrowsableCollection)
  at FSpot.PhotoQuery.RequestReload () [0x00000] in <filename unknown>:0 
  at FSpot.QueryWidget.Close () [0x00000] in <filename unknown>:0 
  at FSpot.MainWindow.UpdateFindByTagMenu () [0x00000] in <filename unknown>:0 
  at FSpot.MainWindow..ctor (FSpot.Database.Db db) [0x00000] in <filename unknown>:0 
  at FSpot.App.get_Organizer () [0x00000] in <filename unknown>:0 
  at FSpot.App.HandleOrganize () [0x00000] in <filename unknown>:0 
  at FSpot.App.Organize () [0x00000] in <filename unknown>:0 
  at FSpot.Driver.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.35.23

Assembly Version Information:

FSpot.Exporters.Folder (0.8.0.0)
FSpot.Tools.RetroactiveRoll (0.8.0.0)
FSpot.Tools.ScreensaverConfig (0.8.0.0)
FSpot.Exporters.PicasaWeb (0.8.0.0)
FSpot.Exporters.Gallery (0.8.0.0)
FSpot.Exporters.Flickr (0.8.0.0)
FSpot.Exporters.CD (0.8.0.0)
FSpot.Exporters.SmugMug (0.8.0.0)
Mono.Cairo (2.0.0.0)
FSpot.Bling (0.8.0.0)
TagLib (0.8.0.0)
pango-sharp (2.12.0.0)
FSpot.Query (0.8.0.0)
gtk-sharp-beans (2.14.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (0.8.0.0)
Hyena.Data.Sqlite (0.8.0.0)
FSpot.JobScheduler (0.8.0.0)
System.Core (3.5.0.0)
unique-sharp (1.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Gui (0.8.0.0)
System.Xml (2.0.0.0)
Mono.Addins (0.4.0.0)
Mono.Addins.Setup (0.4.0.0)
gconf-sharp (2.24.0.0)
Hyena.Gui (0.8.0.0)
atk-sharp (2.12.0.0)
System (2.0.0.0)
gtk-sharp (2.12.0.0)
FSpot.Cms (0.8.0.0)
FSpot.Core (0.8.0.0)
FSpot.Platform (0.8.0.0)
Mono.Posix (2.0.0.0)
gdk-sharp (2.12.0.0)
Hyena (0.8.0.0)
glib-sharp (2.12.0.0)
FSpot.Utils (0.8.0.0)
f-spot (0.8.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.35-23-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

[/etc/debian_version]
squeeze/sid

---

