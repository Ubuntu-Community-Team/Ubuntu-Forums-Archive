---
title: "Create ISO of just the contents of a hard drive"
date: 2011-05-05
forum: General Help
---

### Post by wweeks on 2011-05-05
I've been using the command  ```
dd if=/dev/sda of=/dev/sdb
```
to copy my hard drives contents completely to another hard drive.
However I need a way to copy just the files on one partition. I don't want the entire partition copied, just the files. I need the code to output them in to an ISO, any on know how to do this? I'd appreciate any help.

---

### Post by jerome1232 on 2011-05-05
Does it need to bee cli? You could simply use brasero to create a cd project and write it to disc (meaning create an ISO).

If you need it to be cli then take a look at the man pages for growisofs or genisoimage. I believe both of them can do what you want.

---

### Post by wweeks on 2011-05-05
Doesn't need to be cli, just needs to be bootable when I'm done.

---

