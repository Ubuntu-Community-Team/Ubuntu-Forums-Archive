---
title: "Synchronize data help - one way sync"
date: 2011-01-21
forum: General Help
---

### Post by linuxgr on 2011-01-21
Hi,
I've been googling my issue but I can not find the easiest/safest way to do this.

I have a folder(say /media/A/folderA) which contains very important information that I need to backup to another folder(say /media/B/folderB).

I need to do an ONE-WAY sync, for example:
If I delete something from folderA, it will also be deleted on folderB.
If something though gets deleted from folderB, I want it to be re-copied from folderA instead of being also deleted in folderA.

I am looking for an effective rsync command, which has lots of options and I am not sure which ones to use without messing up. Alternatives are also welcome.

Thanks!

---

### Post by silentstone on 2011-01-21
Rsync is pretty versatile.  You need to go through the manpage for it...these were buried in there: 
[QUOTE="man rsync"]
--existing                 skip creating new files on receiver
            --ignore-existing          skip updating files that exist on receiver
            --remove-source-files      sender removes synchronized files (non-dir)
            --del                      an alias for --delete-during
            --delete                   delete extraneous files from dest dirs
            --delete-before             receiver deletes before transfer (default)
            --delete-during            receiver deletes during xfer, not before
            --delete-delay             find deletions during, delete after
            --delete-after             receiver deletes after transfer, not before
            --delete-excluded          also delete excluded files from dest dirs
[/QUOTE]

Why not make a couple of test directories, and try out some command combos?   A decent GUI frontend for it is Grsync, which is in the repos, although it doesn't explain every single commandline-equivalent option.  Unison is another file sync tool in the repos.  Never tried it myself, but perhaps this would do the trick for you.

---

### Post by linuxgr on 2011-01-23
Thanks, I'll try a couple of those and see if it works the way I need it to.
:-)

---

