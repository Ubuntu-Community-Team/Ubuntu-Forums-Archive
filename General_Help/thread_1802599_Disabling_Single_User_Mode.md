---
title: "Disabling Single User Mode"
date: 2011-07-12
forum: General Help
---

### Post by community on 2011-07-12
I am using Ubuntu 10.10. I want to disable the straight login into root via single user mode during booting.Can anyone help me???

---

### Post by ajgreeny on 2011-07-12
If somebody knows what they are doing, there is no way you can stop this for anyone with physical access to the machine.  You can, however, remove Recovery mode from the grub menu, which may stop many users, by editing /etc/default/grub.

Find the lines
```
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
```and remove the # from the second of the two, and recovery mode will no longer show.

I think you can also set grub to require a password, but I will need to search that out.

Here it is:  [http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by community on 2011-07-16
Thank you.It worked nicely for me.!!!

---

