---
title: "setfacl not working"
date: 2010-11-02
forum: General Help
---

### Post by Manu S S on 2010-11-02
Hi,

Inorder to enable File ACLs, I have modified /etc/fstab to have rw,acl instead of defaults alone and rebooted the system.
When I type 'mount' it shows that the file system has rw,acl.

But when I try to apply the setfacl command to existing directories it is showing the error "Operation not supported".
It works fine when I create a new directory or file and apply setfacl to it.

Thanks in advance.
Manu

---

