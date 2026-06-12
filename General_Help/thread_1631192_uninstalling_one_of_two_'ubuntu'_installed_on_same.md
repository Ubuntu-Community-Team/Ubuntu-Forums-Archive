---
title: "uninstalling one of two 'ubuntu' installed on same system."
date: 2010-11-26
forum: General Help
---

### Post by chinmay3 on 2010-11-26
Hi friends,
 today i accidentally  installed ubuntu twice on same pc which belongs to my friend. also i am unable to login into one of them as i forgot password. i want to uninstall later. is there any possibility to recover password? I am now tri-booting with ubuntu ( with everything working fine) , xp ( giving so much hangs & crashes) & ubuntu ( forgated password)

---

### Post by andrewthomas on 2010-11-26
Chroot into the system that you have forgotten the password and use the passwd command to change the password.

---

### Post by ivarn on 2010-11-26
Go to recovery mode, command prompt and type:
```
sudo passwd username
``` then click enter and type in the new password.

---

### Post by chinmay3 on 2010-11-26
Thanks for that. But what about uninstalling one of them?

---

### Post by dcstar on 2010-11-27
> **chinmay3 said:**
> Thanks for that. But what about uninstalling one of them?

Boot up the Ubuntu that you want to keep, then:
```
sudo dpkg-reconfigure grub-pc
```
and install Grub on the boot sector of your drive.

Then use gparted to remove the Ubuntu partition that is no longer required, then:
```
sudo update-grub
```

---

### Post by WorMzy on 2010-11-27
You don't "uninstall" an operating system. You delete the partition that it lives on. Use a LiveCD and gparted for this task.

---

