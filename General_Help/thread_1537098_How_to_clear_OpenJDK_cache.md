---
title: "How to clear OpenJDK cache?"
date: 2010-07-23
forum: General Help
---

### Post by pwaugh on 2010-07-23
I've been advised to "clear the java cache", and to do so under Windows, one would open the java control panel.  Of course, I'm using OpenJDK, and not Java's java.

Can anyone tell me how I would clear the java cache?

thanks

---

### Post by alex_mayorga on 2011-03-01
Got inspiration from [http://ubuntuforums.org/showpost.php?p=9722971&postcount=2](http://ubuntuforums.org/showpost.php?p=9722971&postcount=2)

In Ubuntu 11.04 the location seems to be:
```
~\.icedtea\cache
```

So to clear the cache just do:
```
rm -rf ~\.icedtea\cache
```

Hope it helps.

---

