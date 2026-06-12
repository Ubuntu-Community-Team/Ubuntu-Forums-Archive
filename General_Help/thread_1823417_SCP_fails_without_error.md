---
title: "SCP fails without error"
date: 2011-08-12
forum: General Help
---

### Post by job on 2011-08-12
I've been experiencing very strange behavior of SCP for some time: whenever I try to copy a file, the output of SCP contains a bunch of underscores and the file is not copied.

```

$ scp test.txt localhost:~/test/
job@localhost's password: 
 _________________________________________

$ ls ~/test/test.txt
ls: cannot access /home/job/test/test.txt: No such file or directory

```

I'm running Kubuntu 11.04 and here is some more info about my setup:

```

$ ssh -V
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010

$ uname -a
Linux squatpc 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

```

Does anybody have any idea what the problem could be?

**Note:** I also posted this question [here]("http://unix.stackexchange.com/questions/18231/scp-fails-without-error") so if anybody knows what the problem is  and wants to get some reputation on Unix & Linux StackExchange you could also post your answer there :-)

---

### Post by job on 2011-08-12
I just installed the vanilla OpenSSH server version 5.8p1 and scp works with this version.

So, I see three possibilities:
[LIST=1]
[*]A problem with my configuration of sshd. I think this would be strange since I didn't change the defaults.
[*]A bug in the patches applied by Ubuntu.
[*]Something wrong with my setup (e.g. weird combination of installed packages)
[/LIST]
1 and 2 seem unlikely since I guess more people would have this problem then.

Any ideas?

---

### Post by job on 2011-08-12
I ruled out the "bug in the Ubuntu patches" option since compiling the sources obtained from "apt-get source openssh-server" produces an sshd that works. Very strange...

---

### Post by job on 2011-08-12
Ok, I figured out the problem: my .bashrc produced output, even in non-interactive sessions, and this output confused scp...

---

