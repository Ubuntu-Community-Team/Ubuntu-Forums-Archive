---
title: "Compiling and executing C/C++"
date: 2010-07-03
forum: General Help
---

### Post by eladna on 2010-07-03
Hello,

I'm new to Linux as a developer and I really want to write a CGI 'Hello World' application (C/C++) in my machine and put it on a Web Hosting service which will run it.

Can I compile a source C/C++ code with GCC/G++ on my machine and run the output executable file on another machine? (considering that they both run Linux x64 bit, but not necessarily the same Linux distribution)

I have the latest version of Ubuntu Server x64 bit 
(which is installed on a computer with an Intel Core2 Quad Q6600 2.40GHz CPU).

Thank you a lot,
Elad

---

### Post by gzarkadas on 2010-07-04
As long as the architecture (which is essentially the core CPU features) is the same, you can definitely do, else the binary .deb packages would not exist :). If you want to execute your binary in another architecture then you will have to cross-compile. 

In your case, the architecture -as you state- is the same, so no need to cross-compile. You have however to ensure that all the libraries needed by your binary executable exist in the target host; else it will not run.

---

