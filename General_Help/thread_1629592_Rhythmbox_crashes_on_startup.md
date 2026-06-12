---
title: "Rhythmbox crashes on startup"
date: 2010-11-23
forum: General Help
---

### Post by Shpadoinkle on 2010-11-23
Using Rhythmbox on Ubuntu 10.10. When I start it, it will pop up fpr about 2 seconds and this is the error I recieve...

```
andrew@andrew-linux:~$ rhythmbox

(rhythmbox:3408): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:3408): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

(rhythmbox:3408): GLib-GObject-CRITICAL **: g_type_class_add_private: assertion `private_size > 0' failed
** (rhythmbox:3408): DEBUG: Loading the real store page

** (rhythmbox:3408): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:3408): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Segmentation fault
```

Any help would be appreciated!

---

### Post by Shpadoinkle on 2010-11-23
Well, found a temporary solution..

I removed the package > rhythmbox-ubuntuone-music-store and all is fine now.

---

### Post by ubuntwinkel on 2011-01-06
> **Shpadoinkle said:**
> Well, found a temporary solution..

I removed the package rhythmbox-ubuntuone-music-store and all is fine now.

That fixed it for me.  

For me rhythmbox was not crashing, but freezing after a few seconds, before it showed any songs or finished loading.  Looked at everything I could think of, checked network connectivity (sshfs, nfs, all OK).

Then I found this thread, uninstalled rhythmbox-ubuntuone-music-store, and rhythmbox started fine.  

Thanks!

---

### Post by Shpadoinkle on 2011-01-06
Glad I could help!

---

### Post by NeddyDownUnder on 2011-03-26
That fix just worked for me too...

Thanks.

---

