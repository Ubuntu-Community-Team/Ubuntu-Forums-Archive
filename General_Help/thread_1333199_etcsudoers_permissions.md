---
title: "/etc/sudoers permissions"
date: 2009-11-21
forum: General Help
---

### Post by jmilana on 2009-11-21
I somehow corrupted by /etc/sudoers file and when I attempt to correct it I obtain a permission error:
joe@joe-laptop:~$ sudo vi /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440
joe@joe-laptop:~$ sudo chmod 0440 /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440
joe@joe-laptop:~$ sudo chmod -w /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440

can someone walk me through how to change back the permissions on /etc/sudoers?

---

### Post by phillw on 2009-11-21
> **jmilana said:**
> I somehow corrupted by /etc/sudoers file and when I attempt to correct it I obtain a permission error:
joe@joe-laptop:~$ sudo vi /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440
joe@joe-laptop:~$ sudo chmod 0440 /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440
joe@joe-laptop:~$ sudo chmod -w /etc/sudoers 
sudo: /etc/sudoers is mode 0640, should be 0440

can someone walk me through how to change back the permissions on /etc/sudoers?


Ahh.... this is not good. Can I ask why you changed the permissions on the /etc/sudoers file ?

> There's two possible reasons it isn't working. One of the them is probably due to the fact that you screwed the permissions on sudoers so sudo can't work period, meaning "sudo chmod 0440 /etc/sudoers" won't have any effect. This is kind of a chicken and egg problem since the root user is disabled by default in Ubuntu, so once you break sudoers, you've no way to obtain root privileges. The only way to fix this is to boot into the rescue system and fix it from the shell there. This is why it's very, very, VERY important that "visudo" be the only utility that's used to edit the sudoers file. It scans the file before saving to make sure that there aren't any errors that would prevent sudo from working and it also employs file locking while editing it.


As mentioned, it IS possible to fix it - but, have you altered any other permissions ?

[http://ubuntuforums.org/showthread.php?t=237527](http://ubuntuforums.org/showthread.php?t=237527)   has some back ground on the matter
Phill.

---

### Post by sisco311 on 2009-11-21
You have to reboot in recovery mode and restore the file's permissions (0440).

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

You should always use *visudo* to edit the file: [thread=1132821]HowTO: Sudoers Configuration[/thread]

---

