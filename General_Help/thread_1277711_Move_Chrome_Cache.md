---
title: "Move Chrome Cache"
date: 2009-09-28
forum: General Help
---

### Post by y87 on 2009-09-28
Hello,

I'd like to have the Google-Chrome unstable build store its Cache on a separate drive in Linux.  I'm running CrunchBang on Ubuntu 8.10.  I got my google-chrome-unstable version from [http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel).  In Windows, you typically just throw something like  --user-data-dir="path" after the command when running chrome.exe and then you can specify the drive and folder.  I tried doing this by running through a prompt: google-chrome  --user-data-dir="path".  This loads Chrome, but I can still see files being stored in my "tmp" folder (like large flash files from any streaming site).  Any suggestions on how get Chrome to store these files on a seperate drive?  Or is the easiest bet just to install Chrome to the seperate drive entirely? (If so, any easy instruction on manually installing the package to a seperate drive would also be appreciated :).) 

Thanks, Van

---

### Post by falconindy on 2009-09-28
I don't believe it can be changed in Linux (evidenced [here](http://code.google.com/p/chromium/issues/detail?id=14545)), but you might be able to trick Chromium with a symlink to where you actually want the cache located. From ~/.cache/chromium, remove the Cache folder and then:
```
ln -s /path/to/new/cache Cache
```
Not sure how much (if any) complaining Chromium will do because of this, but its worth a shot if changing the actual location really isn't possible yet.

---

### Post by y87 on 2009-09-29
Thanks for the reply.  A symlink does look like a very simple solution, and I appreciate the suggestion.  Unfortunately, when I run Chromium it automatically rewrites the symlink to old_Cache_000 and then recreates the original Cache directory.  Any other thoughts?  As mentioned, it may just not be possible yet.

---

### Post by albe.mann on 2009-10-29
According to [http://dev.chromium.org/user-experience/user-data-directory](http://dev.chromium.org/user-experience/user-data-directory) the cache is in $XDG_CACHE_HOME/google-chrome, so you might want to try changing $XDG_CACHE_HOME for Chrome.

---

### Post by mkarnicki on 2011-11-12
I know this thread is old, but some may still be looking for an answer. I've recently bought an SSD drive, so it was of interest to me. Solution:

vim /etc/chromium-browser/default

- CHROMIUM_FLAGS=""
+ CHROMIUM_FLAGS="--disk-cache-dir=/tmp/cache/chromium --disk-cache-size=314572800"

In this example, I gave chromium cache of size ~300 MB in my ram, as my fstab says (among other lines):
tmpfs           /tmp            tmpfs   nodev,nosuid,noexec,mode=1777  0 0

Cheers!

---

### Post by oldos2er on 2011-11-12
Closed, please don't bump old threads.

---

