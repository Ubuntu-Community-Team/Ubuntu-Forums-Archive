---
title: "Compiling from source on Ubuntu"
date: 2009-11-22
forum: General Help
---

### Post by mrsharpe on 2009-11-22
I'am using Ubuntu to learn the in and outs of programming in C++ on a linux platform and like with most versions of linux getting problems with running the ./configure setup for source packages after unzipping them and changing to the source directory. The thing here is not being beaten by the problem but trying to understand how to use the configure setup since it as plenty of options.
Take glib v2.22.2 have it installed ok so whats the deal. Well it seemed a little project to compile from source and just install it into the home directory as an exercise. Ran ./configure with the flag --exec set to the home directory, redirected the output to a log file. At the end of the log file I expected the 'Now Make file' message but no sign of it, so working back the following two lines occur,

[FONT=Calibri]/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In  function  `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115:  undefined reference to `main'[/FONT]

 The /usr/lib/gcc/i486-gnu directory contains lib's for four gcc versions none of these contain crt1.o This is found in /usr/lib. So is configure getting confused about the location of crt1.o and whats the second line referring to? How does one correct this and tell configure to look in the correct directories. I'am just hoping that somebody has the answer because its hard to find good info on using configure and the config.log it generates does not refer to crt1.o. 
I have to leave this one to the experts, yours Martin.

---

### Post by blazemore on 2009-11-23
There's a package in the repos which includes the most common build packages.
I have found it fixes many seemingly unrelated compilation errors.
You can install it with the following
```
sudo apt-get install build-essential
```

---

### Post by mrsharpe on 2009-11-23
The missing library is eglibc-2.10.1 - this is a complete nightmare to install after downloading the source package via the synpaptic package manager and reading the install text. Get it wrong and you screw up your system.
It requires a seperate build directory to run ./configure but how do you set the options in configure to do this?
Has anybody attempted to install this package and got it working correctly?

---

### Post by Giblet5 on 2009-11-23
I read your post (I think - I'm a pretty good reader) and I can't figure out what package you're trying to build.

Not every source package will build easily on any given Linux distro. To assume otherwise is a huge mistake: many source packages were developed by people who have absurdly-esoteric Linux-like installations. That makes them cool, see, and non-conformist. ;)

I would never build a package that depends on a glibc that I don't have. If a source package wants a different glibc or even a different g++ than my distro's default, I'll remove the source and look for alternatives, cuz the person who wrote that garbage is ignorant of coding standards (ergo, what else are they ignorant of). And I'm a developer of many MANY years.

If it's something I desperately need, I'll use the original source as a Hint Book and write my own version, except I'll follow practical coding standards.

That said, it's your system.

---

### Post by mrsharpe on 2009-11-23
Thanks Giblett5. Let me say this was a project to build the glib v2.22.1 source and install it in the home directory since I am trying out things on the linux platform and as you say plenty of distributions lack all the development tools. 
The eglibc is missing from the standard Ubuntu but comes installed on the Karmic Koala version. This is why the glib configure program throws out this error. To install eglibc reguires nerves of steel and of course backing up everything before hand. The problem I have is simply this - how do you tell configure to build into a seperate build directory from the source program?
Of course installing eglibc to the /usr directory overwrites the old library so this is clearly a dangerous install. As anybody installed eglibc from source?

---

### Post by ankspo71 on 2009-11-23
Hi,

Have you tried installing eglibc-source ?  (karmics version is 2.10.1) 
> This package contains the sources and patches which are needed to
build eglibc.It is not installed on my Karmic install, but it is available in the repos. this eglibc thing seems strange to me though... no dependencies with that package are listed.

Also, just for the record, libglib2.0-0 / 2.22.2-0ubuntu1 is already installed on my system but eglibc is not. (glib itself may have been a dependency to one of the programs I installed by synaptic though... not sure.) You might want to double check in your version of Ubuntu by searching for libglib2.0 and libglib2.0-dev to be sure.

Hope this somehow helps.
James

---

### Post by mrsharpe on 2009-11-23
Thanks ankspo
I imagine that eglibc will replace glibc for Ubuntu at some stage but installing the source package is a real pain. I will have ago at installing it into the default dir /usr/local/lib and keep both libraries. 
As any body  managed to install this library in /usr/lib to replace the gnu glibc?

---

### Post by mc4man on 2009-11-23
> As anybody installed eglibc from source?

Why would anyone want to ....? (all  the required libs from that source are installed/available

> how do you tell configure to build into a seperate build directory from the source program?

Ex.
> ...$ [COLOR="Blue"]mkdir build && cd build[/COLOR]
..../build$ [COLOR="Blue"]../configure[/COLOR] <whatever>

---

### Post by mrsharpe on 2009-11-23
Thanks mc4man, have build to a eglibc-build directory using configure using the default settings (after turning off the sanity checking) so make install uses /usr/local  keeping the glibc library untouched. The config.log has an exit code of zero. Is this correct?

The output from configure on the screen looks ok except for :

checking for grep that handles long lines and -e... Usage: /bin/grep [OPTION]... PATTERN [FILE]...
Try `/bin/grep --help' for more information.
../eglibc-2.10.1/sysdeps/unix/sysv/linux/configure: line 213: as_fn_error: command not found

Not sure if this is a fault or not.
I did try using the switch --with-headers with the path /usr/src/linux-headers-2.6.31-14/include/linux for the kernel headers but this gives a fault saying the kernel is too old so I used the default setting with no switch.
There was no 'now make' message at the end so I'am not sure if this build was successfull.
Anybody any ideas?

---

