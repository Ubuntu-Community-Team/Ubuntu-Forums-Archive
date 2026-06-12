---
title: "NTFS Configuration Tool does not work"
date: 2011-11-21
forum: General Help
---

### Post by cancer10in on 2011-11-21
Hi

I am on Ubuntu 11.04 and installed NTFS Configuration Tool from the package manager. When I try to launch NTFS Configuration Tool from System > Administration. It prompts for the system password and disappears after the password is provided. 

Is anyone facing the same issue? Is there a fix for this?

---

### Post by dino99 on 2011-11-21
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Bucky Ball on 2011-11-21
Maybe try NTFS-3g unless that is what the default configuration tool is supposed to use ...

---

### Post by cancer10in on 2011-11-21
Hi

Thanks for the replies. I think I found the fix. I installed hal using teh following command and it worked like a charm

```
 sudo apt-get install hal
```


Though I am not sure what hal is and what did it do to fix it :(

---

