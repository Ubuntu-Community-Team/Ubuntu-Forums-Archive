---
title: "Misbehaving python os.system() call"
date: 2009-12-08
forum: General Help
---

### Post by Quantum7 on 2009-12-08
I am noticing a couple bizarre results to os.system() calls. Could somebody confirm similar output? I'm using 9.10 with python 2.6.4

```
$ python -c 'import os; os.system("time echo hi")'
hi
0.00user 0.00system 0:00.00elapsed 0%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+215minor)pagefaults 0swaps
$ time echo hi
hi

real    0m0.000s
user    0m0.000s
sys     0m0.000s
```or

```
$ python -c 'import os; os.system("bash<<<\"echo hi\"")'
sh: Syntax error: redirection unexpected
$ bash<<<"echo hi"
hi
```These both work fine under CentOS and OS X with the same python versions.

If anyone cares to suggest a workaround, I'm actually interested in running scripts like
```
$ ( time command >output 2>errors ; ) 2> timing
```

---

### Post by Brandon Williams on 2009-12-08
The problem is suggested by the output from python.

> **Quantum7 said:**
> ```
$ python -c 'import os; os.system("bash<<<\"echo hi\"")'
sh: Syntax error: redirection unexpected
```

When it runs the os.system method, it uses sh as the shell, which is dash in Ubuntu. It's quite likely to be bash in other versions of Linux. As a result, you can't use bashisms (like <<<) with os.system on Ubuntu. You can only use strict POSIX syntax. You can test whether/how a specific command line will work by starting an instance of sh and running the command there.

```
bash> sh
$ bash <<< "echo hi"
sh: Syntax error: redirection unexpected
$ echo "echo hi" | bash
hi
$ time echo hi
hi
0.00user 0.00system 0:00.00elapsed 133%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+199minor)pagefaults 0swaps
$ echo "time echo hi" | bash
hi

real	0m0.000s
user	0m0.000s
sys	0m0.000s
```

The output format you're used to seeing is from bash's builtin time. The output you're getting from sh via python is from /usr/bin/time, since dash doesn't have a builtin for this functionality.

---

### Post by Quantum7 on 2009-12-08
> **Brandon Williams said:**
> 
When it runs the os.system method, it uses sh as the shell

Thanks for clarifying. This had actually occured to me, but I dismissed it based on
```
$ python -c 'import os; os.system("echo $SHELL")'
/bin/bash
```Apparently sh doesn't overwrite the $SHELL variable, so the value from my login shell (bash) shows through.

Based on this I guess I'd better use one of
```
os.system('bash -c "time echo hi"')
subprocess.Popen("time echo hi",shell=True, executable="bash")
```

---

### Post by lykwydchykyn on 2009-12-09
> **Quantum7 said:**
> Thanks for clarifying. This had actually occured to me, but I dismissed it based on
```
$ python -c 'import os; os.system("echo $SHELL")'
/bin/bash
```Apparently sh doesn't overwrite the $SHELL variable, so the value from my login shell (bash) shows through.


A better way to determine the shell would be:
```

python -c 'import os; os.system("echo $0")'

```
$0 is always going to be the name of the shell executable.

---

