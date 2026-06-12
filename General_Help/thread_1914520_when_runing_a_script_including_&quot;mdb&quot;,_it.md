---
title: "when runing a script including &quot;mdb&quot;, it stuck there"
date: 2012-01-24
forum: General Help
---

### Post by maggie-bc on 2012-01-24
Hi all,
 
when I ran a script including following sentence, it stoped and stuck there.
 
mdb $(echo 'hostname') return site > __temp.out
 
does anyone know the reason and how to solve it? I already installed the mdbtools.
 
Thanks a lot

---

### Post by maggie-bc on 2012-01-24
BTW, my co-workers could run the same script successfully on his ubuntu machine which doesn't install mdbtools. 
 
ubuntu only complains that "no mdb installed" and ignore this sentence and continue to run.

---

### Post by gordintoronto on 2012-01-24
> **maggie-bc said:**
>  
mdb $(echo 'hostname') return site > __temp.out
 


If you just run that from the command line, without directing the output to a file, what happens? (I'm betting it displays a message and says, "press Enter to continue," or some such.)

---

### Post by maggie-bc on 2012-01-25
Thanks for your reply.
 
when I run " mdb $(echo 'hostname') return site", it gets into Mono Debugger.

---

### Post by maggie-bc on 2012-01-25
I tried to uninstall mdbtools. but after runing "sudo apt-get remove mdbtools", the libmdbtools is still on my machine.
 
if I run "dpkg --list |grep mdb*", the libmdbtools still shows.
 
I run "sudo apt-get remove libmdbtools", but it shows that "package libmdbtools is not installed".
 
I don't why I can't remove it??

---

### Post by directhex on 2012-01-25
> **maggie-bc said:**
> I tried to uninstall mdbtools. but after runing "sudo apt-get remove mdbtools", the libmdbtools is still on my machine.
 
if I run "dpkg --list |grep mdb*", the libmdbtools still shows.
 
I run "sudo apt-get remove libmdbtools", but it shows that "package libmdbtools is not installed".
 
I don't why I can't remove it??

What state exactly does it show?

Installed state is shown as "ii"

Uninstalled packages still show up, usually as "rc" or "un"

---

### Post by maggie-bc on 2012-01-26
> **directhex said:**
> What state exactly does it show?
 
Installed state is shown as "ii"
 
Uninstalled packages still show up, usually as "rc" or "un"
 
It shows "rc".
 
But if it has already been uninstalled/removed, why when I run "mdb $(echo 'hostname') return site", it will get into mono debugger.

---

### Post by directhex on 2012-01-26
> **maggie-bc said:**
> It shows "rc".
 
But if it has already been uninstalled/removed, why when I run "mdb $(echo 'hostname') return site", it will get into mono debugger.

Perhaps because you have the mono-debugger package installed?

That's what mdb is. **M**ono **D**e**B**ugger

---

### Post by gordintoronto on 2012-01-26
mdbtools is tools for Microsoft DataBase, not mono.

What fun, having two packages with similar names.

---

