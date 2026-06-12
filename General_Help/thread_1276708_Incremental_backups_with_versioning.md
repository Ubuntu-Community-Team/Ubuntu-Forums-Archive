---
title: "Incremental backups with versioning"
date: 2009-09-27
forum: General Help
---

### Post by ensnare on 2009-09-27
Hi -- Is there a way to do incremental backups to a remote host with versioning (being able to compare files from one date to another) from the console?  I'm currently using rsync to basically mirror directories on a remote host ... but that doesn't provide protection if some of the files get deleted by mistake.  I'd like to use something like Crashplan but that seems kind of heavy and requires me to install X to configure it.

Thanks for your input and assistance.

---

### Post by StuartN on 2009-09-27
Try this idea - it makes an rsync backup, creates a hardlink copy of the backup (virtually no space, but it looks like the original) and then runs rsync --delete on the duplicate. And then shift them and run again, etc, for as many iterations as you want.

See [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/) for a detailed explanation and scripts.

---

