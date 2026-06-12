---
title: "Catch-22 Gnome PPP GCC Compiler Problem"
date: 2006-01-23
forum: General Help
---

### Post by gigi1234 on 2006-01-23
Hi All,

I am new to Linux/Ubuntu. I really love this distro but it is confusing to me. It seems like you have to have an internet connection get the repositories, packages, updates, etc.  But what do you do if you DON'T have an ethernet connection, only a dialup? I am not a programmer and know nothing about writing my own scripts, etc. 

I want to compile Gnome PPP and have the package but when I try to configure I get an error saying that the compiler cannot create executables. I tried to add all the compilers (GCC) via Synaptic. But I still get the error message. 

All the other distros I have tried include compilers, make, etc. by default. I am confused by Ubuntu. What do I need to do to have the necessary files to compile from source??? 

I am a relative newbie, be gentle and specific. Love in advance!
Gigi

---

### Post by az on 2006-01-24
The toolchain is available on the cd.  Install build-essential and you are good to go.


Be sure that you have all the develomental packages installed, too.  Like libgtk2.0-dev and such.  Any library you need to use with something you compile probably has the header files for compilation in a seperate -dev package.

I don't think all the -dev packages you need are on the cd.  You an install gnome-ppp from universe....

---

### Post by gigi1234 on 2006-01-24
Hmmm...okay. I did install build_essential but now I am getting a message that I am missing a perl parser or something. Does it matter what directory I run the install from? This is something I find really confusing about LINUX- nobody ever tells you where to start a process. I guess it is assumed that everyone knows these details but it can be confusing. Thanks!

---

### Post by az on 2006-01-24
Well, it is not always user-friendly to compile something.  That's why there are linux distributions, where everything is compiled for you.  In this case, gnome-ppp is in the universe repository.

You will need to read the readme included in the tarball to see what the requirements are for compileing gnome-ppp.  I would assume the necessary perl development packages are available on the cd.

---

