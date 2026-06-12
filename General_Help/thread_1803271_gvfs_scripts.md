---
title: "gvfs scripts?"
date: 2011-07-13
forum: General Help
---

### Post by justleen on 2011-07-13
Hi All,

Can any one tell me where the scripts/files are located which are used to mount a network share on .gvfs?

I've got a setup with WOL working, and I'd like to be able to just click the bookmarked share, so that a WOL wake up is send before mounting it.

Any hints would be appreciated!

---

### Post by Morbius1 on 2011-07-13
Not sure if this answers your question:

```
gvfs-mount smb://server/share
```
That command will connect to and mount the remote share at the .gvfs mount point.

---

