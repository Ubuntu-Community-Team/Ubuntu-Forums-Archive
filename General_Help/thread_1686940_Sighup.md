---
title: "Sighup"
date: 2011-02-13
forum: General Help
---

### Post by mahmoodn on 2011-02-13
As you know ```
kill -HUP <PID>
``` should force the <PID> to reread the configuration file. However for some commands it doesn't work.
For example, ```
kill -HUP `pidof kdevelop.bin`
``` will only close the kdevelop!! and not restarting that

Where did I misunderstood?

---

### Post by Habitual on 2011-02-13
Does ```
pidof kdevelop.bin
``` return a PID?

Try this 
```
kill -HUP $(pidof kdevelop.bin)
```

It may be just kdevelop even though the .bin was used to start it.

pidof kdevelop should tell you for certain.

---

