---
title: "Tar Behaviour - Exiting with failure status due to previous errors"
date: 2010-06-11
forum: General Help
---

### Post by M1GEO on 2010-06-11
I just wanted to check when tar prints the following line
> Exiting with failure status due to previous errors

Does that mean the created archive is broken, or, just that some individual files failed.

I am trying to tar up my home directory as a form of crude backup, but when the computer is running, files obviously change.  Tar, run from CRON, always reports the following:

> tar: Removing leading `/' from member names
tar: Exiting with failure status due to previous errors

I wonder if the resulting file will be good (barring those few failed files - which I don't need), or if tar dies and leaves an unfinished file?

Any heads up would be great,
Thanks,

---

### Post by labinnsw on 2010-06-13
This error, I believe always appears at the end of the backup. Your back up file should still be good. To test it, right click the file and select "extract here." The resulting file should be identical the whatever you are backing up.

---

### Post by M1GEO on 2010-06-15
Great. Thanks for the reply. I shall check that out. I mean I'm talking a good Terrabyte or so, so its going to take a while. The actual script creates incremental backups, but the error remains the same. I shall restore a few and see how I get on. 

Thanks.

---

### Post by M1GEO on 2010-06-15
Duplicate post. Sorry.

---

### Post by john newbuntu on 2010-06-16
I like a good 0 return code from tar.   Typically, files you do not own or some mounted filesystems cause problems with tar.  Some examples include excluding the .gvfs virtual filesystem and make sure you own .ICEAuthority.

---

