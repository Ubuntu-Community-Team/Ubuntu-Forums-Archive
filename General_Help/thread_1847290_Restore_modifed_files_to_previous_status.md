---
title: "Restore modifed files to previous status"
date: 2011-09-20
forum: General Help
---

### Post by bobmarco on 2011-09-20
Hi there,
I accidentally resized some pics I wasn't supposed to, so now I'd like to restore them to their previous size. Tried GIMP obviously but the resolution turns very bad. I thought I can use some script/sw to restore those files. I tried back-in-time but had no saved snapshots, tried sbackup but it has an installation bug I couldn't figure out to solve. I'm now trying cg-restore [http://manpages.ubuntu.com/manpages/gutsy/man7/cogito.7.html](http://manpages.ubuntu.com/manpages/gutsy/man7/cogito.7.html) but the scripts does not run. The package cogito seems to be obsolete so I installed git, nevertheless the command 'cg-restore' is not found. Any idea?
Thank you in advance.

I'm using Ubuntu 11.04 with an ext4 filesystem.

---

### Post by mcduck on 2011-09-20
None of those backup/version control tools are going to work as an afterthought, they would only help had you been running them beforehands, so that they would actually have made backups of your files.

You might have been able to restore the original files using some file recovery tool, but that's not likely to work if you have been using the system, it probably has already overwritten the original data. Actually it probably overwrote the original files the moment you saved the new smaller images using the same filenames.

Sorry to tell you, but it's not likely you'd be able to recover the originals in any way. I can only recommend keeping regular backups of your files to avoid such situations in the future...

---

