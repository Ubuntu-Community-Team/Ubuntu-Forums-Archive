---
title: "Install tar.gz"
date: 2011-04-30
forum: General Help
---

### Post by xic816 on 2011-04-30
Just tried the following;

- download x.tar.gz
- extract and move to home folder
- open terminal: 

x@x:~$ cd /home/user/zod_engine
x@x:~/zod_engine$ sudo apt-get build-dep zod_engine
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for zod_engine

Why didn't it work?

---

### Post by WorMzy on 2011-04-30
zod_engine doesn't exist in the repositories, you can't use build-dep for it.

---

### Post by Rich_B_uk on 2011-04-30
So, sorry if I'm stating the obvious or being condescending. Not meaning to do so.

A tar.gz is an archive, nothing more, nothing less. Like a zip file on Windows. So you've downloaded a piece of software and you want to install it. Well, either it's a precompiled binary and you should just be able to execute the app(look for an appropriately named script once extracted), install it (look for the appropriately named script once extracted), or build it from source (look for a make file once extracted).

---

### Post by xic816 on 2011-05-01
> **Rich_B_uk said:**
> So, sorry if I'm stating the obvious or being condescending. Not meaning to do so.

A tar.gz is an archive, nothing more, nothing less. Like a zip file on Windows. So you've downloaded a piece of software and you want to install it. Well, either it's a precompiled binary and you should just be able to execute the app(look for an appropriately named script once extracted), install it (look for the appropriately named script once extracted), or build it from source (look for a make file once extracted).

This is my first time dealing with tar.gz so I dont know what I'm doing :P
I searched for executable files but no response (launchers) so what do I do then? O.o

---

### Post by philipballew on 2011-05-01
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by oldos2er on 2011-05-01
> **xic816 said:**
> This is my first time dealing with tar.gz so I dont know what I'm doing :P
I searched for executable files but no response (launchers) so what do I do then? O.o

Look for a README and/or INSTALL file for instructions. Where did you download the tar.gz from? Many times the site where the file came from will also have links to documentation.

---

### Post by xic816 on 2011-05-01
> **oldos2er said:**
> Look for a README and/or INSTALL file for instructions. Where did you download the tar.gz from? Many times the site where the file came from will also have links to documentation.

Yeah, found it but i didnt manage to install it :P
Also tried looking at youtube for instructions but didnt work,
tried installing it through wine (the windows edition) but didnt work
so i just decided to leave it ^^;

It was from sourceforge /zod engine ([http://sourceforge.net/projects/zod/files/](http://sourceforge.net/projects/zod/files/))

---

### Post by oldos2er on 2011-05-01
Read readme_linux.txt

---

### Post by BigD77 on 2011-05-01
This might be a bit off topic, but I have a question.  I downloaded a backup of my old blog, and it was downloaded as a tar.gz.  If I wanted to expand it and reload the text, what do I use?

---

### Post by WorMzy on 2011-05-01
Who knows. There could be anything inside that archive. You could be using any blogging software. There isn't enough information for us to give you any advice.

---

### Post by BigD77 on 2011-05-03
> **WorMzy said:**
> Who knows. There could be anything inside that archive. You could be using any blogging software. There isn't enough information for us to give you any advice.

I don't know if this would help, but I was using WordPress.  The server was Linux, through Siteocity.com.

---

