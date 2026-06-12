---
title: "Arista won't start"
date: 2011-08-18
forum: General Help
---

### Post by Zanven on 2011-08-18
I click Arista and it shows the thinking  cursor for a half of a second then nothing happens. Terminal reads as  follows:
> ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Traceback (most recent call last):
  File "/usr/bin/arista-gtk", line 1685, in <module>
    main = MainWindow(options)
  File "/usr/bin/arista-gtk", line 398, in __init__
    self.setup_devices()
  File "/usr/bin/arista-gtk", line 624, in setup_devices
    image = _get_icon_pixbuf(device.icon, width, height)
  File "/usr/bin/arista-gtk", line 122, in _get_icon_pixbuf
    image = gtk.gdk.pixbuf_new_from_file_at_size(path, width, height)
glib.GError: Unrecognized image file format

Edit:So I think the problem stems from me improperly installing a preset. I have tried completely removing and reinstalling Arista. I even deleted the contents of the presets folder but when I use "arista-transcode -i" it still has that bad preset. 
I've since deleted the preset I downloaded and have no idea where it is still finding it

---

### Post by Zanven on 2011-08-18
I posted this all at once but I've been at it for a few days. I thought of something right when I posted that last edit. When removing Arista using the package manager it didn't delete the user files in the home directory/.arista . I'm an idiot #-o

---

