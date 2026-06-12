---
title: "GCC problem"
date: 2009-12-28
forum: General Help
---

### Post by grantbourquehelp on 2009-12-28
Hey guys, so I was just following the directions of my new programming book:

```
2. Now compile, link, and run your program.

$ gcc -o hello hello.c
$ ./hello

Hello World
```

Except, when I try the output command in GCC I get this message:
```
root@grant-vm:/home/grant/dev# gcc -o hello hello.c
gcc: hello.c: No such file or directory
gcc: no input files

```

I'm cd'd into the directory of my hello text file. What am I doing wrong here?

---

### Post by Portmanteaufu on 2009-12-28
Can you please post the output of:

pwd && ls -l

---

### Post by grantbourquehelp on 2009-12-28
> **Portmanteaufu said:**
> Can you please post the output of:

pwd && ls -l

```
root@grant-vm:/home/grant# pwd && ls -l
/home/grant
total 44
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Desktop
drwxr-xr-x 2 grant grant 4096 2009-12-28 13:54 dev
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Documents
drwxr-xr-x 2 grant grant 4096 2009-12-27 23:42 Downloads
-rw-r--r-- 1 grant grant  167 2009-12-27 15:29 examples.desktop
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Music
drwxr-xr-x 2 grant grant 4096 2009-12-27 19:21 Pictures
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Public
drwxr-xr-x 2 grant grant 4096 2009-12-27 23:46 source
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Templates
drwxr-xr-x 2 grant grant 4096 2009-12-27 15:45 Videos

```

```
root@grant-vm:/home/grant/dev# pwd && ls -l
/home/grant/dev
total 8
-rw-r--r-- 1 grant grant 95 2009-12-28 13:54 hello
-rw-r--r-- 1 grant grant 74 2009-12-28 13:54 hey

```

---

### Post by AlexDudko on 2009-12-28
You are trying to compile **hello.c** but you have **hello** source file.

---

### Post by Portmanteaufu on 2009-12-28
Great, thanks. The problem is a very simple one. GCC is looking for a file called "hello.c" that contains the code for the Hello World program. You'll notice that in your dev folder (/home/grant/dev) where you're running gcc, there is no file called "hello.c" -- only a file called "hello" and a file called "hey". If the file called "hello" is the one containing your code, simply run:

mv hello hello.c

to rename it. Then re-run the gcc command.

---

### Post by grantbourquehelp on 2009-12-28
Oh, my bad.

When I saw
```
gcc -o hello hello.c
```

I assumed that hello was the file that was going to be outputted to hello.c. But, it's the other way around.

Thanks.

---

### Post by pbrane on 2009-12-28
The **-o** option is what you want to name the output file. gcc will give the compiled file a name of **a.out** by default with that option. And you don't need to be root to compile source, assuming the source is in a directory you have access to. Sometimes you need root access to install source.

---

