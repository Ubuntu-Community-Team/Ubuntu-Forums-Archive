---
title: "Viewing NTFS partition thru' Ubuntu"
date: 2006-04-02
forum: General Help
---

### Post by Gautam Arjun on 2006-04-02
Hi all,
          My Windows XP partition is mounted on my desktop but when i click on it, I'm told that i do not have enough permission to view this volume and that i need to be root to do this....Can someone guide me as to how to achieve this? - any assistance is appreciated.. Thanks in Advance!

Regards
Gautam

---

### Post by Andrew-buntu on 2006-04-02
Try editing the entry for your windows partition in /etc/fstab.  Set your umask to 002, which will allow total access for the owner and the group that owns the disk.  If that still doesn't cut it, set the umask to 000, which will allow everyone total access to the partition.
If you change your fstab, you'll need to unmount and then mount the partition again for the changes to take effect.
Check out "man mount" at the command line for more options you can set on your partitions.

---

### Post by RoboJ1M on 2006-04-02
I added this to my /etc/fstab
```

/dev/hdb1       /mystuff        ntfs    nls=utf8,umask=0222     0       0

```
J1M.

---

### Post by Gautam Arjun on 2006-04-02
Thanks J1M, 
                   That worked and my Windows Files are Visible! - Yay!! - Now, to only set up beagle and gtkpod and I'll officially be in Linux Heaven :)

Regards,
Gautam

---

