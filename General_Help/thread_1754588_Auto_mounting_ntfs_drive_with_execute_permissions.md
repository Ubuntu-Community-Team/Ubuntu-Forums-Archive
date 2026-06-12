---
title: "Auto mounting ntfs drive with execute permissions"
date: 2011-05-10
forum: General Help
---

### Post by doriad on 2011-05-10
Current when my NTFS external drive is auto mounted, I can't run any executables from it.

If I unmount it and then manually do:

sudo mkdir /media/portable
sudo ntfs-3g /dev/sdc1 /media/portable

it works fine. Is there a way to make the auto-mount have "full" access so I can run applications from it?

Thanks,

David

---

### Post by aa-hcl on 2011-06-02
Hi,

it appears I have got the same problem and looking for the solution.

I have a ntfs partition for which I need to have "rwx" permissions, while auto-mount in ubuntu 11.04 only gives me "rw-" permissions and I can not change that...

Did you find the solution already?

Many thanks!

---

### Post by aa-hcl on 2011-06-02
> **doriad said:**
> 
If I unmount it and then manually do:

sudo mkdir /media/portable
sudo ntfs-3g /dev/sdc1 /media/portable



Hi,

I just want to confirm that this works for me as well. But I still prefer the auto-mount option!

Many thanks!

---

