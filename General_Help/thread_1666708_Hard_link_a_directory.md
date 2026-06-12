---
title: "Hard link a directory"
date: 2011-01-14
forum: General Help
---

### Post by COKEDUDE on 2011-01-14
Is it possible to Hard link a directory? Some people on google say it is possible and some say it is not possible. I haven't seen a working solution though.

---

### Post by Vaphell on 2011-01-14
doesn't ln without the -s switch work?

---

### Post by vanadium on 2011-01-14
Why do you need it?

---

### Post by COKEDUDE on 2011-01-14
> **Vaphell said:**
> doesn't ln without the -s switch work?

No. It complains that it is not allowed. 

> **vanadium said:**
> Why do you need it?

The reason I am doing this is because I am sharing some work with other people and I don't want them to be able to delete my copy. I want to be able to see whatever they add my work so hard linking is the best way I know of to do this.

---

### Post by vanadium on 2011-01-15
Technically, it would probably very much possible as it can be done with files, and "man ln" even mentions options for it. However, the operating system does not allow it because this would allow to setup very confusing structures. There is a risk of creating loops, which would make it impossible to run utilities that recurse subdirectories. Therefore, it is not allowed/supported.

The problem with hard links indeed is file management, even with single hardlinked files. You can not see which is the "orginal" and which the "target", because any hard links are equivalent. A single file name indeed is a hard link in its own right.


For general purposes, you better use soft links. It allows you to remember later how the system is set-up. Hard links to files nevertheless can come in handy for specific purposes.

---

### Post by COKEDUDE on 2011-01-17
> **vanadium said:**
> Technically, it would probably very much possible as it can be done with files, and "man ln" even mentions options for it. However, the operating system does not allow it because this would allow to setup very confusing structures. There is a risk of creating loops, which would make it impossible to run utilities that recurse subdirectories. Therefore, it is not allowed/supported.

The problem with hard links indeed is file management, even with single hardlinked files. You can not see which is the "orginal" and which the "target", because any hard links are equivalent. A single file name indeed is a hard link in its own right.


For general purposes, you better use soft links. It allows you to remember later how the system is set-up. Hard links to files nevertheless can come in handy for specific purposes.

Soft links don't update.

---

### Post by vanadium on 2011-01-17
> **COKEDUDE said:**
> Soft links don't update.
Soft links directly lead you to the original file/directory. There is no need that they update. Indeed, the softlink won't work anymore if the hardlink (file/directory) it refers to, is moved.

---

### Post by Urhixidur on 2011-03-04
> **COKEDUDE said:**
> 
The reason I am doing this is because I am sharing some work with other people and I don't want them to be able to delete my copy. I want to be able to see whatever they add my work so hard linking is the best way I know of to do this.

You should be able to set up the user privileges to achieve this: just make the files you "expose" read-only to users other than you (or the admins, obviously).  If you did share hard links, be aware that your "collaborators" would then be able to change the contents of those files as long as they've got write access.  A hard link is nothing more than a separate directory entry for the same underlying file.

Windows supports "hard-linked directories" as junction points : they're quite handy, but one must indeed take care that no loops are created.

Another option that may be useful for you is cloning: you copy an entire directory structure somewhere else, except that every file in those directories is a hard link to the original file (in the original directory structure).

---

