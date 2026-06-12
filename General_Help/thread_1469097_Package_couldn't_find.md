---
title: "Package couldn't find"
date: 2010-05-01
forum: General Help
---

### Post by MughalShahzad on 2010-05-01
Hello to all

I had downloaded bluefish-2.0.0.tar.gz, extracted it, in downloads directory and tried the following command to install

```

shahzad@shahzad-desktop:~$ cd Downloads
shahzad@shahzad-desktop:~/Downloads$ sudo apt-get install bluefish-2.0.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bluefish-2.0.0
shahzad@shahzad-desktop:~/Downloads$

```I had netbeans-6.8-ml-linux.sh, I did the following to install

```

shahzad@shahzad-desktop:~/Downloads$ sudo apt-get install netbeans-6.8-ml-linux.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package netbeans-6.8-ml-linux.sh
shahzad@shahzad-desktop:~/Downloads$ 

```I can install both from repository but those are older versions
Kindly suggest me what to do both said Package couldn't find

Thanks & Regards
Shahzad

---

### Post by lisati on 2010-05-02
Moved to "General help"
Please do not post in "Ubuntu Studio" if the question isn't related to Ubuntu Studio.

---

### Post by akakingess on 2010-05-02
> **MughalShahzad said:**
> Hello to all

I had downloaded bluefish-2.0.0.tar.gz, extracted it, in downloads directory and tried the following command to install

```

shahzad@shahzad-desktop:~$ cd Downloads
shahzad@shahzad-desktop:~/Downloads$ sudo apt-get install bluefish-2.0.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bluefish-2.0.0
shahzad@shahzad-desktop:~/Downloads$

```I had netbeans-6.8-ml-linux.sh, I did the following to install

```

shahzad@shahzad-desktop:~/Downloads$ sudo apt-get install netbeans-6.8-ml-linux.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package netbeans-6.8-ml-linux.sh
shahzad@shahzad-desktop:~/Downloads$ 

```I can install both from repository but those are older versions
Kindly suggest me what to do both said Package couldn't find

Thanks & Regards
Shahzad

Using apt-get install is going to look to the repositories for the install, if you have downloaded and extracted and want to install you need to get into the directory to which it was extracted and more than likely do something like " ./configure " (without the quotes) or something of that nature rather than the apt-get install routine. If you google it you should find plenty of instructions on exactly how to install/compile the apps yourself.

---

### Post by MughalShahzad on 2010-05-02
Thank you so much its works but not finished successfully kindly see the following
```

shahzad@shahzad-desktop:~/Downloads/bluefish-2.0.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... (cached) no
configure: error: GNU gettext tools not found; required for intltool

```

Thanks for giving me time

Regards
Shahzad

---

### Post by themusicalduck on 2010-05-02
This looks like a much easier way to install it - [http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer]("http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer") without having to compile anything.

---

### Post by andrew.46 on 2010-05-03
Hi MughalShahzad,

Perhaps this guide might help you out:

Howto: Build the newest version of Bluefish under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

All the best,

Andrew

---

