---
title: "Filezilla fail to connect"
date: 2010-06-09
forum: General Help
---

### Post by SpinningAround on 2010-06-09
I have a server with ubuntu 10.04 running OpenSSH, I'm trying to connect to the server using Filezilla and sftp problem is that it's not working. I can connect using ssh in the terminal and also connect to the server using ubuntu's own connection tool. To make the problem even weirder do I have an other computer also running ubuntu 10.04 desktop that can connect using filezilla.

Users log in to different accounts using a RSA key with password.

EDIT:
Found a solution, Filezilla require Seahorse to know about the RSA key to work correct. For Seahorse to find the RSA key is both the private and the public key required to be in the .ssh folder.

---

