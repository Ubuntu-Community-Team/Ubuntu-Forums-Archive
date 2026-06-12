---
title: "Executable not running even after chmod'ing it ..."
date: 2011-10-29
forum: General Help
---

### Post by ahmadka on 2011-10-29
I am trying to run a BETA precompiled copy of rcracki .. but the problem is when I try to run the executable, it gives an error:

```
root@hosted-by:~/Desktop/rcracki_mt_0.7_beta2_linux_x86_64# ls COPYING INSTALLING.txt charset.txt libcudart.so.2 libstdc++.so.6 rcracki_mt.ini ChangeLog.txt README.txt libcrypto.so.0.9.8 libgcc_s.so.1 rcracki_mt

root@hosted-by:~/Desktop/rcracki_mt_0.7_beta2_linux_x86_64# sudo chmod +rwx rcracki_mt

root@hosted-by:~/Desktop/rcracki_mt_0.7_beta2_linux_x86_64# ./rcracki_mt

bash: ./rcracki_mt: No such file or directory

root@hosted-by:~/Desktop/rcracki_mt_0.7_beta2_linux_x86_64# sudo ./rcracki_mt

sudo: unable to execute ./rcracki_mt: No such file or directory
```

Also, output for ```
ls -ltr
``` is the following:

[IMG]http://i.imgur.com/aPi9y.png[/IMG]

So does anyone have a clue as to why Ubuntu gives this error ? .. I mean the file is right here, so the error doesn't make sense .. ?!

By the way, I'm using Ubuntu 10.04 ..

---

### Post by lisati on 2011-10-29
Thread closed for review: we don't support breaking into other people's networks here.

---

### Post by lisati on 2011-10-29
Thread re-opened after discussion with OP and other staff members.

We can help with the file permissions, but can't help with use of the binary.

---

### Post by ahmadka on 2011-10-30
Thanks for re-opening the thread !

Can someone help me now ?

Here are the outputs for running 'file rcracki_mt' and 'file ./rcracki_mt':

[IMG]http://i.imgur.com/rNsHf.png[/IMG]

---

### Post by dcstar on 2011-10-30
Post:

```
uname -a
```

---

### Post by ahmadka on 2011-10-30
> **dcstar said:**
> Post:

```
uname -a
```

This is the response:

```
Linux hosted-by 2.6.18-274.3.1.el5.028stab094.3 #1 SMP Thu Sep 22 13:24:07 MSD 2011 i686 GNU/Linux
```

---

### Post by dcstar on 2011-10-30
> **ahmadka said:**
> This is the response:

```
Linux hosted-by 2.6.18-274.3.1.el5.028stab094.3 #1 SMP Thu Sep 22 13:24:07 MSD 2011 **i686** GNU/Linux
```

You are trying to run 64-bit programs on 32-bit Linux.

---

### Post by ahmadka on 2011-10-30
Yeah that's what I thought too, but the filename of the archive has 'x86_64' in it, so I'm assuming it runs on both architectures ?

---

### Post by 3rdalbum on 2011-10-30
> **ahmadka said:**
> Yeah that's what I thought too, but the filename of the archive has 'x86_64' in it, so I'm assuming it runs on both architectures ?

No, x86_64 is 64-bit x86; it's to differentiate it from other 64-bit architectures. You can run an x86 binary on an x86_64 system, but not the other way around.

---

