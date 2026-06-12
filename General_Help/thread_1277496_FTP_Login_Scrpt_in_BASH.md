---
title: "FTP Login Scrpt in BASH"
date: 2009-09-28
forum: General Help
---

### Post by Argentino on 2009-09-28
Hello,

I am trying to write a script in bash that will log me into my FTP server. I found tons of scripts to push files, but I just want it to log me in.

This is what I got already, but its not asking for User nor Pass:

```
#!/bin/bash

clear

USER="myusername"
PASS="mypass"
FTPSERVER="my.ftp.server"

ftp -n $FTPSERVER
user $USER $PASS

cd /backup

```

What am I doing wrong?

Thanks!

---

### Post by Psycho.mario on 2009-09-28
Do you want the script to ask you for a username/password, or do you want it entered into the script already?

---

### Post by Argentino on 2009-09-28
I would really like it to not ask me, for the script to contain username and pass.

---

### Post by falconindy on 2009-09-28
Use the .netrc file in your home directory. Setup an entry as follows:
```
machine my.ftp.server login myusername password mypass
```
Unless its told not to, FTP looks in this file for a matching hostname when you connect to a site. If it finds a match, it supplies the credentials found.

---

### Post by Slim Odds on 2009-09-28
you might want to look into a program called expect.

It's very good for stuff like this

---

### Post by Giblet5 on 2009-09-28
```
ftp -n -i ftp.x.org << !
user yourusername yourpassword
get ls-lR.Z
quit
!
```

Note: Embedding passwords in scripts can be the short path to an unemployment line.

(ftp -n still reads from stdin... You can redirect stdin via "<< !" and terminate the stdin stream with a trailing "!"...)

---

### Post by Slim Odds on 2009-09-28
> **Giblet5 said:**
> Note: Embedding passwords in scripts can be the short path to an unemployment line.

Well.... since FTP is inherently insecure, it really does not matter. The password is sent in PLAIN TEXT across the network for anyone to see. Hardly matters that it's in a script file.

---

