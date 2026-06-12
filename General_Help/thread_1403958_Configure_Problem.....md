---
title: "Configure Problem...."
date: 2010-02-10
forum: General Help
---

### Post by dgohn on 2010-02-10
Having problems compiling a program on a new server.  It compiles just fine on Ubuntu 8.0.4 server but a new install of the latest Ubuntu Server edition it throws out a bunch of warnings on configure.  I am assuming I am missing some lib's or something of the sort.  Any ideas of which ones or what I am missing?  Thanks in advance!

```
checking for sys/select.h... yes
checking for sys/types.h... (cached) no
checking for unistd.h... (cached) no
checking for memory.h... (cached) no
checking crypt.h usability... no
checking crypt.h presence... yes
configure: WARNING: crypt.h: present but cannot be compiled
configure: WARNING: crypt.h:     check for missing prerequisite headers?
configure: WARNING: crypt.h: see the Autoconf documentation
configure: WARNING: crypt.h:     section "Present But Cannot Be Compiled"
configure: WARNING: crypt.h: proceeding with the preprocessor's result
configure: WARNING: crypt.h: in the future, the compiler will take precedence
checking for crypt.h... yes
checking assert.h usability... no
checking assert.h presence... yes
configure: WARNING: assert.h: present but cannot be compiled
configure: WARNING: assert.h:     check for missing prerequisite headers?
configure: WARNING: assert.h: see the Autoconf documentation
configure: WARNING: assert.h:     section "Present But Cannot Be Compiled"
configure: WARNING: assert.h: proceeding with the preprocessor's result
configure: WARNING: assert.h: in the future, the compiler will take precedence
checking for assert.h... yes
checking arpa/telnet.h usability... no
checking arpa/telnet.h presence... yes
configure: WARNING: arpa/telnet.h: present but cannot be compiled
configure: WARNING: arpa/telnet.h:     check for missing prerequisite headers?
configure: WARNING: arpa/telnet.h: see the Autoconf documentation
configure: WARNING: arpa/telnet.h:     section "Present But Cannot Be Compiled"
configure: WARNING: arpa/telnet.h: proceeding with the preprocessor's result
configure: WARNING: arpa/telnet.h: in the future, the compiler will take precede                                                                             nce
checking for arpa/telnet.h... yes
checking arpa/inet.h usability... no
checking arpa/inet.h presence... yes
configure: WARNING: arpa/inet.h: present but cannot be compiled
configure: WARNING: arpa/inet.h:     check for missing prerequisite headers?
configure: WARNING: arpa/inet.h: see the Autoconf documentation
configure: WARNING: arpa/inet.h:     section "Present But Cannot Be Compiled"
configure: WARNING: arpa/inet.h: proceeding with the preprocessor's result
configure: WARNING: arpa/inet.h: in the future, the compiler will take precedenc  
```

---

### Post by flippo on 2010-02-10
You seem to be missing some headers.  I'm not familiar with all of them but assert.h is definitely part of libc, which I assume comes standard with Ubuntu, but I'm not sure.  Have you installed build-essential and your kernel headers? If your going to be compiling these are very nice to have around.

---

### Post by dgohn on 2010-02-10
libc6 and libc6-dev are both installed.  I did install build-essential.  How would I go about installing the kernel headers though?  Thanks again

---

### Post by flippo on 2010-02-10
Thats a good question, I haven't done it on ubuntu in a while (I'm mostly on gentoo now, with a server I store data on running ubuntu).  I think something like:

sudo apt-get install linux-headers-`uname -r`

putting `` around anything in a terminal line runs the command, and uname -r gives your kernel version (try it, its very useful).  If that doesn't work look for something like it in synaptic or do a apt-cache search.

Good luck, hope this works.

---

### Post by dgohn on 2010-02-10
Reading state information... Done
linux-headers-2.6.31-19-generic-pae is already the newest version.
linux-headers-2.6.31-19-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Is what was returned.  So I imagine it is already good to go in that aspect.  Any other ideas that might cause a difference between 8.0.4 and the newest server edition?

---

### Post by flippo on 2010-02-10
what does 'locate assert.h' give you?

---

### Post by dgohn on 2010-02-10
dan@server1:~/rasputin/src$ locate assert.h
/usr/include/assert.h
/usr/include/net-snmp/library/snmp_assert.h
/usr/include/php5/ext/standard/php_assert.h

---

### Post by flippo on 2010-02-10
Okay thats what I expected.  Now, I am most likely using a different version of assert.h than you, but my assert.h only includes features.h.  Your warning is complaining about missing pre-req headers, so I'm assuming features.h is your problem.  Can you look at assert.h (/usr/include/assert.h) for a line like #include <somefile.h> and make sure you have somefile.h?

