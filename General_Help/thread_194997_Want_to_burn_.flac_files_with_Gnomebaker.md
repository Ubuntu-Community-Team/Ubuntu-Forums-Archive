---
title: "Want to burn .flac files with Gnomebaker"
date: 2006-06-12
forum: General Help
---

### Post by TeeAhr1 on 2006-06-12
Its backend is cdrecord.  What libraries does that use?  The error message I get from gnomebaker when trying to import flac files is completely unhelpful.

EDIT: Looking at the homepage, it seems to imply that gstreamer0.8-flac is what's called for, but I have that package.

---

### Post by grendelkhan on 2006-06-12
I think the version of Gnomebaker in Dapper uses Gstreamer 10, so I would say you might need gstreamer plugins bad to get it to work

---

### Post by TeeAhr1 on 2006-06-13
**SOLVED.**

grendelkhan, thanks for the reply.  Turns out it is 0.8, but your suggestion got me going down the right track.  *gstreamer0.8-mad* and *gstreamer0.8-misc* (or one or the other, I installed them both as they are also listed as dependencies on the gnomebaker homepage) are also required.

---

