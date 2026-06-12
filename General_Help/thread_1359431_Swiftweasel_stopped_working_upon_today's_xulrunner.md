---
title: "Swiftweasel stopped working upon today's xulrunner updates"
date: 2009-12-19
forum: General Help
---

### Post by MountainX on 2009-12-19
The error I get is:
```
/opt/swiftweasel/swiftweasel-3.5.5/swiftweasel-bin: 
error while loading shared libraries: libxul.so: 
cannot open shared object file: No such file or directory
```

I'm sure it's because libxul.so was located in /usr/lib/xulrunner-1.9.1.5 and now it is in /usr/lib/xulrunner-1.9.1.6

What's the right way to fix this so it won't happen again on the next xulrunner update?

---

### Post by MountainX on 2009-12-19
This is not the way I would prefer to solve this, but as a temporary workaround, here's what I did:

```
cd /opt/swiftweasel/swiftweasel-3.5.5
rm libxpcom.so
rm libxul.so
ln -s /usr/lib/xulrunner-1.9.1.6/libxul.so libxul.so
ln -s /usr/lib/xulrunner-1.9.1.6/libxpcom.so libxpcom.so
```

---

