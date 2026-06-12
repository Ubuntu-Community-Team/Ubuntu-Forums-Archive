---
title: "F-Spot crashes on import at same file everytime"
date: 2010-07-23
forum: General Help
---

### Post by winchendonsprings on 2010-07-23
When I try to import my Pictures folder F-Spot crashes at photo # 668 every time. After restart and logout/login. 

Is there a way I can get an error log? 

When I start f-spot in terminal and try to import pictures I get this -

[INDENT]ry@ry-desktop:~$ f-spot
[Info  20:32:31.343] Initializing Mono.Addins

(f-spot:22247): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

** (f-spot:22247): WARNING **: Invalid borders specified for theme pixmap:
        /home/ry/.themes/Victory Elementary/gtk-2.0/Images/null.png,
borders don't fit within the image

Unhandled Exception: TagLib.UnsupportedFormatException: file:///home/ry/Pictures/misc%20photos/BRI.bmp (image/bmp)
  at TagLib.File.Create (IFileAbstraction abstraction, System.String mimetype, ReadStyle propertiesStyle) [0x00000] 
  at FSpot.Utils.Metadata.Parse (Hyena.SafeUri uri) [0x00000] 
  at FSpot.FileBrowsableItem.EnsureMetadataParsed () [0x00000] 
  at FSpot.FileBrowsableItem.get_Time () [0x00000] 
  at PhotoStore.CreateFrom (IBrowsableItem item, UInt32 roll_id) [0x00000] 
  at FSpot.Import.ImportController.ImportPhoto (IBrowsableItem item, FSpot.Roll roll) [0x00000] 
  at FSpot.Import.ImportController.DoImport () [0x00000] 
[/INDENT]
I know there is an error from .bmp files but the problem still persists after I remove them.

Any ideas would be great

---

### Post by nemilar on 2010-07-23
The man page indicates that f-spot can take a --debug flag.

Additionally, you may want to look at [https://bugs.launchpad.net/ubuntu/+source/f-spot](https://bugs.launchpad.net/ubuntu/+source/f-spot) and see if this issue has been reported.  If not, you can file a bug report.

---

