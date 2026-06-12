---
title: "Protecting folders"
date: 2011-09-22
forum: General Help
---

### Post by CommuneOfLoon on 2011-09-22
Hi, all.

I'm curious if it is possible in Ubuntu to password protect a given folder? As well, is it possible to make sure that the folder is never accidentally shared on a network?

Thanks.

---

### Post by raja.genupula on 2011-09-22
Hey man
        I know one way , but its not with a password . By using the file permissions we can restrict the access to files from others . please make a look at the link below . 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by bodhi.zazen on 2011-09-22
> **CommuneOfLoon said:**
> Hi, all.

I'm curious if it is possible in Ubuntu to password protect a given folder? As well, is it possible to make sure that the folder is never accidentally shared on a network?

Thanks.

Well, this feature is provided by linux permissions.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Each user should have a unique account and you simply make a file "private" by removing permissions for others.

You can use ACL (Access Control Lists) to extend permissions if you need additional or per user control

If you need more then that, the next step is to use encryption.

---

