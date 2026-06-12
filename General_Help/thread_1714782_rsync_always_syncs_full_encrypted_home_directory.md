---
title: "rsync always syncs full encrypted home directory"
date: 2011-03-25
forum: General Help
---

### Post by marnell on 2011-03-25
I use rsync to synchronize a couple of media folders on my ubuntu (netbook remix) laptop with my NAS (debian). The good news is that it seems to work great - all my files are on both sides. The bad news is that it appears that rsync always syncs the full directory every time I run it, taking about 14 hours. I know for a fact that very few, if any, of these media files ever change on the NAS.

I'm using the simple command:
rsync -zvr --progress /nas/source /laptop/destination

I have a sneaking suspicion that since I encrypt my home directory (where my local copy of the media directory is) that every time I reboot it changes a couple of bits that causes rsync to think it needs to re-sync the files. So, I tried running the command again immediately after finishing - with the same results.

Oh, I should also note that the /nas/source location is mounted locally as another folder in my home directory. I could query the source directly, but I have it mounted for convenience when I'm on my local network - and not all of my media files get synced.

What's going on here? Shouldn't this only sync incremental changes?

---

### Post by marnell on 2011-03-26
bump!

---

### Post by marnell on 2011-03-28
C'mon guys... does anyone know what's going on here? I guess I'll run my own tests to see if there's any change.

---

### Post by blueridgedog on 2011-03-28
Have you tried --size-only?  Have you tried looking at what it wants to copy with --list-only?  Also, do you need compression?  Finally, do the file modification dates change when you decrypt your home directory?  If so, the behavior should be fixed with the size only flag.

---

