---
title: "Apache2 gives &quot;403 Forbidden&quot; error when on external harddrive"
date: 2010-10-05
forum: General Help
---

### Post by IQAndreas on 2010-10-05
My site runs just fine when running from the local harddrive.

However, as soon as I change the directory to a folder on an external NTFS harddrive, I get the "403 Forbidden" error. In addition, I still haven't found any way to properly change the permissions of files on NTFS drives (if that is even possible)

It needs to be on the NTFS drive so that the files are able to be accessed by my Windows installation.

Any way to fix this?

---

### Post by anglican on 2010-10-05
> **IqAndreas said:**
> My site runs just fine when running from the local harddrive.

However, as soon as I change the directory to a folder on an external NTFS harddrive, I get the "403 Forbidden" error. In addition, I still haven't found any way to properly change the permissions of files on NTFS drives (if that is even possible)

It needs to be on the NTFS drive so that the files are able to be accessed by my Windows installation.

Any way to fix this?Are you by any chance sym-linking the external drive into the www directory - and how are you accessing this external drive (is it an smb share or is it attached by usb)? If it is mounted at say /mnt/ntfs-drive try re-mounting it in the html directory (instead of sym-linking):
```
In /etc/fstab something like:
/mnt/ntfs-drive        /var/www/html/ntfs-drive    none    rw,bind 0 0


```These should be helpful errors in /var/log somewhere (I use a different distro for my servers and it would be /var/log/httpd/error.log on mine but ubuntu may be different).

With ntfs there is no way to "fix" permissions/ownership.

H

---

