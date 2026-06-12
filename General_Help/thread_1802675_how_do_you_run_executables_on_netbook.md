---
title: "how do you run executables on netbook?"
date: 2011-07-12
forum: General Help
---

### Post by xoron on 2011-07-12
hi i am trying to run an executable file called "q" with ./q but it says

@ubuntu:~/q/l32$ ./q
bash: ./q: No such file or directory

what am i doing wrong?

thanks in advanced :D

---

### Post by mali2297 on 2011-07-12
Are you sure that the file is in the current directory and that it is executable?

Check with
```

ls -l q

```

---

### Post by xoron on 2011-07-12
> **mali2297 said:**
> Are you sure that the file is in the current directory and that it is executable?

Check with
```

ls -l q

```

that gives me...

@ubuntu:~/q/l32$ ls -l
total 352
-rwxr-xr-x 1 myname myname 356547 2011-06-14 17:27 q

it says q so i must be in the right directory right? :s

---

### Post by haqking on 2011-07-12
> **xoron said:**
> that gives me...

@ubuntu:~/q/l32$ ls -l
total 352
-rwxr-xr-x 1 myname myname 356547 2011-06-14 17:27 q

it says q so i must be in the right directory right? :s
  
Edit: Just read the permissions

---

### Post by xoron on 2011-07-12
> **haqking said:**
> use 

sudo ./q

hmm... it doesnt say file not found but it still isnt running the executable :s

@ubuntu:~/q/l32$ sudo ./q
@ubuntu:~/q/l32$

if it help the program im trying to run is the q programming environment by kx systems. [http://kx.com/trialsoftware.php](http://kx.com/trialsoftware.php) the program is only a few kilobytes

---

### Post by nothingspecial on 2011-07-12
> **haqking said:**
> use 

sudo ./q

NO!

[-X

If you look at the permissions, the op is the owner and has permission to execute the file. Don't run stuff you download off the internet as root. That way disaster lies.

@OP

When you do download stuff from the internet it always helps if you reasd the README file, which, if you do, will tell you to make sure q is in your home directory and to run it from it's OS specific directory. In your case that would be

```
cd
./q/l32/q
```

---

### Post by xoron on 2011-07-12
> **nothingspecial said:**
> NO!

[-X

If you look at the permissions, the op is the owner and has permission to execute the file. Don't run stuff you download off the internet as root. That way disaster lies.

@OP

When you do download stuff from the internet it always helps if you reasd the README file, which, if you do, will tell you to make sure q is in your home directory and to run it from it's OS specific directory. In your case that would be

```
cd
./q/l32/q
```

ive read the readme several times and tried the way your suggesting :P ... it gives me:


@ubuntu:~/q/l32$ cd
@ubuntu:~$ ./q/l32/q
bash: ./q/l32/q: No such file or directory

which is weird cos the file is definitely there :s

---

### Post by nothingspecial on 2011-07-12
Just to be sure, thats not an I instead of a little L is it? It works for me

```
ns@netbook\:~$ ./q/l32/q
KDB+ 2.7 2011.06.13 Copyright (C) 1993-2011 Kx Systems
l32/ 2()core 990MB ns netbook 127.0.1.1 PLAY 2011.09.11 

q)
```

There's my q prompt......  :-k

---

### Post by xoron on 2011-07-12
> **nothingspecial said:**
> Just to be sure, thats not an I instead of a little L is it? It works for me

```
ns@netbook\:~$ ./q/l32/q
KDB+ 2.7 2011.06.13 Copyright (C) 1993-2011 Kx Systems
l32/ 2()core 990MB ns netbook 127.0.1.1 PLAY 2011.09.11 

q)
```

There's my q prompt......  :-k

i probably should of said before... i know the commands are right because i have it working on my desktop... but it wont work on my netbook (fresh ubuntu install).

im just really confused as to why it tells me that there no such file or directory when i try to run.

---

### Post by nothingspecial on 2011-07-12
Don't know what to say. We must be both missing something really obvious. Running it on a netbook should make no difference.

---

### Post by xoron on 2011-07-12
> **nothingspecial said:**
> Don't know what to say. We must be both missing something really obvious. Running it on a netbook should make no difference.

yeh... im gonna kick myself when i find out :p... its probably somthing really obvious.

---

### Post by mali2297 on 2011-07-12
Might it be an executable for a 32-bit OS that you are trying to run on a 64-bit Ubuntu or vice versa?

---

### Post by nothingspecial on 2011-07-12
Good point, if your netbook is 64bit try installing ia32-libs

---

### Post by xoron on 2011-07-12
> **nothingspecial said:**
> Good point, if your netbook is 64bit try installing ia32-libs

IT WORKED!! but its weird I had to install ia32-libs because my desktop is also 64-bit.

but THANKS!! :D

---

### Post by nothingspecial on 2011-07-12
Knew it would be simple, thanks mali2297 for pointing out the obvious :D

---

### Post by nothingspecial on 2011-07-12
> **xoron said:**
> but its weird I had to install ia32-libs because my desktop is also 64-bit.



Something you've already installed may have pulled them in already.

---

