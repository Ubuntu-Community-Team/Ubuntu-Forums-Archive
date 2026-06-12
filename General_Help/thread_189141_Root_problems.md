---
title: "Root problems"
date: 2006-06-04
forum: General Help
---

### Post by sweeper on 2006-06-04
I am trying to install turboprint, I get this happening

stonerat@ubuntu:~/Desktop$ cd turboprint-1.94-3
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ ./setup
ERROR:
xtpsetup must be run in root mode
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ sudo -i
root@ubuntu:~# cd Desktop
root@ubuntu:~/Desktop# cd turboprint-1.94-3
-bash: cd: turboprint-1.94-3: No such file or directory
root@ubuntu:~/Desktop#
 

When I go to root mode it tells me there is no such directory, when not in root mode it can find the directory?


Duh, sudo!

Problem solved.

---

### Post by ycng76 on 2006-06-04
[QUOTE=sweeper]I am trying to install turboprint, I get this happening

stonerat@ubuntu:~/Desktop$ cd turboprint-1.94-3
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ ./setup
ERROR:
xtpsetup must be run in root mode
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ sudo -i
root@ubuntu:~# cd Desktop
root@ubuntu:~/Desktop# cd turboprint-1.94-3
-bash: cd: turboprint-1.94-3: No such file or directory
root@ubuntu:~/Desktop#
 

When I go to root mode it tells me there is no such directory, when not in root mode it can find the directory?


Duh, sudo!

Problem solved.[/QUOTE]
what do you mean by when you sudo you can't locate the directory??
try to do a su - instead.

---

### Post by Skye on 2006-06-04
I think i see what's happening.  When you're logged in as a normal user, you're in your normal user's home directory, which appears to you as ~.  Quoting from the sudo man page:
[quote=sudo Man page] The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the user that the command is being run as. The command name argument given to the shell begins with a - to tell the shell to run as a login shell.  sudo attempts to change to that user’s home directory before running the shell.  It also initializes the environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, and unsetting all other environment variables.  Note that because the shell to use is determined before the sudoers file is parsed, a runas_default setting in sudoers will specify the user to run the shell as but will not affect which shell is actually run.[/quote]

But, when you switch users to root, and cd to Desktop, you're really changing to your root user's Desktop.  If you *have* run it as root, try typing the path out absolutely:

```
cd /home/stonerat/Desktop/turboprint-1.94-3
```

But alternatively, (and much easier, IMO) is to just run ```
sudo ./setup
``` while logged in as your normal user and in the turboprint file.  This is how sudo is supposed to be used- there's really no need to use the root user at all.  Read the sudo manual ```
man sudo
``` to get a better idea of sudo's uses and capibilities.

---

### Post by sweeper on 2006-06-05
Yes, all I had to do was sudo ./setup. It was doing -i that caused the problem as you describe.

---

