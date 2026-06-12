---
title: "Recoll - Indexing hidden files"
date: 2010-06-28
forum: General Help
---

### Post by yeleek on 2010-06-28
Hi,

I use Recoll, and love it.  However its not indexing hidden files, and when I'm looking for a specific configuration value it would help a lot if it did.  I believe its capable of it, but may not be configured for it.

In Recoll config, local parameters - I have the following in global skipped names:

#*
bin
CVS
Cache
cache*
caughtspam
tmp
.thumbnails
.svn
*~
recollrc
.beagle
.git
.hg
.bzr
loop.ps

Any ideas pls?

---

### Post by yeleek on 2010-06-29
Anyone?

---

### Post by Rubi1200 on 2010-06-29
Hi yeleek,
I found this; not sure if this is what you are looking for but hope it helps:

> The list in the default configuration does not exclude hidden directories (names beginning with a dot), which means that it may index quite a few things that you do not want.

[http://www.lesbonscomptes.com/recoll/usermanual/rcl.install.config.html](http://www.lesbonscomptes.com/recoll/usermanual/rcl.install.config.html)

---

### Post by yeleek on 2010-06-29
Hey,

Thanks - yeah I found that (manual comes with package).  I guess the bit that confuses me, is what do these mean?

#*
*~

And could they be responsible?  I can 'find' std files in hidden folders, its hidden files themselves which seem to be missed....

Cheers

---

### Post by medoc92 on 2010-07-02
> **yeleek said:**
> Hey,

Thanks - yeah I found that (manual comes with package).  I guess the bit that confuses me, is what do these mean?

#*
*~

And could they be responsible?  I can 'find' std files in hidden folders, its hidden files themselves which seem to be missed....

Cheers

The incantations above are used to skip misc emacs backup files (file names beginning with  a # or ending in ~). I really have no idea why your hidden files (meaning file names beginning with a '.' I guess) would be skipped by Recoll, this is certainly not the case by default. Email me at "jfd at recoll dot org" if you want to investigate.
Cheers,
jf

---

