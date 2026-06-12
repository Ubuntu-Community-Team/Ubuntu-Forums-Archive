---
title: "login won't work"
date: 2009-09-18
forum: General Help
---

### Post by genshu on 2009-09-18
Hi!
I just installed XUbuntu (and after that Ubuntu, same issue) on my Acer Aspire Notebook via Wubi. The installation itself worked fine. Except when it came to the login of the finished installation:
I entered the same (and I mean I really entered the same) login information as I entered in the beginning of the installation - on the Wubi GUI in Windows. But it just didn't work. I also tried "abc" for both login and passwd but it just didn't work.

I really need Ubuntu on that notebook. Can anyone help? Maybe it's a known issue??
:confused:

---

### Post by rocket16 on 2009-09-18
Did you use Uppercase letterings?

---

### Post by rocket16 on 2009-09-18
If you really do not get the access, then follow this:
1. While Loading Ubuntu at the beginning. press ESC for the Grub Menu.
2. Select the recovery Option, and press e to edit the GRUB
3.Now, go to the second line in the new menu (the line containing "Kernel")
4. Now, select e to edit it
5. Replace "single ro" with "single rw init=/bin/bash"
6. Now, press Enter and then press b
7. A terminal will come. There, you are root. Now, type passwd "your account name" and then enter the new password and confirm it. If still it is not done, then use "adduser" command to create a new user (adduser username). Now, type passwd username and enter password.
8. Next, restart the machine, and login with new password.
(Remember this is a hack. So, please do not try it on Computers in which you are not authorised).

---

