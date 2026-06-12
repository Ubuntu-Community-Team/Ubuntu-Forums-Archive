---
title: "Compilation errors w/ k3b &amp; bzflag"
date: 2006-01-23
forum: General Help
---

### Post by DDM on 2006-01-23
---EDIT: Fixed! It was a bad set of CFLAGS in /etc/environment that I copied from the *ugh* Gentoo forums---

Hi Ubuntu gurus.

After a recent reformat, I've been having trouble compiling both k3b and bzflag cvs. When I do a ./configure on the k3b source, i get this error:

```
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss a package named similar to libstdc++-dev.
```

note that I have build-essential installed, as well as libstdc++-dev. I attached my config.log to this post.

this is what happens when I run ./configure |grep curses```
configure: WARNING: cstdlib: present but cannot be compiled
configure: WARNING: cstdlib:     check for missing prerequisite headers?
configure: WARNING: cstdlib: see the Autoconf documentation
configure: WARNING: cstdlib:     section "Present But Cannot Be Compiled"
configure: WARNING: cstdlib: proceeding with the preprocessor's result
configure: WARNING: cstdlib: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING: cstdio: present but cannot be compiled
configure: WARNING: cstdio:     check for missing prerequisite headers?
configure: WARNING: cstdio: see the Autoconf documentation
configure: WARNING: cstdio:     section "Present But Cannot Be Compiled"
configure: WARNING: cstdio: proceeding with the preprocessor's result
configure: WARNING: cstdio: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING: cstring: present but cannot be compiled
configure: WARNING: cstring:     check for missing prerequisite headers?
configure: WARNING: cstring: see the Autoconf documentation
configure: WARNING: cstring:     section "Present But Cannot Be Compiled"
configure: WARNING: cstring: proceeding with the preprocessor's result
configure: WARNING: cstring: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING: using an internal c-ares lib.
configure: WARNING: Consider installing an updated library at system level
configure: WARNING: link is http://daniel.haxx.se/projects/c-ares/
checking for working ncurses... no
checking for working curses... no
checking for working PDcurses... no
configure: WARNING: could not find a curses library, will build bzadmin without curses
configure: WARNING: Client build has been requested, but GL is not fully available (missing gl.h)
     ... disabling client generation
     no curses!
```And of course I have libncurses5-dev installed. 

This is driving me nuts, as I've compiled both of these programs many many times without issue. I tried re-installing all of these packages through synaptic, without any results. I have compiled other programs on this current setup, which have seemed to run ok. 

Any help is appreciated. Thanks.

---

### Post by DDM on 2006-01-23
Here's the real config.log attachment, guess it was too big uncompressed.

---

### Post by GeneralZod on 2006-01-23
'Sup, duders? :coal:

As a wild stab in the dark, have you tried

```

apt-get build-dep k3b

```

(or whatever the syntax is)? I'd imagine the build dependencies for the newest K3B/ bzflag don't differ too much from the versions that are in the repositories.

---

### Post by DDM on 2006-01-23
I just tried build-dep for both k3b and bzflag, and all dependencies were already fulfilled. Thanks for your advice though.

---

### Post by GeneralZod on 2006-01-23
Thank *you* for correctly spelling "advice" :)

Well, this is a very odd one indeed - I've just downloaded the 0.12.10 version of k3b from their website, and my ./configure finished fine.

Have you tried making up a simple 5 line C++ program and trying to compile that?

Which version of libstdc++-dev do you have (I have 6.4.0)?

---

### Post by DDM on 2006-01-23
lets see....

Synaptic says I have:

libstdc++5 3.3.6-8ubuntu1
libstdc++6 4.0.1-4ubuntu9
libstdc++6-4.0-dev 4.0.1-4ubuntu9
libstdc++6-dev 3.4.4-6ubuntu8

---

### Post by DDM on 2006-01-23
oh, and I can compile other programs. I'm compiling Gaim CVS and it appears to be working OK. I also tried k3b svn, and it did not compile, same problem.

---

### Post by GeneralZod on 2006-01-23
[QUOTE=DDM]oh, and I can compile other programs. I'm compiling Gaim CVS and it appears to be working OK. I also tried k3b svn, and it did not compile, same problem.[/QUOTE]

gaim is C, not C++, so you should probably try and compile a simple C++ program just to make sure.  Something that makes use of the STL should be a good test.

What's the output of 

```

g++ -v

```
?

---

### Post by DDM on 2006-01-23
here it goes. thanks for your speedy replies:```
g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
```

---

### Post by GeneralZod on 2006-01-23
[QUOTE=DDM]here it goes. thanks for your speedy replies:[/QUOTE]

Goons get preferential treatment :)

Try compiling this file:

[http://etotheipiplusone.com/primediff.cpp](http://etotheipiplusone.com/primediff.cpp)

```

wget http://etotheipiplusone.com/primediff.cpp
g++ primediff.cpp -o primediff

```

---

### Post by DDM on 2006-01-23
How'd you know that I have stairs in my house? Was it my post in sh/sc?

Oh and that program compiled and ran fine.
4652353 & 4652507 have the new largest difference of 154

I feel like I should be paying for this service.

---

### Post by GeneralZod on 2006-01-23
[QUOTE=DDM]How'd you know that I have stairs in my house? Was it my post in sh/sc?
[/QUOTE]

Yep - I am a master Internet Detective :)

[QUOTE=DDM]
I feel like I should be paying for this service.[/QUOTE]

Well, I'm actually completely out of ideas now, I'm afraid :/ If you want, I can make a crappy checkinstall deb of k3b 0.12.10 and send it to you, but this might not be wise as it can screw things up, and doesn't actually solve the root underlying problem.  

You might want to link this thread in your SH/SC post so that no one suggests anything that's been tried already.

---

### Post by DDM on 2006-01-23
I'm mostly concerned with getting this fixed before it happens again at a more crucial time, as I don't really need any of new features in k3b. This is annoying. Thanks alot for your help with troubleshooting.

---

