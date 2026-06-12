---
title: "Problem with Password!"
date: 2006-06-05
forum: General Help
---

### Post by txetxubcn on 2006-06-05
Hello from Spain... and sorry but my worst english...

I install ubuntu 6.06 and i put
user:txetxu
password:abc01

when I install and ubuntu login screen appears, I put txetxu and the pwd but It say that's incorrect...
I reinstall ubuntu but It continues happening


Can you help me please?

---

### Post by Ramses de Norre on 2006-06-05
Maybe you had a different keyboard layout when installing? Try booting into recovery mode (you can choose that in the grub menu) and run ```
passwd txetxu
``` to set a new password, then do ```
init 6
``` to reboot and you may be able to log in with the password you just set.

---

### Post by txetxubcn on 2006-06-05
I did it and I reboot and the same thing happens

```

root@txetxu-ubuntu:~# passwd txetxu-ubuntu

```

and ubuntu says that txetxu-ubuntu not an user :mad:

I think that user is txetxu-ubuntu, It is right? but ubuntu says that it is not
:(

Can you help me?

---

### Post by txetxubcn on 2006-06-05
I am searching the user that ubuntu uses but I don't find :(

---

### Post by Maci_01 on 2006-06-09
I have the same problem as txetxubcn.

I entered a username and password but it doesn't seem to be working. When I try to change the pass from the recovery console it tells me "user not found."

Is there anyway that we could create a user from there or enable root login from the console in order to create an account?

---

### Post by Ramses de Norre on 2006-06-09
Can you boot into recovery mode and look at the output of ```
cat /etc/shadow
cat /etc/passwd
``` post it here then.

---

### Post by Ted_Smith on 2006-06-09
Try reading the entries here and see if that helps : 

[http://www.ubuntuforums.org/showthread.php?t=103648&page=2](http://www.ubuntuforums.org/showthread.php?t=103648&page=2)

---

### Post by Maci_01 on 2006-06-09
I entered a command simmiliar to
```
useradd -m -G audio users video sudo gdm cdrom -s /bin/bash fred
passwd joe

```

Logged in as joe at the Gnome Login GUI. Looked at the home folder and the folders were joe and josph. I was entering the wrong name (joseph) into the login. I feel quite stupid.

Thanks for all your help, again. :-)

---

