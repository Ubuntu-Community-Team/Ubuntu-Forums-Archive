---
title: "Premission denied on executing node.js on ssh"
date: 2011-01-25
forum: General Help
---

### Post by Consideration on 2011-01-25
Hi, 
I'm trying to run Node.js on an ssh server where I don't have a super user account. 
I have compiled it and installed it to my home directory on my local computer.
I can successfully launch it from there but after uploading the binary (and include,lib and share folders) to my ssh. I get permission denied even though it says that I have permission to execute.

Terminal output:
```

bash-3.2$ cd opt
bash-3.2$ ls
bin  include  lib  share
bash-3.2$ cd bin
bash-3.2$ ls -l
total 7004
-rwxr-xr-x 1 113426_master 113426 7150893 Jan 25 22:59 node
-rwxr-xr-x 1 113426_master 113426     355 Jan 21 18:18 node-waf
bash-3.2$ node
bash: /storage/content/26/113426/opt/bin/node: Permission denied
bash-3.2$ echo $USER
113426_master

```

---

