---
title: "Issue with udisks mounting script"
date: 2010-10-19
forum: General Help
---

### Post by beastrace91 on 2010-10-19
So I have a small bash script I run at user startup to automount all drives on the system. The only issue is that for some reason when the script mounts an NTFS partition it gives me a "permission denied" error when I go to access it until I unmount and manually remount the ntfs partition. Any idea why it would do this?

Here is my short script ```
#! /bin/sh
for i in $(udisks --enumerate-device-files | grep -v disk | grep -e [0-9]$)
do
  udisks --mount $i
done
```

~Jeff

---

### Post by anarchy404 on 2010-10-19
I'm definitely no expert, but generally when "permission denied" is your output, you need to elevate yourself to root or chmod -700 the script

---

### Post by beastrace91 on 2010-10-19
> **anarchy404 said:**
> I'm definitely no expert, but generally when "permission denied" is your output, you need to elevate yourself to root or chmod -700 the script

You need root to mount ANYTHING. Any since all the drives mount and all but ntfs work fine I do not think it is a permission issue with being root or not (Script is run as root at startup)

~Jeff

---

