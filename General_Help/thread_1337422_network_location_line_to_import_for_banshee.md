---
title: "network location line to import for banshee"
date: 2009-11-25
forum: General Help
---

### Post by sdowney717 on 2009-11-25
I have shared folders on one pc containing videos.
I want to import this location into banshee
the import dialog allows a typed line

what would be the link to type for a shared folder on the network?

well, I solved it following this post. Mount a smb share in nautilus.

goto network
find the shared network folder
right click and select 'mount' it will then appear in the left side panel

the share then shows in a hidden folder called .gvfs
when importing the media in banshee point it to this hidden folder

> I've been successfully using gio/gvfs since Gnome 2.22. I'm not sure if there
are bindings good enough for C# to support gio natively, but it's now possible
to mount the smb:// share through nautilus and point Banshee to a _symlink_ to
.gvfs/share on server dir. Banshee has problems with accessing fuse mounts
directly but seems to work fine with symlinks to those.

Another option is to use autofs which I'm quite happy with.

Of course it would be best if Banshee would support all gio/gvfs communication
natively. It should be possible to set a 'local' and 'remote' share. The local
one could be integrated into the library itself and a remote share could be a
separate source but still indexed in my banshee db.

---

### Post by bornagainpenguin on 2010-04-17
> **sdowney717 said:**
> I have shared folders on one pc containing videos.
I want to import this location into banshee
the import dialog allows a typed line

what would be the link to type for a shared folder on the network?

well, I solved it following this post. Mount a smb share in nautilus.

goto network
find the shared network folder
right click and select 'mount' it will then appear in the left side panel

the share then shows in a hidden folder called .gvfs
when importing the media in banshee point it to this hidden folder

Thank you for this tip!

--bornagainpenguin

---

