---
title: "idle python-2.7 crashing"
date: 2012-09-28
forum: General Help
---

### Post by HomerSimpson748 on 2012-09-28
Running 12.04 64bit. IDLE Python 2.7 crashes after executing the following:

```

>>> help()
help> modules

```

syslog shows:

Sep 28 23:47:07 titan kernel: [642504.355460] idle-python2.7[19347]: segfault at 7fffe34cef98 ip 00007f51212e071b sp 00007fffe34cefa0 error 6 in libc-2.15.so[7f5121299000+1b3000]

---

