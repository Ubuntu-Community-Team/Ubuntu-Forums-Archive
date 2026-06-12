---
title: "Help with symlink"
date: 2011-10-09
forum: General Help
---

### Post by spiky001 on 2011-10-09
I have to have libc.so.6 in lib, I found libc.so.6 in /lib/i386-linux-gnu/libc.so.6 I hope I created a correct symlink  to lib ```
ln -n /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6
```.  The file libc.so.6 now shows in red /lib/[COLOR=Red]libc.so.6[COLOR=Black] I hope this is correct for a symlinked file? Also how do you remove the symlink just incase 

I also created symlink as root 
[/COLOR]
[/COLOR]

---

### Post by matt_symes on 2011-10-09
Hi

> **spiky001 said:**
> I have to have libc.so.6 in lib, I found libc.so.6 in /lib/i386-linux-gnu/libc.so.6 I hope I created a correct symlink  to lib ```
ln -n /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6
```.  The file libc.so.6 now shows in red /lib/[COLOR=Red]libc.so.6[COLOR=Black] I hope this is correct for a symlinked file?
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
I use -s for as symlinked file.

[/COLOR][/COLOR] ```
ln **-s** /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6
```[COLOR=Red][COLOR=Black] 
That is fine for a symlink. That will create  a symlink in [/COLOR][/COLOR] /lib/[COLOR=Red][COLOR=Black]libc.so.6[/COLOR][COLOR=Black] that points to [/COLOR][/COLOR] /lib/i386-linux-gnu/libc.so.6
You can test this with

```
readlink -f /lib/libc.so.6
```[COLOR=Red][COLOR=Black]
> Also how do you remove the symlink just incase [/COLOR][/COLOR]
Delete it using rm.

Kind regards

---

### Post by spiky001 on 2011-10-09
Ok as i created the link as root due to permissions Can I chmod it to the user? if so how?

---

### Post by matt_symes on 2011-10-09
Hi

Just use the standard chown with the -h switch so the symlink does not get dereferenced.

```
sudo chown -h user:user /path/to/symlink
```Kind regards

---

### Post by spiky001 on 2011-10-09
Ok that changed the symlink to the user thks, But my script fails,_here_   . It fails with this```
/home/spiky/bin/version-check.sh: line 22: /lib/libc.so.6: No such file or directory
```. I cant really chown lib directory

---

### Post by matt_symes on 2011-10-09
Hi

Open a terminal and type
[FONT=monospace]
[/FONT]```
ls -l /lib/libc.*

```Post the results back here.

Can you also post your script ?

Kind regards

---

### Post by spiky001 on 2011-10-09
```
lrwxrwxrwx 2 spiky spiky 12 2011-06-19 16:11 /lib/libc.so.6 -> libc-2.13.so
```

[http://www.linuxfromscratch.org/lfs/view/7.0-rc1/prologue/hostreqs.html](http://www.linuxfromscratch.org/lfs/view/7.0-rc1/prologue/hostreqs.html)

---

### Post by matt_symes on 2011-10-09
Hi 

LFS eh ? I hope you have plenty of coffee ;)

> **spiky001 said:**
> ```
lrwxrwxrwx 2 spiky spiky 12 2011-06-19 16:11 /lib/libc.so.6 -> libc-2.13.so
```

Did you create the link with the -n switch or the -s switch ? 

ie ln -n or ln -s ?

Looks like you did not use the -s option. Try it with that.
Here is mine
```

matthew@matthew-laptop:~$ ls -l /lib/libc.*
lrwxrwxrwx 1 root root 14 2011-05-24 13:59 /lib/libc.so.6 -> libc-2.11.1.so
matthew@matthew-laptop:~$ 
```My link is owned by root though.

Kind regards

---

### Post by spiky001 on 2011-10-09
I used the n switch, When i run the script I get the failure  /lib/libc.so.6: No such file or directory

---

### Post by matt_symes on 2011-10-09
Hi

> When i run the script I get the failure  /lib/libc.so.6: No such file or directory

I don't quite get that. I assume it's the -n switch but..

What do you get if you open a terminal and type

```
/lib/libc.so.6 --version
```

and 

```
readlink -f /lib/libc.so.6
```

Kind regards

---

### Post by spiky001 on 2011-10-09
ok output /lib/libc.so.6 --version  command not found also run as root

readlink -f /lib/libc.so.6
returns
/lib/libc-2.13.so

---

### Post by spiky001 on 2011-10-09
I,ll pop back tomorrow thks for your help

---

### Post by matt_symes on 2011-10-09
Hi

> **spiky001 said:**
> ok output /lib/libc.so.6 --version  command not found also run as root

readlink -f /lib/libc.so.6
returns
/lib/libc-2.13.so

