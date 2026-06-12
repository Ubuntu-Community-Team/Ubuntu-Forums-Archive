---
title: "Changing default USB automount permissions?"
date: 2009-12-01
forum: General Help
---

### Post by probedb on 2009-12-01
Hi folks,

I have a couple of USB drives I auto mount in Gnome and most stuff is fine.

However Squeezebox Server runs under it's own user and cannot see the drives.

It seems Gnome automounts as the current user but permissions are owner only, I need to set the read/write permissions so other users can access them.

Any thoughts? Have found the gconf-editor and tried adding a key 'mount_options' under system/storage/default_options/ntfs-3g

Cheers!
Paul.

---

