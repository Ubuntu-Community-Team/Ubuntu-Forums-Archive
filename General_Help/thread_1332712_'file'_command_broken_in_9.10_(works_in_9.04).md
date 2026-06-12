---
title: "'file' command broken in 9.10 (works in 9.04)"
date: 2009-11-20
forum: General Help
---

### Post by Mark Rose on 2009-11-20
I'm having a rather strange issue.

I am using the Fileinfo extension to PHP to detect the contents of uploaded files. It works great and returns results like "video/mpeg" in Ubuntu 9.04.

However, in 9.10 it's returning "application/octet-stream".

The same issue is noted with the 'file' command, so I suspect it's a system level issue.

Can anyone offer any insight as to how to fix this?

---

### Post by Giblet5 on 2009-11-20
From the file man page:

"**MAGIC DIRECTORY**
...
     The order of entries in the magic file is significant.  Depending on what system you are using, the order that they are put together may be incorrect."

Check out your /etc/magic file. (I was a bit surprised)

You can grab one from a Jaunty CD, or there are plenty of them available elsewhere.

---

### Post by Mark Rose on 2009-11-20
Ubuntu9.10$ file --version
file-5.03
magic file from /etc/magic:/usr/share/misc/magic

Ubuntu9.04$ file --version
file-4.26
magic file from /etc/magic:/usr/share/file/magic

/etc/magic has only a couple comments (in 9.10 and 9.04)
/usr/share/misc/magic is a symlink to ../file/magic

Checking /usr/share/misc/magic in 9.10 and 9.04 have several differences.

Hmmm...

---

### Post by Giblet5 on 2009-11-20
So make a copy of the existing magic file and copy the one from a 9.04 iso. See if it works as expected. That's easier than trying to trace how the diffs will be interpreted.

---

### Post by Mark Rose on 2009-11-20
Copying the files in /usr/share/file/ over has no effect. I'm going to try installing the old version of file.

---

### Post by Mark Rose on 2009-11-20
Manually installing

libmagic1_4.26-2ubuntu3_amd64.deb
file_4.26-2ubuntu3_amd64.deb

from Jaunty solves the problem.

---

### Post by dcstar on 2009-11-20
> **Mark Rose said:**
> Manually installing

libmagic1_4.26-2ubuntu3_amd64.deb
file_4.26-2ubuntu3_amd64.deb

from Jaunty solves the problem.

It solves **your** problem. Put in a proper bug report so the developers know about the issue.

---

### Post by Mark Rose on 2009-11-20
> **dcstar said:**
> It solves **your** problem. Put in a proper bug report so the developers know about the issue.

Already did :P

I guess I should have linked it here, too.

[https://bugs.launchpad.net/bugs/486085](https://bugs.launchpad.net/bugs/486085)

---

