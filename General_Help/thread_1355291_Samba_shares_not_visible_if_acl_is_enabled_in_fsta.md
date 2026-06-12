---
title: "Samba shares not visible if acl is enabled in fstab ?!"
date: 2009-12-14
forum: General Help
---

### Post by bo190e on 2009-12-14
When I enable extended acls on a mounted filesystem /etc/fstab (option acl), the Samba server disappears from the net when browsing from windows clients. When the filesystem is mounted without the acl option it works again.

The mounted filesystem is where the samba shared directories is located.

I see no error messages in the samba logs, and everything seems to run as expected (seen from the linux side).
Any suggestions on what's going on ?

I'm running Ubuntu server 9.10 + ubuntu-desktop. All the latest updates has been installed.

Thanks in advance 
/Bo

---

