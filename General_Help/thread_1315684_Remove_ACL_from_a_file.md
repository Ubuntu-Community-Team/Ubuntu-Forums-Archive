---
title: "Remove ACL from a file"
date: 2009-11-05
forum: General Help
---

### Post by hwttdz on 2009-11-05
Somehow a bunch of files in my home directory got hit with ACL (access control lists), which is preventing me from creating on the fly backups of things, like when editing a file.  Anyways I'd like to remove ACL's from all my files, and I seem to be having a lot of trouble with setfacl.  Can anyone tell me how to remove an ACL from a file?

I'm so happy to mark this one solved, this was a real pain. Anyways, I may have been mistaken the dot is actually an selinux security context, which can be removed with the setfattr command.  To run this on everything below a given directory (i.e. everything in ~ if run from ~) one can do

find . -print0 |xargs -0 -n 1 sudo setfattr -h -x security.selinux

The sudo is needed (despite the fact that they're my files).  Anyways hopefully this is the end of my problems with this.

---

