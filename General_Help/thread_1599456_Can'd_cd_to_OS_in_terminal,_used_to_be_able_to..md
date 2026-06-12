---
title: "Can'd cd to OS in terminal, used to be able to."
date: 2010-10-17
forum: General Help
---

### Post by Jetso on 2010-10-17
I'm trying to learn commands in Terminal, so I tried to CD to my OS drive, which all my files from Windows are at. I used to be able to ```
cd /media
cd OS
ls
```

Then all my files show up. Now I can't even when I use the command history to execute the exact same commands. I can see them when I got to places, like always, but not in terminal. How can I go to see them again?

---

### Post by btindie on 2010-10-17
It's probably that in the past when you've accessed them through the terminal you've first accessed them through nautilus. When you do it will create a directory in /media for that partition and mount it there.

You can manually mount the partitions if you want and add an entry to fstab for it. If you want, provide the output of ```
sudo blkid
```

---

