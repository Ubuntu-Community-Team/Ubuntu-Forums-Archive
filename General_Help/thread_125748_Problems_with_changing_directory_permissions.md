---
title: "Problems with changing directory permissions"
date: 2006-02-04
forum: General Help
---

### Post by rikard_grankvist on 2006-02-04
I want to change the permissions for one of my partitions to full access. When browsing in nautilus I have read and execute but not write permissions to hda6. I'm new to ubuntu (used mandriva before), and I can't change the permissions. In mandriva I would do:
```
chmod -R 777 /media/hda6/
```
I've understood you use the sudo command with ubuntu, so I tried prefixing that command with sudo (also added the -v)and entered the password. I see all the files flash by ("changed permissions to rwxrwxrwx for file /media/hda6/foo" etc). But the permissions haven't changed when browsing in nautilus. What am I doing wrong here? I suppose I'm using the wrong command, since it seems to execute correctly.

---

### Post by dcstar on 2006-02-04
[QUOTE=rikard_grankvist]I want to change the permissions for one of my partitions to full access. When browsing in nautilus I have read and execute but not write permissions to hda6. I'm new to ubuntu (used mandriva before), and I can't change the permissions. In mandriva I would do:
```
chmod -R 777 /media/hda6/
```
I've understood you use the sudo command with ubuntu, so I tried prefixing that command with sudo (also added the -v)and entered the password. I see all the files flash by ("changed permissions to rwxrwxrwx for file /media/hda6/foo" etc). But the permissions haven't changed when browsing in nautilus. What am I doing wrong here? I suppose I'm using the wrong command, since it seems to execute correctly.[/QUOTE]
What are the permissions set in your /etc/fstab for accessing this mount?

---

### Post by rikard_grankvist on 2006-02-04
"/dev/hda6       /media/hda6     vfat    defaults        0       0"

---

### Post by rikard_grankvist on 2006-02-04
I looked into fstab and figured it was a default nouser setting that kept me from writing to it. Apparently not... If there's anyone who knows fstab, how can I give all users write permission for a partition?

---

### Post by taurus on 2006-02-04
Something like

/dev/hda6 /media/hda6 vfat defaults,umask=0000  0 0

---

### Post by rikard_grankvist on 2006-02-04
Thanks. Let's see if this works.

---

