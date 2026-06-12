---
title: "Root system remounted read-only."
date: 2005-01-28
forum: General Help
---

### Post by martijntje on 2005-01-28
This morning my root filesystem remounted read-only, probably because of an error. After a little bit of research, i found out that this is done, because of a line in my /etc/fstab file:
 > /dev/hdh2       /               ext3    defaults,errors=remount-ro 0       1
 
 Since i am on a job-trip right now, i have to depend on the ssh-server to let me do my stuff. However, right now, i can't do anything. Almost anything i try gives me IO-errors. I can't even reboot it.
 
 So, my question is: what can i do about it? Resetting it is not an option, since i'll be home only after a week or three.

---

### Post by rudi on 2005-01-28
Your fstab entry seems ok. You could try to remount fstab using:
 [b]sudo mount -a
 [/b]

---

### Post by martijntje on 2005-01-28
[QUOTE=rudi]Your fstab entry seems ok. You could try to remount fstab using:
 [b]sudo mount -a
 [/b][/QUOTE]
 Thanks, but no thanks:
> $ sudo mount -a
Password:
sudo: Can't open /var/run/sudo/martijntje/1: Read-only file system

I can't run sudo anyways, so i can't solve the problem. Root account is disabled (default ubuntu setting), so i'm pretty much stuck.

---

