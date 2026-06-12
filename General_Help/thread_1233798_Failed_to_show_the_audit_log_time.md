---
title: "Failed to show the audit log time"
date: 2009-08-07
forum: General Help
---

### Post by dummyt on 2009-08-07
Hi all,

Just tried to following this URL for enable the audit log, however i found time showed as "[COLOR=Red]<D0>^P^G<B8>^D[/COLOR]". Anyone know how to solve this problem ? Please help.

[http://www.cyberciti.biz/tips/linux-audit-files-to-see-who-made-changes-to-a-file.html](http://www.cyberciti.biz/tips/linux-audit-files-to-see-who-made-changes-to-a-file.html)

# ausearch -f /mnt/dept/test.txt -i | less
type=PATH msg=audit(Friday, August 07, 2009 [COLOR=Red]<D0>^P^G<B8>^D[/COLOR].534:11) : item=0 name=/mnt/dept/test.txt inode=13 dev=fc:04 mode=file,644 ouid=root ogid=root rdev=00:00

---

