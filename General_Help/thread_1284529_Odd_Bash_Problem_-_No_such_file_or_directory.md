---
title: "Odd Bash Problem - No such file or directory"
date: 2009-10-06
forum: General Help
---

### Post by smartbei on 2009-10-06
I am trying to run a program (an ELf file), but I am getting No such file or directory when the file clearly exists.

I guess I just do not understand the error:
```

smartbei@smartbei-desktop:~$ ahash
bash: /home/smartbei/bin/ahash: No such file or directory

```
As you can see, it found the file.

Running it directly is no better:
```

smartbei@smartbei-desktop:~$ ~/bin/ahash
bash: /home/smartbei/bin/ahash: No such file or directory

```

Any help? Thanks!

---

### Post by t0p on 2009-10-06
Try it like this:

```
./ahash
```

---

### Post by smartbei on 2009-10-07
That behaves just like the second example from before:
```

smartbei@smartbei-desktop:~/bin$ ls
ahash
smartbei@smartbei-desktop:~/bin$ ./ahash
bash: ./ahash: No such file or directory

```

:-(

---

### Post by geirha on 2009-10-07
If you are on a 64-bit system trying to run a 32-bit binary, you may get such a message, where "No such file or directory" refers to the 32-bit linker not being found.

If I remember correctly, you'll need to install at least the ia32-libs package. Though if you're able to find a 64-bit build of the app, that would be the better option.

---

### Post by smartbei on 2009-10-07
The binary is 32-bit, as is my system :-) - I checked.

---

### Post by DeBOBAHer on 2009-10-07
Try mc. Maybe there using some non latin letters or spaces in name. You can also try to rename it with mc.

---

### Post by geirha on 2009-10-07
Are you sure it's not the program itself that is unable to find a certain file? Try running it through strace.
```
strace ahash 2>&1 | grep '^open'
```

EDIT: Ehrm no, then the error wouldn't have had the bash: prefix.

What's the output of this though?
```
file ~/bin/ahash /bin/bash
```

---

### Post by smartbei on 2009-10-07
Thanks for the replies!

@geirha - here is the output:
```

smartbei@smartbei-desktop:~$ file ~/bin/ahash /bin/bash
/home/smartbei/bin/ahash: ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), dynamically linked (uses shared libs), not stripped
/bin/bash:                ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

Looks like it will work on FreeBSD, and not on Linux. Is there a simple way to get it to work?

@DeBOBAHer: midnight commander didn't change anything. And, I renamed it to all latin characters just in case.

---

### Post by 3rdalbum on 2009-10-07
EDIT: Too late, problem already discovered.

---

### Post by geirha on 2009-10-07
You can run linux binaries on BSD, but I don't think there's an easy way to run BSD binaries on linux (if at all possible) ...

---

