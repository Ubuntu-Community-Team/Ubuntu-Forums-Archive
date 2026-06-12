---
title: "sftp force permissions on upload"
date: 2011-03-17
forum: General Help
---

### Post by wyattisimo on 2011-03-17
I'm running Ubuntu 10.04 LTS

Using sftp, is there any way to force particular file permissions upon upload?  I want the permissions on all files uploaded via sftp to be 664.

I've searched around and cannot find an answer.  Many people ask similar questions and many responses recommend using umask, but as far as I understand it, umask is just a bit mask--it cannot be used to set permissions.

Please help.  Thanks!

---

### Post by Lars Noodén on 2011-03-17
You'll want to set [umask](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Umask_and_Chroot) for the **internal-sftp** subsystem to 0002 or something like that.

---

### Post by wyattisimo on 2011-03-17
> **Lars Noodén said:**
> You'll want to set [umask](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Umask_and_Chroot) for the **internal-sftp** subsystem to 0002 or something like that.

Thanks for the response.  I've played with umask, and it does not do what I need.  I need to *set* specific permission, not just *allow* permissions.  A umask of 0002 simply disables the "other" write bit, so a file with permissions 777 will become 775 on the server.

I need to ensure that all uploaded files have permissions 664 regardless of their permissions before they were uploaded.

---

