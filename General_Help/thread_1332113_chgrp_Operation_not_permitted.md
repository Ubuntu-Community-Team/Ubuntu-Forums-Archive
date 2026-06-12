---
title: "chgrp Operation not permitted  ?"
date: 2009-11-20
forum: General Help
---

### Post by siddukirk on 2009-11-20
Hello all,

I have created a dir called sample

which has the following user permissions 


$ls -l 
drwxr-xr-x  2 hadoop hadoop  4096 2009-11-20 11:02 sample

but when i try to change the group hadoop to some other existing group 

$chgrp -R friends sample
chgrp: changing group of `sample': Operation not permitted


I know that its achievable through sudo command but y the $user (hadoop)  who created the folder in first place lacks the permission to do so ?

---

### Post by iMisspell on 2009-11-20
how abuot 
```
chown -R hadoop:friends sample
```

---

### Post by Vista1330 on 2011-04-26
> **iMisspell said:**
> how abuot 
```
chown -R hadoop:friends sample
```

This doesn't work.
I would also like to be able to let a non-root or sudo user use the chgrp command (if he or she is the owner of the files).

Any help surely appreciated.

---

