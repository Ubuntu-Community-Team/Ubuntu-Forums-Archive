---
title: "Lost password.  Any hope?"
date: 2006-06-09
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-09
Ok.  I no longer no the password on my main account.  Can I recover the data that's on it or am I going to have to hunt for everything again?

..At least Windows had that "security question"

-ben

---

### Post by elamericano on 2006-06-09
Just boot into recovery mode. Then type, "passwd your_account_name"

That will set the password for that account. Then reboot.

---

### Post by jonibo on 2006-06-09
If you can log in as root, do so and then enter the following command at a command line:
1)  passwd USER
where USER is your account name.

BUT... I am assuming your root account is tied to your main account via sudo, so you might have to do the following.

Put the live CD in your computer and reboot... you'll get a live session.  Open a terminal.
Enter the following commands:

1)  mount /dev/hdaX /mnt
Replace X with the partition number of your root partition.

2)  mount -t proc proc /mnt/proc
3)  mount -t sysfs sysfs /mnt/sys
4)  cd /mnt
5)  chroot  .   /bin/bash
6)  passwd USER
Replace USER with the name of your user account
Give yourself a new password, reboot... remove the CD and hopefully you can log in.

---

### Post by jaapd on 2006-06-09
The password is simply in a file:
[http://ubuntuforums.org/showthread.php?t=143334](http://ubuntuforums.org/showthread.php?t=143334)

---

### Post by jongkind on 2006-06-09
[QUOTE=jaapd]The password is simply in a file:
[http://ubuntuforums.org/showthread.php?t=143334](http://ubuntuforums.org/showthread.php?t=143334)[/QUOTE]


Did you recently open that file? From what ths was a bug which is corrected now.

---

### Post by elamericano on 2006-06-09
[QUOTE=jaapd]The password is simply in a file:
[http://ubuntuforums.org/showthread.php?t=143334](http://ubuntuforums.org/showthread.php?t=143334)[/QUOTE]
Come on, Dapper's out now. Let's all forget that titanic installer bug. Besides, if he got the updates that file should be cleaned. In other words, you're not helping.

---

