---
title: "A few questions about rsync"
date: 2011-10-04
forum: General Help
---

### Post by Manolicious on 2011-10-04
I like the idea of rsync, I typically use rsync -avvcz --progress and I use --delete if I had just reordered file directories, but there are a few things I'm not sure about what it is doing.

Now say I don't alter any files, I just alter the directory structure.  If I'm trying to back up to a copy of the old directory structure, I'd like rsync to just reorder the directory structure of the backup copy.  However from the readout it looks like rsync will whole sale delete a directory not in the master copy and proceed to write those files from scratch in the new directory.  Is their an option or another program that avoids this?  Is their an initial run I could to with rsync that just reorders the file directories without writing anything?  Am I just being a stickler?

Another thing, I've been running into corrupt files quite a lot on my system, and I'm worried about rsyncing those to my backups and rewriting what could still be the original unharmed file in the backup.  Is there a way to detect corrupt files through a directory quickly?  Is there a way rsync can detect and avoid backing up corrupt files?  Can you place a condition on rsync to not backup files with less memory than their previous version?

---

### Post by collisionystm on 2011-10-04
I use rsnapshot. It lets me do backups as far back as I want to go. You can even make 6 months worth of backups on an external drive. Or longer if you have the space. I guess this is an easy way to always have some kind of working file? The only thing I can suggest is typing rsync --help

---

### Post by seawolf167 on 2011-10-04
Rsync doesn't know that you just moved the directory from one location to another location. All it sees is that the destination isn't the same as the source, so if you pass the --delete switch, it'll remove the destination differences and re-write with the source contents.

---

