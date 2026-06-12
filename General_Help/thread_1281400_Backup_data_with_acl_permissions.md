---
title: "Backup data with acl permissions"
date: 2009-10-03
forum: General Help
---

### Post by megarainman on 2009-10-03
I want to backup every day 200 GB of data with ACL permissions.  I looked for a system that works with hardlinks and so  I started with backintime that at first glance seems to work very nice.  But when I try to restore a file or folder all the acl permissions are gone.

So I guess I need to find something else that support ACL.  I read a lot of good things about rdiff.  But the problem is that the fileserver is based on ubuntu 8 and the backupserver is based on ubuntu 9.  To install the latest version of rdiff on the fileserver i need to upgrade python to >2.6 otherwise the backup won't work.  I could try an apt-get upgrade on the fileserver... but wouldn't that be to risky if you know that there is a whole company who depends on that fileserver?  

It would be nice if some of you could give me some good advice!

---

### Post by StuartN on 2009-10-03
Rsync has the -A or --acls option which is not enabled by default, so I assume Backintime also does not enable acl preservation by default.

---

### Post by megarainman on 2009-10-05
> **StuartN said:**
> Rsync has the -A or --acls option which is not enabled by default, so I assume Backintime also does not enable acl preservation by default.

Thanx, the option of -A was the right solution.

---

