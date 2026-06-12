---
title: "Automatic Firefox downloads to vfat are size 0"
date: 2006-06-06
forum: General Help
---

### Post by elamericano on 2006-06-06
I set Firefox to save all my downloads to a download folder on my vfat partition (by setting "Save all files to this folder"). The download manager doesn't open. Still the filename is created with filesize 0.

If I set the preference to "Ask me where to save every file", then I can select the same folder, and the download works.

OR

I leave it on automatic, but save to my home directory on the ext2 partition. It works.

My fstab options for the vfat are: defaults,utf8,umask=007,gid=46, and I am in group 46.

I'd like to not have to select the directory every time I download, does anyone have any ideas that my workaround this small bug?

---

### Post by tsb on 2006-06-06
try unmask=000

---

### Post by elamericano on 2006-06-06
No difference. I changed umask=000, then umount -a, mount -a. I checked that the permissions on all files was now 777, and they were, but it still only creates the filename in this configuration - which, I should point out, it still would need write permissions to do.

---

### Post by elamericano on 2006-06-06
No other ideas?

Oh well. It's not a big bug....

---

