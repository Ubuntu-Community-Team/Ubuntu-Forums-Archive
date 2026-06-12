---
title: "nautilus crashes when browsing Places/Computer"
date: 2009-10-24
forum: General Help
---

### Post by dj-toonz on 2009-10-24
Hi all, Having problems trying to view Places/Computer, Nautilus just shuts down :-(. If I open a terminal prompt up and type in Nautilus, this is the error log that I'm getting 

toonz@toonz-laptop:~$ nautilus
Initializing nautilus-clamscan extension
Initializing nautilus-dropbox 0.6.1
Initializing nautilus-image-converter extension
** Message: Initializing gksu extension...
Initializing nautilus-open-terminal extension

** (nautilus:7340): WARNING **: Unable to add monitor: Not supported

(nautilus:7340): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:7340): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken.

sys:1: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
toonz@toonz-laptop:~$

all the post's I've read, have said it's to do with ubuntuone but I don't have the Ubuntuone installed :-( 

The only last thing I can think of what I installed was the daily ppa for network-manager. so if it is that, how can I totally un-install it & revert back to the version in the main repos cheers

---

### Post by dj-toonz on 2009-10-24
Update, removed everything I can think of & still crashing :-(, I can't even access the network or the desktop machine :-( so looks like I'll have to do a re-install or go to XP as it seems like this bug is not even being fixed as there's loads of posts about it from differnt people but no proper answers :-( 

as anybody got any ideas to how to fix it ? cheers

---

