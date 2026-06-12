---
title: "Script for un mounting a removable disc?"
date: 2011-02-19
forum: General Help
---

### Post by J697 on 2011-02-19
I am programming something and the device needs to be constantly removed to test it, and if I don't go into 

System
--Administration
--|--Disk Utility
--|--|--Unmount device

Then the data won't copy properley, so is there a script that I can run to quickly un mount a device?

---

### Post by cjhabs on 2011-02-19
> **J697 said:**
> I am programming something and the device needs to be constantly removed to test it, and if I don't go into 

System
--Administration
--|--Disk Utility
--|--|--Unmount device

Then the data won't copy properley, so is there a script that I can run to quickly un mount a device?

sudo umount <mount_point>

for example:
sudo umount /media/music

---

### Post by J697 on 2011-02-20
> **cjhabs said:**
> sudo umount <mount_point>

for example:
sudo umount /media/music

thanks :D

---

### Post by J697 on 2011-02-20
Sorry, double post is the only way to make this thread visible again. Every time I start the script it makes me put in a password via terminal, can I bypass this so it will automatically unmount it without requiring a password?

---

### Post by cjhabs on 2011-02-21
> **J697 said:**
> Sorry, double post is the only way to make this thread visible again. Every time I start the script it makes me put in a password via terminal, can I bypass this so it will automatically unmount it without requiring a password?

You need to edit the sudoers file to do that - there are assorted security risks with that.
See [http://ubuntuforums.org/archive/index.php/t-19236.html](http://ubuntuforums.org/archive/index.php/t-19236.html) for a previous discussion of this topic.

---

