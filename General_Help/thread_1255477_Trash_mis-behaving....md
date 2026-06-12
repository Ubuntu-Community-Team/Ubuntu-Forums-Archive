---
title: "Trash mis-behaving..."
date: 2009-09-01
forum: General Help
---

### Post by dkolars on 2009-09-01
Still figuring out Ubuntu JJ...  new problem... suddenly my trash icon disappeared from the bottom bar... so, added it back...  now, there is never anything in the trash, but files that I delete are totally gone... did several searches and they do not exist anymore...

And, using Gnome Image Viewer, attempted to delete an image, and was told that the program couldn't access the Trash...

Where is the Trash located?  I've read several posts and it seems to be very convoluted!!  My Trash folder is listed with my home dir, my mounted drives, and the directories I've created...  should it be somewhere else?

Frustrating, as delete doesn't always mean I really meant it :-)   Thanks!  dk

---

### Post by P4man on 2009-09-01
These may help:

[http://ubuntuforums.org/showthread.php?t=568324](http://ubuntuforums.org/showthread.php?t=568324)
[http://ubuntuforums.org/showthread.php?t=315381](http://ubuntuforums.org/showthread.php?t=315381)

---

### Post by dkolars on 2009-09-01
> **P4man said:**
> These may help:

[http://ubuntuforums.org/showthread.php?t=568324](http://ubuntuforums.org/showthread.php?t=568324)
[http://ubuntuforums.org/showthread.php?t=315381](http://ubuntuforums.org/showthread.php?t=315381)

Links mention that I should have ~/.Trash... Well, I have no ~/.Trash... can I just create it and some program will use it as it's meant to be used?

The other path mentioned in those links is /home/<user>/.local/share/Trash...

That exists, and contains 3 sub-dirs:  expunged, files, info.  All are empty.  When I delete a file, it does not go there.  As I mentioned, it is totally gone from the hdd...  

I used GNOME Commander to copy a file to a different directory, then deleted it.  I then used File Browser to search the File System... Found the original file + a backup copy on an external hdd, but not the deleted one.  So, something has taken away the directions to the Trash folder, wherever it should be...

Do I need to re-install something?  I see a lot of references to Nautilus, and have several Nautilus files installed, but not a program that is linked to anywhere..???

thanks.  dk

---

### Post by P4man on 2009-09-02
Do you have a hidden .trash-1000 folder? If so, remove that.

It seems the location of the trash folder has changed over time, and perhaps using some old programs causes a mix up. I also read elsewhere about a bug relating to this, which has been fixed meanwhile, but you may need to run the updater:

[http://ubuntuforums.org/showthread.php?t=1157497](http://ubuntuforums.org/showthread.php?t=1157497)

---

### Post by dkolars on 2009-09-03
Well, ran the updater, did NOT re-install Jaunty...  also allowed the updater to find un-verified updates, etc.

Still, nothing goes to the trash...

I did do a search for "trash" and found over 400 various icons for different trash states, many different resolutions... a LOT of duplication!!  Don't understand Linux well enuf yet to wade it and delete the "unneeded" ones...  no time for that, either, not until probably Nov!  

So, for now, deleted files get moved to new junk directory until I'm sure that they're not needed...

---

