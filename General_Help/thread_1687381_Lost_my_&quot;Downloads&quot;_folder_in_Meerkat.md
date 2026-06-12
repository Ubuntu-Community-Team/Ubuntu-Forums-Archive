---
title: "Lost my &quot;Downloads&quot; folder in Meerkat"
date: 2011-02-13
forum: General Help
---

### Post by grey1beard on 2011-02-13
Losing my car keys is something I have learned to live with, but now my Downloads folder has vanished.
I'm sure I left it in the usual place, but it's nowhere to be found.

I'd be very grateful if someone could help me find it, or at least tell me how to reinstate it.
I assume it's not as easy as just creating a new folder in my Home folder called "Downloads", is it ?

Fearful of breaking something else,
John

---

### Post by TeoBigusGeekus on 2011-02-13
> **grey1beard said:**
> I assume it's not as easy as just creating a new folder in my Home folder called "Downloads", is it ?

You'll never know until you try it.

---

### Post by oldfred on 2011-02-13
Did you have data you want to recover in Downloads?

Yes you can just create a new folder.

Have you looked in trash, and looked with this and with hidden files shown

gksudo nautilus

Just be careful not to delete or move anything else as with the above you are the administrator and can do anything, including lots of damage.
Places to look.
Trash
Here is where these files normally reside.

    * ~/.local/share/Trash User's Trash (hardy and later)
    * ~/.Trash User's Trash (pre-hardy)
    * /root/.local/share/Trash System Trash (hardy and later)
    * /root/.Trash System Trash (pre-hardy):
    * /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

---

### Post by grey1beard on 2011-02-13
OK, so that was easy, and nothing fell off.
John

---

### Post by grey1beard on 2011-02-13
Thanks for looking by oldfred.
I'll have an explore tomorrow as the eyelids are beginning to droop !
John

---

