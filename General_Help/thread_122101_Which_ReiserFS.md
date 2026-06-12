---
title: "Which ReiserFS?"
date: 2006-01-26
forum: General Help
---

### Post by fbg111 on 2006-01-26
In the Breezy installation partition tool, one file system option is ReiserFS, but it is not clear whether that is v3 or v4.  Does anyone know?  I searched the website and forums, but can't find a clear answer for this.  If I missed an Ubuntu specs webpage or something, feel free to post it.  Thanks!

---

### Post by hw-tph on 2006-01-26
It is reiserfs v3.6.
v4 is not widely used - AFAIK the stable vanilla kernel has no reiserfs4 support yet.


Håkan

---

### Post by slux on 2006-01-26
...not that the ubuntu kernel is the same thing as the stable vanilla kernel...

But yeah, it's still considered not for the faint of heart. Filesystems usually take their time to mature because bugs can be so devastating.

---

### Post by fbg111 on 2006-01-27
Thanks.  Is there a command that ouputs the fs version from within linux?

---

