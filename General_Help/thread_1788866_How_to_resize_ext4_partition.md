---
title: "How to resize ext4 partition"
date: 2011-06-23
forum: General Help
---

### Post by Lucas Malor on 2011-06-23
I created only two partitions, root and /home. I want to resize root to a bigger value. I tried to play a little with parted without result. How can I do it safely?

---

### Post by sanderd17 on 2011-06-23
You cannot edit partitions that are "in use", so you need to load up a live CD.

In the live CD, you can right click a partition in gParted (gnome frontend to parted) and resize it.

---

### Post by Lucas Malor on 2011-06-27
Ok, I've done. After it Ubuntu boots, but I noticed some problems:

1. in Shutdown GUI I can only shutdown, restart or suspend. There's no more hibernate.
2. during boot I see this warning: speech-dispatcher disabled; edit /etc/default/speech-dispatcher

---

### Post by blueridgedog on 2011-06-27
> **Lucas Malor said:**
> Ok, I've done. After it Ubuntu boots, but I noticed some problems:

1. in Shutdown GUI I can only shutdown, restart or suspend. There's no more hibernate.


Do you have more RAM than swap?  Hibernate needs more swap than ram to work.

---

### Post by Lucas Malor on 2011-06-27
No, I have more swap... but I moved the swap partition too.

---

### Post by sanderd17 on 2011-06-27
1. You probably forgot to add the swap partition, can you look into the system monitor and see how much swap you really have?

2. Do you notice any effect? If not I should not care about it, it's only a warning, no error.

---

### Post by Lucas Malor on 2011-06-28
Yes, there was no swap. The problem was I deleted swap partition and recreated it, so I changed its UUID in /etc/fstab .

speech-dispatcher seems to be a speech synthesis technology. It's interesting but I can survive without.

Thank you for the help.

---

