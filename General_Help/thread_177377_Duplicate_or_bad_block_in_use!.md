---
title: "Duplicate or bad block in use!"
date: 2006-05-16
forum: General Help
---

### Post by bjornkri on 2006-05-16
Help! :shock:

This happens when I try booting:
```

Duplicate or bad block in use!
Multiply-claimed block(s) in inode 2224411: 222 8
(There are 1 inodes containing multiply-claimed blocks.)

File /etc/ufc.conf (inode #2224411, mod time Thu Oct 28 18:50:12 2004) has 2 multiply-claimed block(s), shared with 1 file(s):
        <filesystem metadata>

UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
         (i.e., without -a or -p options)


fsck failed. Please repair manually and reboot. Please note that the root system is currently mounted read-only. To remount it read-write:

# mount -n -o remount,rw /

CONTROL-D will exit from this shell and REBOOT the system.

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#

```

And that's that. What on earth should I do now?

*panicking slightly*

---

### Post by bjornkri on 2006-05-16
I tried doing the obvious thing, running fsck without any flags, and it gives me two options: Clone multiply-claimed blocks? and Delete file?

I answered both with a no, as I'm not sure what to do. Don't want to ruin anything :-k

---

### Post by bjornkri on 2006-05-16
Wow, hard to get a reply around here.

For future reference: Turns out that those just seem to be Big Scary Words, but the default options took care of it. Just ran fsck, answered yes to cloning and whatever came after that and voilá. Everything works fine.

---

### Post by Mustard on 2006-05-16
Glad you worked it out anyway. :)

---

