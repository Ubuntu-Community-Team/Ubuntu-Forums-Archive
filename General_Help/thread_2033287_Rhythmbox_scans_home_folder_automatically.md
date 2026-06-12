---
title: "Rhythmbox scans home folder automatically"
date: 2012-07-25
forum: General Help
---

### Post by anoe on 2012-07-25
hi there, i've got ubuntu precise pangolin (12.04) with all updates and a lot of audio software (from ubuntu studio and other repositories).

I've got my music in a external usb hard drive. God knows why, rhythmbox is scanning my home folder automatically, thought i don't think i have ever told him so. I deleted ~/.local/share/rhythmbox and ~/.gconf/apps/rhythmbox with no luck (i did this after editing configuraton with gconfig-editor to make sure the only folder active in rhythmbox library folders was the one in the external drive).

After deleting everything, i run rhythmbox and it automatically scans again the home folder...

i'm gonna purge it and install it again, to see what's up...

any other suggestion?

tx

---

### Post by BBQdave on 2012-07-25
> **anoe said:**
> any other suggestion?

Yup...

Rhythmbox > Edit > Preferences > Music (tab) >
un-tick *Watch my library for new files*
or set location of music files - *Music files are placed in* :)

---

### Post by anoe on 2012-07-26
tx.

i did that - untick the watch..., exited rhythmbox, deleted ~/.local/share/rhythmbox/rhythmdb.xml (to start from scratch) and then assigned the music library folder.

cheers!!!

---

