---
title: "Confused about deja-dup / Ubunto One in 11.10"
date: 2011-10-17
forum: General Help
---

### Post by manlymatt83 on 2011-10-17
Hi folks,

I'm loving 11.10 so far, but I'm a bit confused about deja-dup.

I went into Settings and chose "backup", which launched deja-dup.  I turned on automated backups and closed the window.  Initially, things were set to Ubuntu One.  I later went in and changed that to "Local Folder", and pointed it to the mount point of the external drive.  For some reason, the external drive wasn't listed  as an option (which I thought was weird) even though it was mounted.  After the backup ran, the local folder option had automatically changed to FTP, with the folder being the full path of the folder on the external drive, but no server/port info filled in.  I found this behavior weird.  So here are my three questions:

1) Why was my external drive (mounted at /media/external automatically by Ubuntu when I plug it in) not listed as an option?

2) How come when I chose Local Folder, and put in /media/external/backups, did the software automatically switch it to FTP (leaving server and port blank, but still).

3) When the default was Ubuntu One, and I had turned on automatic backups, did deja-dup actually do anything?  I don't even have an Ubuntu One account, so I'm confused as to why it even let me choose Ubuntu One in the first place.  Would it have asked me to login after attempting the initial backup or something, or did my files get sent to a random Ubuntu One account? :P

Thanks for any answers!

---

### Post by lovinglinux on 2011-10-17
3 - I have an Ubuntu One account and when you create the backup it uploads automatically. In your case, I suppose it should prompt for your credentials before uploading.

I just removed Ubuntu One client and the option is no longer available in Déjà Dup.

---

