---
title: "Need help in recovering encrypted ~/home"
date: 2012-01-03
forum: General Help
---

### Post by ubuntu27 on 2012-01-03
I am trying to recover my files using a Xubuntu Live USB.

According to [this thread]("http://ubuntuforums.org/showthread.php?t=1597246"), I first have to enter ```
ecryptfs-unwrap-passphrase /media/04b67fb1-aafd-4082-aebc-493c509bdbe1/home/.ecryptfs/**YOUR-UserName**/.ecryptfs/wrapped-passphrase
``` into the terminal to get my passphase.

However I get:

```
ubuntu@ubuntu:~$ cryptfs-unwrap-passphase /media/bf9a8f90-c901-41ba-beeb-e81a5a892a77/home/.ecryptfs/ubuntu27/.ecryptfs/wrapped-passphase
cryptfs-unwrap-passphase: command not found
ubuntu@ubuntu:~$ 

```

What should I do?


Thank you in advance. :)

---

### Post by kpuz on 2012-01-03
When I enter that command in my terminal it says:

No command 'cryptfs-unwrap-passphrase' found, did you mean:
 Command 'ecryptfs-unwrap-passphrase' from package 'ecryptfs-utils' (main)
cryptfs-unwrap-passphrase: command not found

---

### Post by ubuntu27 on 2012-01-03
Hey guys! I found a **better** way to recovering your encrypted files [in this site]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html"). 

Problem solved! :popcorn:


From [that page]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html"):

If you find yourself in a situation where you need to recover your Encrypted Home or Encrypted Private directory, simply:

    boot the target system using an Ubuntu 11.04 Desktop LiveCD
    make sure that your target system's hard drive is mounted
    open a terminal
    and run ```
**sudo ecryptfs-recover-private**
```
    follow the prompts
    access your decrypted data and save somewhere else
    you can also launch the graphical file browser with 'sudo nautilus'  and navigate to the temporary directory

---

