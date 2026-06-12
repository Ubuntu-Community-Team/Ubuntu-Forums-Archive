---
title: "Can't run executable from inside Virtualbox 12.04"
date: 2012-04-29
forum: General Help
---

### Post by dishbert on 2012-04-29
Well this is odd.

I have an executable file that runs fine from Mint 10.04:

chris@chris-linux-downstairs ~ $ ./buds
Opening serial device '/dev/ttyS0' (19200,8N1)...OK
Creating PTY device...OK
Setting PTY device '/dev/pts/1' (115200,8N1)...OK
Startup complete, waiting for commands...

But the same exact file copied to 12.04 in Virtualbox and with the permissions changed to allow it to executed fails:

chris@chris-VirtualBox:~$ cd Test
chris@chris-VirtualBox:~/Test$ ls
buds
chris@chris-VirtualBox:~/Test$ ./buds
bash: ./buds: No such file or directory

I'm baffled!

---

### Post by Bandit on 2012-04-29
And ls list it in that directory?
Try ./full/dir/to/file exp: ./home/bandit/conky_start.sh

---

### Post by dishbert on 2012-04-29
Thanks Bandit.

Like this?

chris@chris-VirtualBox:~$ sudo cp buds /home/chris/Test
[sudo] password for chris: 
chris@chris-VirtualBox:~$ cd Test
chris@chris-VirtualBox:~/Test$ ls
buds
chris@chris-VirtualBox:~/Test$ ./buds
bash: ./buds: No such file or directory
chris@chris-VirtualBox:~/Test$ ./home/chris/Test/buds.sh
bash: ./home/chris/Test/buds.sh: No such file or directory
chris@chris-VirtualBox:~/Test$

---

### Post by dishbert on 2012-04-29
I'll attach a pic to show what it looks like from Nautilus.

---

### Post by dishbert on 2012-05-17
Now I've tried it in Ubunut 10.04 installed in Virtualbox (thinking it might be a 12.04 issue) and still no luck.

chris@chris-vbox:~/test$ ls
buds
chris@chris-vbox:~/test$ ./buds
bash: ./buds: No such file or directory
chris@chris-vbox:~/test$ 

Anyone?

---

### Post by miegiel on 2012-05-17
Try these :
```
/home/chris/test/buds
```
or
```
sh /home/chris/test/buds
```
or (from the *test* directory)
```
sh buds
```
All assuming the file is called *buds* and not *buds.sh*

---

### Post by dishbert on 2012-05-17
Thanks for helping miegiel.

Yes the file is just named buds with no .sh extention.

chris@chris-vbox:~$ cd test
chris@chris-vbox:~/test$ ls
buds
chris@chris-vbox:~/test$ /home/chris/test/buds
bash: /home/chris/test/buds: No such file or directory
chris@chris-vbox:~/test$ sh /home/chris/test/buds
/home/chris/test/buds: 1: Syntax error: word unexpected (expecting ")")
chris@chris-vbox:~/test$ sh buds
buds: 1: Syntax error: word unexpected (expecting ")")
chris@chris-vbox:~/test$

---

### Post by miegiel on 2012-05-18
> **dishbert said:**
> Thanks for helping miegiel.

Yes the file is just named buds with no .sh extention.

chris@chris-vbox:~$ cd test
chris@chris-vbox:~/test$ ls
buds
chris@chris-vbox:~/test$ /home/chris/test/buds
bash: /home/chris/test/buds: No such file or directory
chris@chris-vbox:~/test$ sh /home/chris/test/buds
/home/chris/test/buds: 1: Syntax error: word unexpected (expecting ")")
chris@chris-vbox:~/test$ sh buds
buds: 1: Syntax error: word unexpected (expecting ")")
chris@chris-vbox:~/test$

I think "No such file or directory" refers to a missing file (or path) in the script. If you can't find it post the script here (in a code box please).

```
code box :)
```

---

### Post by dishbert on 2012-05-18
I don't think I can display the code inside this file.

I didn't code it myself, it's a binary file, but it's the same file that runs fine in Mint 10:

chris@chris-linux-downstairs ~/EMU $ ./buds
Opening serial device '/dev/ttyS0' (19200,8N1)...OK
Creating PTY device...OK
Setting PTY device '/dev/pts/2' (115200,8N1)...OK
Startup complete, waiting for commands...

---

### Post by miegiel on 2012-05-18
Then I think it's using (system) paths that are different in ubuntu.

---

### Post by dishbert on 2012-05-18
A new day, and I figured out it was a 32 bit binary trying to run on a 64 bit OS.

chris@chris-vbox:~$ file buds
buds: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

So I installed libc6:i386 and all is fine now.

Thanks for working with me on this miegiel.

---

