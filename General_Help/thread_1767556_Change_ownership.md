---
title: "Change ownership"
date: 2011-05-25
forum: General Help
---

### Post by Bobscrachy on 2011-05-25
I need to change the ownership of some files in my opt directory. I tried using chown, with no success. 

sudo chown user /opt/swift/bin

All this did was cause little locks to appear on the icons in that directory. The user privileges are still unchangeable.

---

### Post by ruffEdgz on 2011-05-25
If the path /opt/swift/bin is an actual file and not a directory, the command you used should have worked. You could just try not using the -h since that only helps if you trying to change symbolic links.

If the path /opt/swift/bin is a directory and you need not just that directory but the files below it to also have the same ownership, you will need to do the following code:

```

sudo chown -r user /opt/swift/bin/

```

The -r will recursively go through that directory and make "user" the owner of all the files inside /opt/swift/bin/

Hope that helps.

---

