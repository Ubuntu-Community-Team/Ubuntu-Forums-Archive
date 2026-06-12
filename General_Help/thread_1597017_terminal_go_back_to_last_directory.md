---
title: "terminal: go back to last directory"
date: 2010-10-14
forum: General Help
---

### Post by l3ecl on 2010-10-14
if i was in /home/user/directory1/directory2/directory3/directory4 and i changed directory to /home/user/,  how do i quickly go back to my previous directory (namely  //home/user/directory1/directory2/directory3/directory4 )

---

### Post by jbrown96 on 2010-10-14
Lookup pushd and popd.

---

### Post by blueridgedog on 2010-10-14
[http://linuxgazette.net/109/marinov.html](http://linuxgazette.net/109/marinov.html)

Basically 

cd --

---

### Post by RedSquirrel on 2010-10-14
> **l3ecl said:**
> if i was in /home/user/directory1/directory2/directory3/directory4 and i changed directory to /home/user/,  how do i quickly go back to my previous directory (namely  //home/user/directory1/directory2/directory3/directory4 )

```
cd -
```will work in that case.

---

