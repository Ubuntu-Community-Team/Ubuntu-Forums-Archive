---
title: "F-Spot makes trouble"
date: 2009-10-30
forum: General Help
---

### Post by yester64 on 2009-10-30
Hi, i recently installed a new internal harddrive and moved my photos onto the drive.
After that i installe F-Spot and started importing, but it failed. First i thought it is the permission and yes it was. So i changed the permission on the folder and files, but still it fails to import.
What can it be what i do not see?

I attached an image of the error i am getting.

This is for sure a silly cause that i fail to see.

---

### Post by lavinog on 2009-10-30
sometimes running programs in a terminal might give you better messages.

---

### Post by yester64 on 2009-10-30
I've got this

System.IO.FileNotFoundException: Could not find uri "file:///media/Pictures&Movies/Music/iTunes/iTunes Media/Music/Boston/Third Stage/cover.jpg".
  at Gnome.Vfs.VfsStream..ctor (System.String text_uri, FileMode mode, Boolean async) [0x00000] 
  at Gnome.Vfs.VfsStream..ctor (System.String uri, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) Gnome.Vfs.VfsStream:.ctor (string,System.IO.FileMode)
  at FSpot.ImageFile.Open () [0x00000] 
  at FSpot.ImageFile.PixbufStream () [0x00000] 
  at FSpot.ImageFile.Load (Int32 max_width, Int32 max_height) [0x00000] 
  at PixbufLoader.ProcessRequest (.RequestItem request) [0x00000] 
  at FSpot.ThumbnailGenerator.ProcessRequest (.RequestItem request) [0x00000] 

it almost looks like that it is looking for previous locations.
Where does fspot store ini files? Because i remember that i uninstalled it but i don't think that i deleted the old config etc.. files.

---

