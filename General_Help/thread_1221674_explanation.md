---
title: "explanation"
date: 2009-07-24
forum: General Help
---

### Post by krisrae675 on 2009-07-24
hi could someone just breakdown the commands in this rsync filter
- /download/**/.lock*
- /download/**/.log*
+ /download
+ /download/**
+ /selfile
+ /selfile/**
+ .rsync-filter
: .rsync-filter
- *

thanks

---

### Post by wojox on 2009-07-24
+ includes
- excludes
* wildcard
** wildcard
/ directory

---

### Post by krisrae675 on 2009-07-24
> **wojox said:**
> + includes
- excludes
* wildcard
** wildcard
/ directory

Thanks for reply i have reference pointed those but its not quite that we are after.
In our ccobex folder is (download, selfile, obexfile.log and obexscan.log) at present the selfile and download transfer over no prob, but the obexfile.log and obexscan.log do not and we wondered if the current settings on our rsync filter above were correct or how we can change them some ideas thx

---

