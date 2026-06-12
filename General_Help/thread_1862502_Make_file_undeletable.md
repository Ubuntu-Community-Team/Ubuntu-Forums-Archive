---
title: "Make file undeletable"
date: 2011-10-16
forum: General Help
---

### Post by samuelm on 2011-10-16
Hi,
I am using ext4 on my box. Is it possible in *any* way to make a file undeletable? Undeletable not in the sense of "recoverable if deleted" but in the sense of "not removable even by root, unless made deletable by root". In other words, something like "chattr +i" except that modification of the file's contents would be allowed. Is it possible to do this?

Thanks,
samuelm

---

### Post by collisionystm on 2011-10-16
> **samuelm said:**
> Hi,
I am using ext4 on my box. Is it possible in *any* way to make a file undeletable? Undeletable not in the sense of "recoverable if deleted" but in the sense of "not removable even by root, unless made deletable by root". In other words, something like "chattr +i" except that modification of the file's contents would be allowed. Is it possible to do this?

Thanks,
samuelm

Pretty sure you cannot stop root from deleting files. That is why root is dangerous. It ignores any and all rules of the system. Of course... I could be wrong! :)

---

### Post by samuelm on 2011-10-16
Well, changing a file's attributes with "chattr" can render the file undeletable even by root, using the "+i" flag. But the problem is, the file becomes unmodifiable as well. I'd like to be able to modify the file, but not be able to delete it.

---

### Post by capscrew on 2011-10-16
> **samuelm said:**
> Well, changing a file's attributes with "chattr" can render the file undeletable even by root, using the "+i" flag. But the problem is, the file becomes unmodifiable as well. I'd like to be able to modify the file, but not be able to delete it.

I believe chattr +i** makes the file immutable, what does chattr -u** do differently?

---

### Post by samuelm on 2011-10-16
"chattr +u" is a "deprecated" attribute that only used to work on the first ext fs. It no longer works under ext2,3, or 4. See the bottom of "man chattr"

---

### Post by hwttdz on 2011-10-16
Maybe put it on a partition which is mounted as read only?  That way you/root couldn't modify it without unmounting/remounting.  Some of the removable media even have physical switches to make read only (some usb sticks, memory cards...).

---

### Post by samuelm on 2011-10-22
Thank you all for your suggestions. I'll mark this thread as solved. In the meantime, I hope Theodore Ts'o and other Linux developers develop such a feature and build it into the ext4 or a future filesystem.

---

### Post by The Cog on 2011-10-22
Running **chattr +i** on the file's containing directory will make the directory unmodifiable so that you can't add or delete any files in there. This might suit your needs.

---

### Post by samuelm on 2011-10-23
Ok, wow. Thanks!

---

