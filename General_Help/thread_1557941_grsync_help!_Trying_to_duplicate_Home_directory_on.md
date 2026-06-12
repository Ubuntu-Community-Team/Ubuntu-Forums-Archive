---
title: "grsync help! Trying to duplicate Home directory on another PC"
date: 2010-08-21
forum: General Help
---

### Post by The Bright Side on 2010-08-21
Hey guys,

I hope you can help me with this probably not too uncommon problem. I have a desktop and laptop PC, and I want to duplicate the desktop's Home directory (without all the hidden stuff, only my "normal" folders) on my laptop.

My laptop has 2 hard disks, and I want to have my "Multimedia" folder on the second hard disk (it's all on the same folder on the desktop).

Creating the backup on an external hard drive is not the problem. I use the option "--exclude-from=".grsync/exclude", and the "exclude" file contains only the line ".*".

When backing up, I use the "delete on destination" option to create a perfect duplicate of the Home folder.

Now I tried to copy that - without the "Multimedia" folder - to my laptop's hard disk. So this time, I put only the line "Multimedia" into the "exclude" file.

Guess what happened? Grsync immediately started deleting all the hidden folders on my destination.

I stopped it before it could do any major damage (deleted all my theme settings).

Long story, short question:

How can I configure grsync to copy everything except the "Multimedia" to my destination and delete all files that don't match - except the hidden folders and files directly in "Home"?

---

