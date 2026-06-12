---
title: "how to undo chown root $(which ntfs-3g)???"
date: 2012-02-07
forum: General Help
---

### Post by ohnonot on 2012-02-07
i accidentally performed this:
```

chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g)
```
or actually i think it was a mistake.

after getting this error message:

Failed to mount xxxx:

Error mounting: mount exited with exit code 1: helper failed with:
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)

i check out the link in the error message, where it says:

... The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g) In such case the driver will also be able...

and i happpily went and did this only to find afterwards that one is "strongly discouraged" to do that.
experienced strange behavior after that, which *i think *has nothing to do with mounting.

what did i actually do?

can i undo it?

should i undo it?

any help appreciated. thanks.

---

### Post by Vaphell on 2012-02-07
it set the ownership of ntfs-3g binary to root (it was root either way) and changed properties to 4755 (default is 0755, so just run chmod with that value)
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by ohnonot on 2012-02-13
thanks!

so i undid the relevant part with
> chmod 0755 $(which ntfs-3g)-right?

system still works, no visible difference. good. i'm relieved.

---

### Post by ohnonot on 2012-02-15
...and since everything still works i'm marking this as solved.

---

