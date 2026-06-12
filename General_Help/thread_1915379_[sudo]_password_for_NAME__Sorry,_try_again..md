---
title: "[sudo] password for NAME:  Sorry, try again."
date: 2012-01-26
forum: General Help
---

### Post by itschaos on 2012-01-26
Hey everyone, New user here.
And I've got a strange problem.

I'm trying to use The Terminal and I keep getting this error "[sudo] password for alex:  Sorry, try again."

I'm typing in the right password because I've used it many times before. This problem all started after updating over 300 updates as I Just installed Ubuntu (11.10) tonight but all was working before the updates.

Command ID Brings up
> uid=1000(alex) gid=1000(alex) groups=1000(alex),4(adm),20(dialout),24(cdrom),46(plugdev),109(nopasswdlogin),116(lpadmin),118(admin),124(sambashare)


and "cat /etc/sudoers" brings up
> cat: /etc/sudoers: Permission denied


I have done google searches but I have found no help :/

Any ideas?:confused:

---

### Post by Rodney9 on 2012-01-26
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by luca616 on 2012-02-05
hi i have the same issue, i upgraded to natty narwhal i i keep getting the same error over and over again. if i do a gksu command it asks for my keyring password and it allows me to access the program. so i know im not typing the password wrong

---

### Post by yetiman64 on 2012-02-05
> **luca616 said:**
> hi i have the same issue, i upgraded to natty narwhal i i keep getting the same error over and over again. if i do a gksu command it asks for my keyring password and it allows me to access the program. so i know im not typing the password wrong

In a terminal (or dash) put in "gconf-editor" (without the quotes). When gconf-editor opens navigate to apps > gksu, and check that the sudo-mode setting is ticked. Not sure if this will fix it, but the fact gksu works and sudo doesn't suggests this setting may have been changed in your install to me. Good luck.

---

### Post by aasdfasdfg on 2012-02-05
> **itschaos said:**
> Hey everyone, New user here.
And I've got a strange problem.

I'm trying to use The Terminal and I keep getting this error "[sudo] password for alex:  Sorry, try again."

I'm typing in the right password because I've used it many times before. This problem all started after updating over 300 updates as I Just installed Ubuntu (11.10) tonight but all was working before the updates.

Command ID Brings up


and "cat /etc/sudoers" brings up


I have done google searches but I have found no help :/

Any ideas?:confused:

Please provide more information. Are you able to log into a graphical desktop, but the issue occurs when you attempt to open a terminal emulator from the desktop?

Or, are you stuck trying to login to a tty?

In the former case, determine whether you are logged in as a user or as a guest. If you are logged in as a user, then I am assuming you typed your password correctly when turning on the computer?

---