For example, my version of assert.h only includes features.h, so when I run "locate features.h" I see it is in /usr/include/feature.h, which is the expected behavior.

Is this any help?

I'm puzzled by this problem, you seem to be missing a (or a couple) dev library(s), but I have no idea which...

---

### Post by dgohn on 2010-02-10
I also only have features.h as an include


Here is locate features.h

dan@server1:/usr/include$ locate features.h
/usr/include/features.h
/usr/include/ldap_features.h
/usr/include/c++/4.4/parallel/features.h
/usr/share/doc/fetchmail/fetchmail-features.html
/usr/src/linux-headers-2.6.31-19/arch/mips/include/asm/cpu-features.h
/usr/src/linux-headers-2.6.31-19/arch/sh/include/asm/cpu-features.h
/usr/src/linux-headers-2.6.31-19/arch/um/include/asm/required-features.h
/usr/src/linux-headers-2.6.31-19/arch/x86/include/asm/required-features.h
/usr/src/linux-headers-2.6.31-19/include/linux/hdpu_features.h
/usr/src/linux-headers-2.6.31-19/include/xen/features.h
/usr/src/linux-headers-2.6.31-19/include/xen/interface/features.h
/usr/src/linux-headers-2.6.31-19-generic/include/linux/hdpu_features.h
/usr/src/linux-headers-2.6.31-19-generic-pae/include/linux/hdpu_features.h
dan@server1:/usr/include$


I am assuming that there is something higher than simply missing one header file as its happening numerous times.  The output from my ./configure is only a small portion of it.  There is much more just like it.  Thanks for the help thus far and I look forward to solving this issue.

---

### Post by flippo on 2010-02-10
I agree that it looks like all of your headers are there, and your not missing a build dependency.  

I've been looking through some other people having some similar issues, and this may be an issue with the version of autoconf your using, can you revert to the autoconf version you were using on ubuntu 8.04 and try it again, or is that not possible.  I sadly don't remember how to do that with the ubuntu package management tools.

---

### Post by dgohn on 2010-02-10
Ok this part I don't understand...

New server:
```

dan@server1:~/game/cnf$ autoconf --version
Autoconf version 2.13
---
Autoconf 2.13 chosen by Debian wrapper script.
For information and tuning advice see autoconf(1).

```

Old Server:
```
:
/home/fatemud/game# autoconf --version
autoconf (GNU Autoconf) 2.61
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by David J. MacKenzie and Akim Demaille.

```


So the old server has a newer version of autoconf... However...

(New Server):
```

dan@server1:~/game/cnf$ sudo apt-get install autoconf
[sudo] password for dan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
autoconf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any ideas?

---

### Post by sandyd on 2010-02-10
> 
     configure: WARNING: pi.h: present but cannot be compiled
     configure: WARNING: pi.h:     check for missing prerequisite headers?
     configure: WARNING: pi.h: see the Autoconf documentation
     configure: WARNING: pi.h:     section "Present But Cannot Be Compiled"
     configure: WARNING: pi.h: proceeding with the compiler's result
[http://www.gnu.org/software/hello/manual/autoconf/Present-But-Cannot-Be-Compiled.html](http://www.gnu.org/software/hello/manual/autoconf/Present-But-Cannot-Be-Compiled.html)
doesnt matter that it says pi.h instead of whatever yours said.

---

### Post by sandyd on 2010-02-10
> **dgohn said:**
> Ok this part I don't understand...

New server:
```

dan@server1:~/game/cnf$ autoconf --version
Autoconf version 2.13
---
Autoconf 2.13 chosen by Debian wrapper script.
For information and tuning advice see autoconf(1).

```

Old Server:
```
:
/home/fatemud/game# autoconf --version
autoconf (GNU Autoconf) 2.61
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by David J. MacKenzie and Akim Demaille.

```


So the old server has a newer version of autoconf... However...

(New Server):
```

dan@server1:~/game/cnf$ sudo apt-get install autoconf
[sudo] password for dan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
autoconf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any ideas?

did you install any PPAs?

---

### Post by sandyd on 2010-02-10
> **dgohn said:**
> Ok this part I don't understand...

New server:
```

dan@server1:~/game/cnf$ autoconf --version
Autoconf version 2.13
---
Autoconf 2.13 chosen by Debian wrapper script.
For information and tuning advice see autoconf(1).

```

