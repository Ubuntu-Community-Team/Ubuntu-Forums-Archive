---
title: "best way to downgrade from php 5.3 to 5.2.17"
date: 2012-05-09
forum: General Help
---

### Post by metalsoft on 2012-05-09
hello everyone
i am using ubuntu 10.04 Server edition with plesk 10.4.4
i need to downgrade from php 5.3 to 5.2.17 in order to get zend optimizer to work.
i heard that downgrading php and compiling a new version of it might corrupt plesk control panel and it should be done carefully. so what i wanted to ask is : "What is the **safest** and **easiest** way to downgrade from php 5.3 to 5.2.17 on my server without any trouble?"

---

### Post by Sergius14 on 2012-05-09
This is the best Way:

[http://randyfay.com/node/63](http://randyfay.com/node/63)

BUT you are going to install unsecure 5.2 versions from Karmic edition.

Give a try to that method but changing a bit and instead of Karmic (9.10) choose Hardy (8.04) which has support up to Apr/2013 for Servers editions.

This method with 8.04 packages are the best/secure/easy way to dowgrade PHP from 5.3 to 5.2.

---

