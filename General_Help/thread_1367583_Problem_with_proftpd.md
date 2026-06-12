---
title: "Problem with proftpd"
date: 2009-12-29
forum: General Help
---

### Post by tx8090 on 2009-12-29
Hi,

i installed proftpd on my ubuntu Server (9.04 Jaunty).
I configured it with gproftpd, i added a user with full right to change the /var/etc directory.

But if i connect with a computer to my ftp server, i can see the directory and the files in this directory, but i cant change the files.

Is this happening because the /var/etc directory is a system-directory?#

If yes, how can i access full this directory??

I use a program which has got its config-file in this directory and i would like to change this file on a other computer.


Please help,

thank you very much

Best Regards

---

### Post by gsmanners on 2009-12-29
I don't think using FTP that way is a good idea. For security reasons, you should probably use SSH.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by tx8090 on 2009-12-29
but i _need_ to use FTP, no other choice

---

