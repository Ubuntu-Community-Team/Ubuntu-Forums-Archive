---
title: "how to cp files using ssh?"
date: 2010-01-30
forum: General Help
---

### Post by flyingsliverfin on 2010-01-30
how do i copy files using ssh throught the terminal?

for ex: im on my friends mac, ssh to my computer which has a ssh server running. how do i download a file on the server to the mac through the terminal?

same thing for other way around: mac -> server

---

### Post by cszikszoy on 2010-01-30
use scp.

```
man scp
```

should tell you all you need to know.

---

### Post by flyingsliverfin on 2010-01-30
ill do that soon... after i ssh into the computer and am there, how do i change the local directory (as in the computer im sshing from)?

is there a way to copy the file from within the computer after directly sshing in without using scp

---

### Post by falconindy on 2010-01-31
sshfs is also an option. you could do the following:

```
sshfs user@domain.tld:~/ /path/to/local/mount
```

You'll be prompted for a password (or not, if you're using key authentication), and then the directory specified by the first arg will be mounted at local path specified by the second arg. Gives you the freedom to poke around the remote comp without having to bounce back and forth between ssh and scp.

---

### Post by synapsys on 2010-01-31
> **flyingsliverfin said:**
> ill do that soon... after i ssh into the computer and am there, how do i change the local directory (as in the computer im sshing from)?

is there a way to copy the file from within the computer after directly sshing in without using scp

Open another terminal window.

---

### Post by switch10 on 2010-01-31
```
scp user@192.168.0.0:/home/username/file /home/user/target_dir
```

switch the 192.168.0.0 with the IP of the server.

use scp -r to copy directories

---

### Post by nmaster on 2010-01-31
you can try looking ar rsync too.

---

### Post by flyingsliverfin on 2010-01-31
thx everyone ive figured out a compromise between many ur suggestions :D

---

