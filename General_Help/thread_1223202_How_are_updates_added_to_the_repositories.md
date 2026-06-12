---
title: "How are updates added to the repositories?"
date: 2009-07-25
forum: General Help
---

### Post by sg42 on 2009-07-25
Hi, all.

Jaunty currently has octave version 3.0.1 as the latest version. The octave people have released a later stable version (3.2.2). I tried reading the source of a particular function, and the new version has fixed a bug in the old version.

I can compile the new one and install it manually, but would rather use synaptic. So, my question is this:

Would anyone know how the latest version makes it to the Ubuntu repositories? I'd be glad to try my hand at making a .deb file from the source and sending it to the repositories.

Thanks.

---

### Post by shaggy999 on 2009-07-26
Well normally you talk to the package maintainer:

```
apt-cache show octave3.0 | grep Maintainer
```

However, updates are generally only submitted to a current release of Ubuntu if it's security-related. If you want an official Ubuntu package updated that is not a security release you can:

1) Check to see if it's been submitted to backports
2) Look for a seperate PPA archive that maintains the package
3) Wait for the next release of Ubuntu

---

