---
title: "dispaly all files list morethan 20 mb size in ubuntu terminal"
date: 2010-07-01
forum: General Help
---

### Post by kptsuresh on 2010-07-01
hi guys !
I want to know how to get the details of all files in my system more than 20mb or some specific amount of file size in Ubuntu terminal by using commands...

any help please..

thanks in advance.. :)

---

### Post by CannibalZerg on 2010-07-01
```

sudo find /path/to/file -type f  -size +20M -ls

```

Replace "/path/to/files" with "/", if you want to search entire system.

---