I'm not quite sure why you are getting what you are getting. It's late here so it's quite possible my brain has stopped working for the night though.

```

matthew@matthew-laptop:~$ /lib/libc.so.6 --version
GNU C Library (Ubuntu EGLIBC 2.11.1-0ubuntu7.8) stable release version 2.11.1, by Roland McGrath et al.
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.4.3.
Compiled on a Linux >>2.6.24-27-server<< system on 2011-01-21.
Available extensions:
        crypt add-on version 2.1 by Michael Glad and others
        GNU Libidn by Simon Josefsson
        Native POSIX Threads Library by Ulrich Drepper et al
        BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.debian.org/Bugs/>.
matthew@matthew-laptop:~$ readlink -f /lib/libc.so.6 
/lib/libc-2.11.1.so
matthew@matthew-laptop:~$
```Let's have a look at what it is pointing to. What's the output of

```
ls -l /lib/libc-2.13.so
```Kind regards

---

### Post by spiky001 on 2011-10-10
```
spiky@spiky-toshiba:~$ /lib/libc.so.6 --version
bash: /lib/libc.so.6: No such file or directory
spiky@spiky-toshiba:~$ readlink -f /lib/libc.so.6
/lib/libc-2.13.so
```[FONT=monospace]ls -l /lib/libc-2.13.so[/FONT]
```
spiky@spiky-toshiba:~$ ls -l /lib/libc-2.13.so
ls: cannot access /lib/libc-2.13.so: No such file or directory
spiky@spiky-toshiba:~$ sudo ls -l /lib/libc-2.13.so
[sudo] password for spiky: 
ls: cannot access /lib/libc-2.13.so: No such file or directory
spiky@spiky-toshiba:~$
```cd /lib && ls | less just what we need.


```
ld-linux.so.2
libatasmart.so.4
libatasmart.so.4.0.3
libatm.so.1
libatm.so.1.0.0
libbrlapi.so.0.5
libbrlapi.so.0.5.5
libbsd.so.0
libbsd.so.0.2.0
libbz2.so.1
libbz2.so.1.0
libbz2.so.1.0.4
libcap.so.2
libcap.so.2.20
libcrypto.so.0.9.8
_**libc.so.6**_
libdevmapper-event.so.1.02.1

```ls of i386-linux-gnu

```
ld-2.13.so
ld-linux.so.2
libacl.so.1
libacl.so.1.1.0
libanl-2.13.so
libanl.so.1
libattr.so.1
libattr.so.1.1.0
libblkid.so.1
libblkid.so.1.1.0
libBrokenLocale-2.13.so
libBrokenLocale.so.1
_**libc-2.13.so**_
libcidn-2.13.so
libcidn.so.1
libcom_err.so.2
libcom_err.so.2.1
libcrypt-2.13.so
libcrypt.so.1
_**libc.so.6**_
libdbus-1.so.3
libdbus-1.so.3.5.4
libdl-2.13.so
libdl.so.2
```ls -l /lib/libc.so.6```
spiky@spiky-toshiba:/lib$ ls -l libc.so.6
lrwxrwxrwx 2 spiky spiky 12 2011-06-19 16:11 libc.so.6 -> libc-2.13.so
spiky@spiky-toshiba:/lib$
```ls -l /
```
drwxr-xr-x  19 root root  4096 2011-10-09 18:53 lib
```

I think I,ve covered it all here

---

### Post by matt_symes on 2011-10-10
Hi

> I think I,ve covered it all here
:D

```
spiky@spiky-toshiba:~$ readlink -f /lib/libc.so.6 
/lib/libc-2.13.so
```and
[FONT=monospace]
[/FONT]```
[FONT=monospace]spiky@spiky-toshiba:~$ ls -l /lib/libc-2.13.so 
ls: cannot access /lib/libc-2.13.so: No such file or directory
[/FONT]
```[FONT=monospace]Now we are getting somewhere. The symlink ([/FONT]/lib/libc.so.6)[FONT=monospace] is pointing to a file ([/FONT]/lib/libc-2.13.so) [FONT=monospace]that does not exist.

The symlink needs to point to

[/FONT]> /lib/i386-linux-gnu/libc-2.13.soOpen a terminal and type

```
sudo rm /lib/libc.so.6
```This will remove the link. Then type

```
sudo ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6
```You are using Natty. I don't believe the link /lib/libc.so.6 is used on Natty. **Deleting the link would break Maverick and Lucid and would have to be repaired from a live CD/USB by recreating the symlink.**

Check the link after by typing
[FONT=monospace]
[/FONT]```
/lib/libc.so.6 --version
```Kind regards

---

### Post by spiky001 on 2011-10-10
Thks for your time and effort now the script runs clean

---

