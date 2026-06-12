---
title: "Installing Desktop Drapes"
date: 2009-11-19
forum: General Help
---

### Post by praveenthivari on 2009-11-19
Hi,
I am trying to install Desktop Drapes in Jaunty and the ubuntu repo doesn't has it. I downloaded the source code and tried to install but I get this error:
```

praveen@praveen-desktop:~$ cd /home/praveen/Downloads/drapes-0.5.2/
praveen@praveen-desktop:~/Downloads/drapes-0.5.2$ ./configurechecking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... none
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for UNMANAGED_DEPENDENCIES_MONO... no
checking for UNMANAGED_DEPENDENCIES_MINT... no
configure: error: You need to install mono
praveen@praveen-desktop:~/Downloads/drapes-0.5.2$ 


```So, how do I get 'mono' installed.

I tried this:
```
sudo apt-get install mono
```

But no use.

---

### Post by 3rdalbum on 2009-11-19
When you go to compile something and it tells you that you need a package, you need the "development headers". On Ubuntu, you can download the development headers by looking in Synaptic for the package with "-dev" at the end of it.

So in your case, the Mono development headers should be in "libmono-dev" (it's what popped up when I did a search in Synaptic for Mono).

---

### Post by praveenthivari on 2009-11-19
Thanks for the reply 

This is wat I got in terminal:
```
praveen@praveen-desktop:~$ sudo apt-get install libmono-dev
[sudo] password for praveen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmono-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmono0
E: Package libmono-dev has no installation candidate
praveen@praveen-desktop:~$ 

```and the 'libmono0' which it refers to is already installed. I hv attached a pic of synaptic. There is no 'libmono-dev' in synaptic. Pls see it.

---

### Post by fluffman86 on 2009-11-19
You'll need to figure how to get the configure script to check for libmono0 instead of libmono-dev.  

And I'm not sure about Jaunty, but in Karmic there is a program called "Drapes" available in the repos to manage desktop wallpaper...not sure if that's what you need, though.

---

### Post by praveenthivari on 2009-11-19
Thanks.
Was using it in Karmic myself. But Karmic had some problems, so installed Jaunty back to allow the bugs getting cleared.

---

