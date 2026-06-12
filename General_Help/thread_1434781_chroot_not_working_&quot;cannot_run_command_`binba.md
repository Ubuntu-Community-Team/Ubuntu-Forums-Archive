---
title: "chroot not working: &quot;cannot run command `/bin/bash': No such file or directory&quot;"
date: 2010-03-20
forum: General Help
---

### Post by Geraba on 2010-03-20
I'm trying to change the root directory to /tmp/somedir using chroot, but even using sudo or su-ing to root I get the message:

```
cannot run command `/bin/bash': No such file or directory
```

I tried copying /bin/bash to /tmp/somedir/, but the same error occurs. What's wrong with my chroot?

---

### Post by yabbadabbadont on 2010-03-20
Please post the exact command you run when trying to chroot.

---

### Post by Geraba on 2010-03-20
```
sudo chroot /tmp/somedir
```or


```
sudo chroot /tmp/somedir bash
```

---

### Post by sisco311 on 2010-03-20
How did you create the chroot environment? 

What's the content of /tmp/somedir?

```
ls /tmp/somedir
```

---

### Post by Geraba on 2010-03-20
I had just created it with "mkdir /tmp/somedir"

Since I copied bash to it, ls /tmp/somedir gives:

bin

and inside it is just bash.

---

### Post by soltanis on 2010-03-20
From the manpage:

```

NAME
       chroot - run command or interactive shell with special root directory

SYNOPSIS
       chroot NEWROOT [COMMAND [ARG]...]
       chroot OPTION

```

Without any command, as you invoked it, chroot attempts to run the shell (/bin/sh) but if that doesn't exist in the target directory, then it won't work out.

If you want to run a specific command in a chroot'ed jail, you should just invoke the command directly instead of trying to meticulously set up an environment within an environment -- much easier that way.

---

### Post by sisco311 on 2010-03-20
> **Geraba said:**
> I had just created it with "mkdir /tmp/somedir"

Since I copied bash to it, ls /tmp/somedir gives:

bin

and inside it is just bash.

The chroot directory must be populated with a minimum set of files.

You can use debootstrap to create a minimal, Ubuntu or Debian, chroot environment: [uhelp]/community/DebootstrapChroot[/uhelp].

---

### Post by Geraba on 2010-03-20
But since I copied bash there, shouldn't it at least run and then give an error about the lack of files?

---

### Post by OK23 on 2012-01-11
Hello,
thread is dead for more than 10 months, but maybe this reply will save someone precioussss time...

For chrooting few things must be done:
[LIST=1]
[*] creation of directory for chroot environment - e.g. */home/chroot*


[*] creation subdirectories proc, dev and lib inside above chroot directory:
```
mkdir /home/chroot/{dev,proc,lib}
```

[*] binding */dev/* and */proc/* directories to this chroot directory:
```
mount --bind /dev/ /home/chroot/dev/
mount --bind /proc/ /home/chroot/proc/

```

[*] copying/link files which will be used in chrooted environment into /home/chroot/ into proper directory - e.g. /bin/bash should be placed in /home/chroot/bin/bash


[*] finding and copying/link library files needed for above files (e.g. /bin/bash) into proper directories, must be used command:
```
ldd /bin/bash
```

[/LIST]

And after all of this you can try to run chroot environment. I hope that I haven't miss anything important. In fact you should try to google for *setting chroot*

At last, but not least: message *cannot run command `/bin/bash': No such file or directory"* is not complete and can be misleading. It should be more complete for example like this: *cannot run command `/bin/bash': No such file,  directory **or library files for this command**"*. 
Without 2 last steps of creating chroot list, /bin/bash in chrooted environment won't run even if bash would be placed in /home/chroot/bin/ directory (without proper libraries).

---

### Post by sisco311 on 2012-01-11
[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

Thread Closed. :)

---

