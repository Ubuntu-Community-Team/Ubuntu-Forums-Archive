---
title: "List of defult packages?"
date: 2006-06-29
forum: General Help
---

### Post by nbx909 on 2006-06-29
Is there a list of all the packages installed in a defult version of ubuntu somewhere?

---

### Post by az on 2006-06-29
[QUOTE=nbx909]Is there a list of all the packages installed in a defult version of ubuntu somewhere?[/QUOTE]
Maybe boot the live cd and run

dpkg -L

The live system is the same as the installed system with a small exception.  You will have to disregard the live-cd packages, since they get removed from the installed system after you install.

---

### Post by nbx909 on 2006-06-29
```
nbx@ubuntu:~$ dpkg -L
dpkg-query: --listfiles needs at least one package name argument

Use --help for help about querying packages;
Use --licence for copyright licence and lack of warranty (GNU GPL).

```
wrong command?

---

### Post by mduran on 2006-06-29
the commands
```

dpkg -l |grep ^ii

```

or
```

dpkg -l |grep ^ii |cut -d' ' -f3

```

or
```

dpkg --get-selections |grep install$

```

or
...

---

### Post by az on 2006-06-30
[QUOTE=nbx909]```
nbx@ubuntu:~$ dpkg -L
dpkg-query: --listfiles needs at least one package name argument

Use --help for help about querying packages;
Use --licence for copyright licence and lack of warranty (GNU GPL).

```
wrong command?[/QUOTE]
Yup.  

dpkg -l


(Little L)  The thing is, I make that mistake every time I do it, too!  (type a big L instead of a little l)


Sorry.

dpkg -L is to list the contents of a package.

---

