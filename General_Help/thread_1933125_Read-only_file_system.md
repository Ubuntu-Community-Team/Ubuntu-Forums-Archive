---
title: "Read-only file system?"
date: 2012-02-28
forum: General Help
---

### Post by Tornikee on 2012-02-28
Hello.

I use dual boot of Ubuntu 11.10 and Windows 7, and changed partition distribution today, allocating more disk space to Windows. After switching back to Ubuntu, I can't delete files either due to an error that says this can't be done on a read-only file system, or simply because 'delete' and 'move to trash' options in the right-click menu are grayed out. Also, I can't save files (pictures, etc.) from the web to the hard disk.

I am pretty certain this issue was caused by the partition change, but how can I solve it?

Thanks in advance.

---

### Post by Tornikee on 2012-02-29
Any hints?

---

### Post by SeijiSensei on 2012-02-29
Linux marks a filesystem as read-only when it discovers errors in the filesystem during mounting.  Here's one method to fix the problem:

Reboot and select the "recovery mode" kernel from the grub menu.  (If you don't see this menu, hold down shift during boot.)  You'll end up at a menu; choose the "root shell" option.

Now you'll be taken to a text-mode shell.  At the prompt, run these commands:

```
mount -n -o remount,rw /
touch /forcefsck
shutdown -r now

```

That will force a reboot and a filesystem check upon startup.

---

### Post by Tornikee on 2012-02-29
Thanks for the reply. Upon startup this evening, I ran Ubuntu Live CD and performed a disk check from there, and after switching to Ubuntu, the issue disappeared.
Still, thanks for the hint - I may need it in future.

---

