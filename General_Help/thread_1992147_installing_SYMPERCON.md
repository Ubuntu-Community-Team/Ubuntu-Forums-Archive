---
title: "installing SYMPERCON"
date: 2012-05-31
forum: General Help
---

### Post by Nullomore on 2012-05-31
Sorry if I'm not posting in the right place. I wasn't exactly sure where to put this.

I would like to use this program, SYMPERCON, found here ([http://sourceforge.net/projects/sympercon/files/source/](http://sourceforge.net/projects/sympercon/files/source/)). I read the documentation and installed the necessary compiler.

Now in the documentation, it tells me to navigate to the directory /source and type "configure". When I do this, I get the message "configure: command not found". When I peek into the /source directory, I see an item called "configure" and an item called "configure.bat"

I suspect that my mistake is something very basic, but since I'm not terribly good at this, I'm not sure what I'm doing wrong.

Thanks for any help you can give!

---

### Post by steeldriver on 2012-05-31
In Linux, the system searches for executables using an environment variable called PATH. Since the directory you're in is not in PATH you need to tell it that the 'configure' executable is right there in the current directory (.) , i.e.

```
./configure
```

The 'configure.bat' file is probably there for building in MS Windows environments, you can likely ignore that.

---

### Post by Nullomore on 2012-05-31
Thanks for your quick reply!

I tried doing ./configure instead, and I got "if: Malformed file inquiry"

---

### Post by steeldriver on 2012-05-31
Hmm... I had a quick look and it seems like the configure script uses the C-shell (!#/bin/csh)

What csh do you have installed? I don't think csh is installed at all by default 

```
 ./configure
bash: ./configure: /bin/csh: bad interpreter: No such file or directory

```
I installed tsch - after that it configured and built OK

---

### Post by Nullomore on 2012-05-31
PERFECT!! Thank you so much!

I did:

apt-get install tcsh
tcsh ./configure

and it worked!

---

