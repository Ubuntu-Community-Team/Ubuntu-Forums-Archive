---
title: "Help with Executable command"
date: 2010-08-24
forum: General Help
---

### Post by Alan Morgan on 2010-08-24
Hello all,

I am having trouble with setting Executable parameter on a couple files.  I am trying to install perforce on my Ubuntu installation.

I did this "sudo chmod +x p4"

then ran:   p4 -v

and I get this error: 

--bash /usr/local/bin/p4: No Such file or Directory

Same result if I run with sudo

sudo p4 -v

Any ideas?

Thanks in advance,

A

---

### Post by shazbut on 2010-08-24
try ./p4

---

### Post by Alan Morgan on 2010-08-24
> **shazbut said:**
> try ./p4

Hiya shaz,

When I do that I get a "command not found.

I even followed these steps:


[LIST=1]
[*]Integrate the Perforce control script into the boot process.   sudo update-rc.d perforce defaults
[*]Goto your home directory then use the control script to start the Perforce server.   cd ~
  sudo /etc/init.d/perforce start
[*]Use the control script to restart the Perforce server.   sudo /etc/init.d/perforce restart
[/LIST]
And, get a command not found.

Thoughts?

A

---

### Post by Alan Morgan on 2010-08-26
Is there any other reason why a "no such file or directory" error would happen?

A

> **shazbut said:**
> try ./p4

---

### Post by Vaphell on 2010-08-26
is p4 listed when you do ls -l?

---

### Post by Alan Morgan on 2010-08-26
Yes, both p4 and p4d are.  I even did a check on permissions.  

Any thoughts?

Flap

> **Vaphell said:**
> is p4 listed when you do ls -l?

---

### Post by Vaphell on 2010-08-26
./p4 should work if it's in the current directory, wth?

paste output of **./p4** and **ls -l p4***

---

### Post by Alan Morgan on 2010-08-26
Thanks for helping.   Here is what happens:

> perforce@3P-Server:/usr/local/bin$ ./p4
-bash: ./p4: No such file or directory
perforce@3P-Server:/usr/local/bin$ sudo ./p4
sudo: unable to execute ./p4: No such file or directory
perforce@3P-Server:/usr/local/bin$


perforce@3P-Server:/usr/local/bin$ ls -l p4*
-rwxrwxrwx 1 userftp userftp  755814 Aug 26 16:43 p4
-rwxrwxrwx 1 userftp userftp 2078284 Aug 26 16:43 p4d

Ideas?

Thanks in advance,

A


> **Vaphell said:**
> ./p4 should work if it's in the current directory, wth?

paste output of **./p4** and **ls -l p4***

---

### Post by Vaphell on 2010-08-26
file p4
maybe incorrect architecture?

[https://bbs.archlinux.org/viewtopic.php?id=94549](https://bbs.archlinux.org/viewtopic.php?id=94549)

---

### Post by Alan Morgan on 2010-08-26
Hi,

Well, I ran the file command and this what I get:

perforce@3P-Server:/usr/local/bin$ ls
p4  p4d
perforce@3P-Server:/usr/local/bin$ file p4
p4: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
perforce@3P-Server:/usr/local/bin$ file p4d
p4d: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
perforce@3P-Server:/usr/local/bin$

Any idea what I might be missing in libraries?

A

PS.  I went into the rc file and edited the top line to #!/bin/bash -e

When I ran the rc I got this:


perforce@3P-Server:/etc/init.d$ sudo update-rc.d perforce defaults
update-rc.d: warning: /etc/init.d/perforce missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System startup links for /etc/init.d/perforce already exist.
perforce@3P-Server:/etc/init.d$

Then:


perforce@3P-Server:~$ sudo: /etc/init.d/perforce: command not found
-bash: sudo:: command not found



> **Vaphell said:**
> file p4
maybe incorrect architecture?

[https://bbs.archlinux.org/viewtopic.php?id=94549](https://bbs.archlinux.org/viewtopic.php?id=94549)

---

### Post by Alan Morgan on 2010-08-26
Welll.....this is embarrassing.

I figured out I was using the 32bit Perforce instead of 64 bit.   Now I can start.  I just need to do some clean-up.

Thanks for your help.

A

---

### Post by Alan Morgan on 2010-08-27
Well, here is where I am with this now.

When I run it directly from the folder (/usr/local/bin/)  I get a Bus Error.

When I try to start the server I get a --Bash no file or directory error.

Any thoughts?

---

