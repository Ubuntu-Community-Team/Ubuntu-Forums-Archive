---
title: "how to unzip ?"
date: 2012-10-04
forum: General Help
---

### Post by winzip on 2012-10-04
when I  type   ```
unzip  /home/user/myapp.zip
```     I  get  **INVALID COMMAND**  message.

Whats wrong ?  how do I fix it ?

I'm using  Ubuntu Server 10 OS.

---

### Post by doktorOblivion on 2012-10-04
Is unzip installed and the directory in your path.  To check:
```

$ which unzip
/usr/bin/unzip

```

---

### Post by winzip on 2012-10-04
> **doktorOblivion said:**
> Is unzip installed and the directory in your path.  To check:
```

[COLOR=Blue][B]$ which unzip
/usr/bin/unzip[/B][/COLOR]

```

Yes. I get the same as [COLOR=Blue]**BLUE**[/COLOR]

---

### Post by doktorOblivion on 2012-10-04
Have you tried:
```

/usr/bin/unzip <path>/my.zip

```

Also, the following would be interesting:
```

$ unzip -?
UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

```

---

### Post by winzip on 2012-10-04
By the way I'm calling unzip via sftp ....is it a problem ? if so whats the workaround ?

```
sftp>unzip  /home/user/myapp.zip
```

---

### Post by doktorOblivion on 2012-10-04
Yes, I don't think that is supported.  To check, do the following:
```

sftp> ?
Available commands:
bye                                Quit sftp
cd path                            Change remote directory to 'path'
chgrp grp path                     Change group of file 'path' to 'grp'
chmod mode path                    Change permissions of file 'path' to 'mode'
chown own path                     Change owner of file 'path' to 'own'
df [-hi] [path]                    Display statistics for current directory or
                                   filesystem containing 'path'
exit                               Quit sftp
get [-Ppr] remote [local]          Download file
help                               Display this help text
lcd path                           Change local directory to 'path'
lls [ls-options [path]]            Display local directory listing
lmkdir path                        Create local directory
ln [-s] oldpath newpath            Link remote file (-s for symlink)
lpwd                               Print local working directory
ls [-1afhlnrSt] [path]             Display remote directory listing
lumask umask                       Set local umask to 'umask'
mkdir path                         Create remote directory
progress                           Toggle display of progress meter
put [-Ppr] local [remote]          Upload file
pwd                                Display remote working directory
quit                               Quit sftp
rename oldpath newpath             Rename remote file
rm path                            Delete remote file
rmdir path                         Remove remote directory
symlink oldpath newpath            Symlink remote file
version                            Show SFTP version
!command                           Execute 'command' in local shell
!                                  Escape to local shell
?                                  Synonym for help

```
from within your sftp session.  You should just ssh onto the machine to perform the unzip.

---

### Post by windscape on 2012-10-04
Hi,

Based on the output above, it might work if you put ! in front of unzip, like this: ```
!unzip /home/user/myapp.zip
```

---

### Post by doktorOblivion on 2012-10-04
Yes, escaping to local shell should work, but you must use an absolute path to the zip file.

---

### Post by winzip on 2012-10-04
> **windscape said:**
> Hi,

Based on the output above, it might work if you put ! in front of unzip, like this: ```
!unzip /home/user/myapp.zip
```

this does not work

---

### Post by windscape on 2012-10-04
Hi,

What about ```
!/usr/bin/unzip /home/user/myapp.zip
```

---

### Post by doktorOblivion on 2012-10-04
Check your local shell env..!
```

sftp> !echo $PATH

```
It could be the rc file that is getting picked up is not setting the PATH correctly.

---

