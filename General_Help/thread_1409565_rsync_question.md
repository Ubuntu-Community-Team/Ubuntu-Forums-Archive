---
title: "rsync question"
date: 2010-02-17
forum: General Help
---

### Post by sr_guy on 2010-02-17
I've figured out the command to use to copy a dir from one pc and copy it to another over a network.

```

rsync --delete -azvv -e ssh /home/remastersys/remastersys root@192.168.1.2:/home/foo/mythbox

```

The other PC asks for the password, I enter it, and transfer starts. How do I incorporate the password in the command above so it does not ask for the password?

---

### Post by b0b138 on 2010-02-17
Read up on ssh keys  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by LoneWolfJack on 2010-02-17
```
man rsync
```

> --password-file
This option allows you to provide a password in a file for accessing a
remote  rsync  server. Note that this option is only useful when
accessing an rsync server using the built in transport, not when using a
remote shell as the transport. The file must not be world readable. It
should contain just  the  password as a single line. 

---

