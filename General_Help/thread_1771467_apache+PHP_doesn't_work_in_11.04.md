---
title: "apache+PHP doesn't work in 11.04"
date: 2011-05-30
forum: General Help
---

### Post by Kallikanzarid on 2011-05-30
I have installed apache+PHP, but even phpinfo gives 500. CLI PHP works fine. What can be the cause?

---

### Post by ruffEdgz on 2011-05-30
If you do the following command, do you see both php.conf and php.load is enabled?:
```
 
ll /etc/apache2/mods-enabled/ | grep php

```
I can only assume that this is the reason why php isn't being used or you just installed the php5-cli without installing php5.

---