Old Server:
```
:
/home/fatemud/game# autoconf --version
autoconf (GNU Autoconf) 2.61
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by David J. MacKenzie and Akim Demaille.

```


So the old server has a newer version of autoconf... However...

(New Server):
```

dan@server1:~/game/cnf$ sudo apt-get install autoconf
[sudo] password for dan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
autoconf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any ideas?
EDIT: found it.
depending on your version, install one of these. :)
[http://packages.ubuntu.com/search?keywords=autoconf2.13](http://packages.ubuntu.com/search?keywords=autoconf2.13)

which translates to 
```

sudo apt-get install autoconf2.13
```:P

---

### Post by dgohn on 2010-02-10
Please forgive the n00bness but PPA's?

---

### Post by sandyd on 2010-02-10
> **dgohn said:**
> Please forgive the n00bness but PPA's?

NVM about that. see above post.

---

### Post by dgohn on 2010-02-10
So I should install Dapper or one of those listed?

---

### Post by dgohn on 2010-02-10
I had already had autoconf2.13 on the server causing the problems.  The server not causing the issues was running 2.61

Any other ideas?  Thanks again for all of the assistance, greatly appreciated.

---

### Post by flippo on 2010-02-11
I would upgrade Autoconf, I'm not sure how to do that with ubuntu tools, you can always build and install the source yourself, although someone more experienced than me will most likely be able to help you.

---

### Post by dgohn on 2010-02-11
Autoconf upgraded to 2.64.  Same problem still exists.  Completely removed gcc and installed only gcc-4.2 (which was on the server that it works on fine) and still no dice.

Any other ideas?

---

### Post by flippo on 2010-02-11
I am stumped.  Does the program your installing have a list of its build dependencies?  Although it seems the files autoconf is complaining about are there, it wouldn't hurt to triple check.  Other than that I am out of ideas

---

### Post by dgohn on 2010-02-11
Its actually a MUD.  Several of these types of games run on the previous server.  None will compile or configure on the new one.

---

### Post by john newbuntu on 2010-02-11
Thanks to Google, read this up.  This might help you:
[http://www.gnu.org/software/hello/manual/autoconf/Present-But-Cannot-Be-Compiled.html#Present-But-Cannot-Be-Compiled](http://www.gnu.org/software/hello/manual/autoconf/Present-But-Cannot-Be-Compiled.html#Present-But-Cannot-Be-Compiled)

---

### Post by dgohn on 2010-02-11
Ok from that link you posted and what I gather from it is that I need to add the following to my configure.ac file...
 
```
     AC_CHECK_HEADERS([number.h pi.h], [], [],
     [[#ifdef HAVE_NUMBER_H
     # include <number.h>
     #endif
     ]])

```
 
Right under:  
```
  AC_INIT([Example], [1.0], [bug-example@example.org])

```
 
However that doesn't solve the problem.  Am I missing something in the documentation?  I am assuming so because it kind of confused me to be honest.  Thanks for the help!

---

### Post by john newbuntu on 2010-02-12
I have not mucked much with autoconf.  But it looks like depending on the version, it relies on either the preprocessor or compiler or both for header checks, which is what is causing these problems.  The link I pointed out was only an example.

Remove the code that you added in configure.ac file and add this instead:
AC_CHECK_HEADERS([crypt.h assert.h arpa/telnet.h arpa/inet.h])
Now try the build.

If this does not work, you will have to find dependencies on each header file that it
is complaining about (like the one given in the example) and include those in configure.ac.  Example:

AC_CHECK_HEADERS([abc.h assert.h ], [], [],
     [[#ifdef HAVE_ABC_H
     # include <abc.h>
     #endif
     ]])

where abc.h is the file that refers to assert.h and so on.

---

### Post by dgohn on 2010-02-12
Any intelligent person that is having a problem like this over a certain period of time would post to several different forums.  As I appreciate ALL of the help found on this forum, the answer was found on another forum.  I am happy that I can post the solution to this forum as this is the FIRST forum I goto for help with anything regarding Ubuntu as it has the vast knowledge of long using Ubuntu user's.  Thanks to everyone that helped and the following is the solution:



It was an odd libc6-dev package that was the same  version as current on the Ubuntu site, but had different header file  contents. This could have been because of a bad .iso install or a bad apt-get install.  Either way, if you run into this problem:
 
The solution was: 
apt-get update 
apt-get clean 
dpkg -r --force-depends libc6-dev 
apt-get install libc6-dev

Solved all of the configure warnings as well as the compile errors.


Again, thanks to everyone that helped and I hope this thread will reach out to others that 'google' this problem.

---

