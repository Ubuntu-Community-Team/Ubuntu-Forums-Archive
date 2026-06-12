---
title: "Permission error on remote directory mounted with sshfs"
date: 2011-07-12
forum: General Help
---

### Post by hojjat on 2011-07-12
I mounted a remote directory using the following command:

sshfs remote.machine.com:/home/myuser/ ~/remote

and I do have full permission on the files on the remote directory (e.g. I can modify them or delete them when I log into the remote machine using ssh). However, in my locally mounted version, I can't modify the files. I can delete them and paste the new version with no problem, but when I try to overwrite I get a permission error. Any ideas?


PS:Never mind, I found the solution:

sshfs remote.machine.com:/home/myuser/ ~/remote -oworkaround=rename

---

