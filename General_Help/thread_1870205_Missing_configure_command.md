---
title: "Missing /configure command"
date: 2011-10-26
forum: General Help
---

### Post by J Hildreth on 2011-10-26
I am absolutely new to Linux, Ubuntu, and all the operations/management related to this OS.  I recently deleted some files related to C++ and gui programming using the package manager and I may have clobbered something I needed to keep unintentionally.  I want to compile a simple "hello world" program using the command line interface (Terminal).  From my web searches I gather that the normal procedure would be something like -  ./configure   make   and make install.  When I attempt to execute the ./configure command I get the following error message.

                                             bash: ./configure: No such file or directory

What I need to know is how to recover the configure application.  Can anyone help me??

Joe

---

### Post by oldos2er on 2011-10-27
> **J Hildreth said:**
>                                        bash: ./configure: No such file or directory

That indicates there's no 'configure' file in the current directory. 'configure' files are usually supplied with source code, not in a package.

Double-check which directory you're in when running ./configure

You'll need to install the package build-essential to compile source code (without knowing which packages you removed it's difficult to say if you'll need to install anything beyond that). See 
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by J Hildreth on 2011-10-27
OldOS2er

      Thanks for the reply.

      First, let me reiterate that I know essentially nothing about the Linux way of doing anything, so don't assume any existing knowledge on my part.  You may not have picked up on the fact that I am writing the source code to the "Hello world" program I am attempting to compile, link, and execute.  From your reply, it seems that I need to create some type of file in addition to the source file in order to get ./configure to work.  Is this correct?

      By the way, build-essential is loaded on my system.

Joe

---

### Post by oldos2er on 2011-10-28
I wouldn't think you'd need to create a ./configure script for a simple Hello World program.

[http://en.wikipedia.org/wiki/Configure_script](http://en.wikipedia.org/wiki/Configure_script)

---

### Post by J Hildreth on 2011-10-30
Oldos2er

OK.  Let's have a go at this starting at the beginning.  Again, please assume I know nothing so specific directions would be appreciated.

Let's assume I have my helloworld source file, named helloworld.cpp, in a directory called a.  What are the steps I need to perform to compile, link, and execute the program?

---

