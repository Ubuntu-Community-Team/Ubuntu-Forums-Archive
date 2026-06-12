---
title: "gtkpod help - missing files"
date: 2012-02-12
forum: General Help
---

### Post by tim_norman2003 on 2012-02-12
hi
im trying to set up my iphone 3gs (ios 5.0.1) with my music.

using gtkpod it shows all the songs and movies i have added to the phone (using my friends itunes) but the files dont show up on my phone.

can you please tell me how to remidy this problem, so i can listen to more than  1/4 of my music .

(on a side note when i try and put more tracks on my iphone it says it cant be done because of missing hashinfo files..)

any ideas?

thanks
Tim

---

### Post by tim_norman2003 on 2012-02-12
this is the terminal output when i try to sync:


gtktim@tim-desktop:~$ gtkpod

(gtkpod:3430): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem
libitdbprep: itdb_iphone_start_sync called with uuid=26d96e4ed8e4796790891c8a7e2b26b6fe00c630
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (gtkpod:3430): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
Could not delete 'ddd.itdbm'
itdb_iphone_stop_sync: posted syncDidFinish
libitdbprep: itdb_iphone_start_sync called with uuid=26d96e4ed8e4796790891c8a7e2b26b6fe00c630
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (gtkpod:3430): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
Could not delete 'ddd.itdbm'
itdb_iphone_stop_sync: posted syncDidFinish

---

### Post by Huss on 2012-03-18
Hi Tim

I'm having a similar problem - GTK or banshee wont sync. One way I found to get around this is using 'FileApp' and copying my music, pics, ebooks and documents to the app. 

This is a temporary solution as there are some limitations, but here goes:
- Install Fileapp from the app store (Free)
- Connect your phone via usb
- Go to the 'Documents' partition that should mount when plugged in. 
- Double click on the 'FileApp' icon, then open the 'Documents' subfolder 
- Copy the files you want to this folder. It's a good idea to make the whole directory structure and then copy across as it doesn't seem to let you move or rename items.

Limitations:
- Can't easily change directory structure
- No playlists in built in music player. Might be able to use the 'open in' function to do this with another app
- Probably others, I haven't played with it much yet. 

This is very much a temporary solution, but is the best one I've found until gtkpod is working again. 

Cheers

Huss
(Ubuntu 11.4, iphone 3gs - ios 5.1)

---

