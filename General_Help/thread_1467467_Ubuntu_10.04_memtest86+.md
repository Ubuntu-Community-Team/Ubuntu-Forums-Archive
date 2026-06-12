---
title: "Ubuntu 10.04 memtest86+"
date: 2010-04-30
forum: General Help
---

### Post by UTBlueDevil on 2010-04-30
Ok. I have tried to install Ubuntu 10.04 four times now, but everytime I do it freezes at the exact same spot..."Preparing Memtest86+" with "about 18" minutes left. I am upgrading from 9.04, I have had to reinstall the whole OS after this failed the three other times. I really like Ubuntu, but I can't figure this out! Any help would be greatly appreciated.

---

### Post by mathfreak123 on 2010-04-30
I always thought the memory test was supposed to continue indefinitely, or through several passes.

---

### Post by UTBlueDevil on 2010-04-30
Thanks for the quick response. That would make sense, but it has been sitting for over two hours saying it has "about 18 minutes remaining". Any more ideas?

---

### Post by bcbc on 2010-04-30
Is this a wubi update?

I did this as a test and it was looping under this - if you click on the terminal window it just shows 'finding <some kernel>'
Anyway - just click CTRL-C on this, and then it continues. I've seen a number of other posts from wubi users showing this works.

---

### Post by ranch hand on 2010-04-30
If you are installing this should not be a problem.  File a bug;
```

ubuntu-bug ubiquity

```
from your live CD.

If you are running an upgrade you will have better luck if you upgrade to 9.10 and then to 10.04.

---

### Post by UTBlueDevil on 2010-04-30
CTRL+C worked! Thanks so much!

---

