---
title: "trouble using the SCP comand."
date: 2011-06-24
forum: General Help
---

### Post by 00Disco on 2011-06-24
Hello everyone,

I am pretty much brand spanking new to this and i am having some issues.  i am trying to transfer a copy of software and settings to a new computer. using Ubuntu 11.04
I am trying to install ubuntu on a new computer from my old computer.  not to sure about what i am doing.  i could use some help.


discoron@00Disco71:~$ scp discorron@ubuntu: /home/discoron/installed-software
ssh: connect to host ubuntu port 22: Connection refused


thank you for any assistance in resolving this issue.

---

### Post by Bachstelze on 2011-06-24
Whatever you want to do, this is probably not the way to do it, so please elaborate. :)

As for the error, you must have the OpenSSH server installed on the remote machine, it's in the package *openssh-server*.

---

