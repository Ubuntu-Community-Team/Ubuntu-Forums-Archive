---
title: "how to get libcrypto.so.4"
date: 2012-08-14
forum: General Help
---

### Post by psw2099 on 2012-08-14
Not sure if this is the right place to post this question, but I'll start here. I'm setting up a simulator on ubuntu that requires libcrypto.so.4. How to I get this file? Thanks.

---

### Post by oldos2er on 2012-08-14
```
apt-cache search libcrypto
``` will show each relevant package, once you've decided which one you need run ```
sudo apt-get install libcrypto++9
``` for example.

---

