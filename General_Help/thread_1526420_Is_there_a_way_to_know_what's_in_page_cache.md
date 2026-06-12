---
title: "Is there a way to know what's in page cache?"
date: 2010-07-08
forum: General Help
---

### Post by xzased on 2010-07-08
Hi. I was wondering if there is a way to know which files are in the linux page cache. I've searched but the only thing I've found is meminfo... Is there anything out there that can give more details regarding what is being cached? Thanks

---

### Post by CannibalZerg on 2010-07-08
Look at fincore command:
[https://launchpad.net/ubuntu/karmic/i386/fcoretools/1.0-1](https://launchpad.net/ubuntu/karmic/i386/fcoretools/1.0-1)

To list all open files you can use lsof, something like:
```

#!/bin/bash
lsof | grep REG | awk '{print($9)}' | while read fn; do
 echo $fn`fincore $fn -justsummarize`
done

```

---

### Post by xzased on 2010-07-08
Thanks! Exactly what I needed :D

---

