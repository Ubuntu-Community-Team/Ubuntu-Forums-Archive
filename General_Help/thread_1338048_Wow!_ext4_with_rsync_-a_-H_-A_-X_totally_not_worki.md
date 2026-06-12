---
title: "Wow! ext4 with rsync -a -H -A -X totally not working w/ hard link"
date: 2009-11-26
forum: General Help
---

### Post by btbluesky on 2009-11-26
Got a new hdd. The old one has a ext4 fs struct of a daily snapshot using hard links w/ rsync and cp -a (the basic principle is [here]("http://www.mikerubel.org/computers/rsync_snapshots/") )
And it's been running fine in the old hdd.

Tried rsync -a -H -A -X (the -H is suppose to work w/ hard links), and the entire structure is not rsync at all.

Guess I'll have to re-backup everything manually to get it up and running...

---

