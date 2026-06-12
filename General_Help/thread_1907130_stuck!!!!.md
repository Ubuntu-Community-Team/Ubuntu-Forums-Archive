---
title: "stuck!!!!"
date: 2012-01-10
forum: General Help
---

### Post by wingnut2626 on 2012-01-10
i recently typed the command "sudo chmod 700 /" like a dingbat.  now i have no sudo or su command.  can anyone help and tell me what i need to do to restore the permissions?  also since running that command my wifi isnt connecting. is that related to the  chmod thing?  help please!!!!

---

### Post by sisco311 on 2012-01-10
Boot into recovery mode and restore the permissions:
```
chmod 0755 /
```

---

### Post by wingnut2626 on 2012-01-10
How do I boot into recovery mode?  10.04

---

### Post by sisco311 on 2012-01-10
Reboot the computer. During the boot process hold down the **Shift** key. When the Grub menu appears highlight the "recovery mode" option and press Enter. Wait for all the boot processes to finish, then select the "Drop to root shell" option.

---

### Post by wingnut2626 on 2012-01-11
Thank you so much!   Resolved my issue and got wifi connected too!  I guess the only way to learn is to cause mistakes sometimes.  Thanks again!

---

### Post by spacecheck on 2012-01-11
> **wingnut2626 said:**
> Thank you so much!   Resolved my issue and got wifi connected too!  I guess the only way to learn is to cause mistakes sometimes.  Thanks again!
Great! Be sure to use the thread tools to mark the thread Solved.

Have fun!

---

