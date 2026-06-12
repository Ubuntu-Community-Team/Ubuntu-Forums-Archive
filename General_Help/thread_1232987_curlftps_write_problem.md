---
title: "curlftps write problem"
date: 2009-08-06
forum: General Help
---

### Post by sam1948 on 2009-08-06
hello
i'm using curlftps to mount a remote ftp to a local folder
i can read but its making some writing errors or not write at all.

for example lets say /home/ftp is the mount point
typing :
```
#> gedit /home/ftp/new_file 
```
the file is created but can't be save.

copying copy file and folders names but not its internals text

the line i use for mounting is
```

curlftpfs -o direct_io -o umask=777 jon:smith@192.168.1.100 /home/ftp 
```

---

### Post by Disabled20240622 on 2009-10-13
It's a mask, using 000 seems to trick it into giving you 777. I don't know why using no mask gives you 000.

---

### Post by sam1948 on 2009-11-07
hey, I don't need that any more.
but thank anyway

---

