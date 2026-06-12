---
title: "Help, synaptic and update manager doesn't work."
date: 2010-01-18
forum: General Help
---

### Post by Nautilus112 on 2010-01-18
This happened completely randomly.  One day, my synaptic and update manager is working fine and the next day, I open one of them and get a error window that doesn't say anything (no details on the error).
So, i tried the terminal, sudo apt-get update, and this message shows:

Reading package lists... Error! 
E: Problem parsing dependency Depends 
E: Error occurred while processing lib&#65533;tartup-notificamion0-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages 
E: The package lists or status file could not be parsed or opened.

Can anyone help?

---

### Post by michy99 on 2010-01-18
Try this:```
sudo rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
sudo apt-get update
```

---

### Post by Nautilus112 on 2010-01-18
Wow, thank you, I don't know what I did by that command, but it works. Thanks.

---

### Post by michy99 on 2010-01-18
There was something messed up in that file. You removed it, which made apt-get download the whole file again when you did the update.

---

