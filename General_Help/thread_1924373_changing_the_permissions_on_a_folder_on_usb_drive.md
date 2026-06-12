---
title: "changing the permissions on a folder on usb drive"
date: 2012-02-12
forum: General Help
---

### Post by ChemMeister on 2012-02-12
Hi,

I can't change the permissions of a folder on a flsh drive I am typing

```

sudo chmod - R g=rwx myFolder

```

But the permissions remain the same, any ideas why? Thanks

---

### Post by oldos2er on 2012-02-12
The command syntax is wrong, for one thing. What filesystem is the flash drive using? If it's FAT or NTFS, chmod won't work.

Did you intend to use chown instead of chmod? 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ChemMeister on 2012-02-12
> **oldos2er said:**
> The command syntax is wrong, for one thing. What filesystem is the flash drive using? If it's FAT or NTFS, chmod won't work.

Did you intend to use chown instead of chmod? 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Oops I totally forgot about the filesystem,  it is NTFS, so how do ii change the folder permissions then?

---

### Post by oldos2er on 2012-02-12
Check the URL I posted.

---

