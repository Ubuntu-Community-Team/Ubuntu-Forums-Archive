---
title: "Removed Plymouth and broke system"
date: 2011-02-07
forum: General Help
---

### Post by haiyun211 on 2011-02-07
Hi everyone I was really stupid and uninstalled Plymouth on ubuntu 10.04 and now my system will not start up is there any way to get plymouth back on there I cant get console the only way im on here is running live disc.  

Thanks in advanced.

---

### Post by dcstar on 2011-02-07
> **haiyun211 said:**
> Hi everyone I was really stupid and uninstalled Plymouth on ubuntu 10.04 and now my system will not start up is there any way to get plymouth back on there I cant get console the only way im on here is running live disc.  

Thanks in advanced.

Edit the /boot/grub/grub.cfg file on the hard disk and remove the "splash" option on the Ubuntu boot lines.

Reboot and then reinstall it and then do the following:

```
sudo update-grub
```

---

### Post by haiyun211 on 2011-02-10
Thanks for your reply but when I removed Plymouth it really screwed up that file.  So I just reinstalled. But thanks Anyway.

---

