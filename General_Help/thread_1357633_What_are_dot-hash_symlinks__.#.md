---
title: "What are dot-hash symlinks?  .#?"
date: 2009-12-17
forum: General Help
---

### Post by KernelKing on 2009-12-17
In the directories of a project I have been working on for several months, I have started to notice the presence of symlinks that are named 

.#filename.extension -> [email]username@ubuntu.four-digit-number.ten[/email]-digit-number

The username@ubuntu* is not available when I try to ls it.

filename.extension are files that I had or have been editing in Emacs.  Older versions of those files without the .# exist in the same directory.

What are these symlinks?

---

### Post by dcstar on 2009-12-17
> **KernelKing said:**
> In the directories of a project I have been working on for several months, I have started to notice the presence of symlinks that are named 

.#filename.extension -> [email]username@ubuntu.four-digit-number.ten[/email]-digit-number

The username@ubuntu* is not available when I try to ls it.

filename.extension are files that I had or have been editing in Emacs.  Older versions of those files without the .# exist in the same directory.

What are these symlinks?

[http://admissions.rpi.edu/dept/acs/rpinfo/common/Computing/Consulting/Software/Emacs/Hints/backup.html](http://admissions.rpi.edu/dept/acs/rpinfo/common/Computing/Consulting/Software/Emacs/Hints/backup.html)

They are probably archived copies of the various emacs edits.

---

