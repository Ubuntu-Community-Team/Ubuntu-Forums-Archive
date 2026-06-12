---
title: "Sync two directories on the same system."
date: 2010-02-01
forum: General Help
---

### Post by iEthan on 2010-02-01
I have two directories:

[LIST]
[*]/home/Dropbox/InstantInstall/Version 2
[*]/var/www/instantinstall
[/LIST]

I want to keep the changes in the first directory synced with the ones in the second directory. How would I do so? I was thinking a bash script on a cron job.

---

### Post by whiskeylover on 2010-02-01
Why not create a symbolic link instead?

---

### Post by ajgreeny on 2010-02-01
Yes, use a link.

I have four different linux distros on my machine and all the minor testing ones that I have just to look at have links to the data folders in my main distro (docs, photos, videos, music etc etc) in their own home folders.  I do not link other folders/files except sometimes the hidden .mozilla and .mozilla-thunderbird profile folders.  That way any emails I get in one of the test distros is in the main distro's mail folder rather than separate, and bookmarks in firefox are the same.  The latter can now be done more easily with various extensions for firefox.

---

