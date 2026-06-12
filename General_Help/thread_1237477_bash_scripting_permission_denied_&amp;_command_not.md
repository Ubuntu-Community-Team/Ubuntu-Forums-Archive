---
title: "bash scripting: permission denied &amp; command not found errors"
date: 2009-08-11
forum: General Help
---

### Post by newagelink on 2009-08-11
It apparently [does not get simpler than this]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-2.html"). Yet I feel like my computer hates me: see gnome-terminal: ```
daniel@daniel-laptop:~$ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz
daniel@daniel-laptop:~$ gedit hello.sh&
[4] 3964
daniel@daniel-laptop:~$ ls
Desktop      examples.desktop  hello.sh  podcasts  Templates
documents    godorchance       music     programs  videos
en_US.UTF-8  google-earth      pictures  Public
[4]+  Done                    gedit hello.sh
daniel@daniel-laptop:~$ ./hello.sh
bash: ./hello.sh: Permission denied
daniel@daniel-laptop:~$ sudo ./hello.sh
[sudo] password for daniel: 
sudo: ./hello.sh: command not found
``` Why won't it work? And why can't I tab-complete the script names? I can tab-complete "gedit hello.sh" but not "./hello.sh".

---

### Post by Brandon Williams on 2009-08-11
You need to give the script executable permission:
```
$ chmod u+x hello.sh
```

If it's not executable, then it's not a command, and so bash won't consider it a candidate for autocompletion when you try to use it as a command.

---

### Post by ptn107 on 2009-08-11
```

chmod u+x hello.sh   # Mark the file as executable
./hello.sh           # to run it

```

---

### Post by wojox on 2009-08-11
Yes permissions always help and 
```
gksudo gedit hello.sh
```

---

### Post by michy99 on 2009-08-11
> **wojox said:**
> Yes permissions always help and 
```
gksudo gedit hello.sh
```

There's no reason to edit this file as root.

---

