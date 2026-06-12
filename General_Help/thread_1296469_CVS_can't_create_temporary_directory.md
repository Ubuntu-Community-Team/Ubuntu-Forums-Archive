---
title: "CVS can't create temporary directory"
date: 2009-10-20
forum: General Help
---

### Post by Steinar on 2009-10-20
I'm having problems with CVS on a freshly installed Jaunty box.

```
cvs update
can't create temporary directory /tmp/cvs-serv14592
Read-only file system
```

My user can easily create directories under /tmp.
Do I need to add a user CVS to /etc/group or something?

---

### Post by zefew on 2009-10-20
> **Steinar said:**
> I'm having problems with CVS on a freshly installed Jaunty box.

```
cvs update
can't create temporary directory /tmp/cvs-serv14592
Read-only file system
```

My user can easily create directories under /tmp.
Do I need to add a user CVS to /etc/group or something?

Weird. I started experiencing the same thing. Probably a bug on CVS.

/tmp permission is 777 by default. anybody can create a directory under it.

---

### Post by Steinar on 2009-10-21
CVS now works fine, this seems to have been a server-side problem (cvs.savannah.gnu.org).

---

