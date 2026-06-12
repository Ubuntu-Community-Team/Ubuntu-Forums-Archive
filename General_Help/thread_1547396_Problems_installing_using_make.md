---
title: "Problems installing using make"
date: 2010-08-06
forum: General Help
---

### Post by mindlessbrain on 2010-08-06
Hi all,

I've gotten some great help from this board so I thought I'd ask again. 

I'm trying to install bwa - Burrows Wheeler Alignment Tool. Here: [http://bio-bwa.sourceforge.net/bwa.shtml](http://bio-bwa.sourceforge.net/bwa.shtml) if you're interested. 

When I cd into the folder and type make I get errors, and I have no idea what to make of them.

```

jill@jill-desktop:~/Desktop/bwa/bwa-0.5.7$ make
make[1]: Entering directory `/home/jill/Desktop/bwa/bwa-0.5.7'
make[1]: Nothing to be done for `lib'.
make[1]: Leaving directory `/home/jill/Desktop/bwa/bwa-0.5.7'
make[1]: Entering directory `/home/jill/Desktop/bwa/bwa-0.5.7/bwt_gen'
gcc -c -g -Wall -O2 -m64 -DHAVE_PTHREAD   bwt_gen.c -o bwt_gen.o
In file included from /usr/include/features.h:378,
                 from /usr/include/stdio.h:28,
                 from bwt_gen.c:25:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
bwt_gen.c: In function ‘BWTIncConstructFromPacked’:
bwt_gen.c:1416: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
bwt_gen.c:1432: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
bwt_gen.c:1447: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
make[1]: *** [bwt_gen.o] Error 1
make[1]: Leaving directory `/home/jill/Desktop/bwa/bwa-0.5.7/bwt_gen'
make: *** [lib-recur] Error 1
jill@jill-desktop:~/Desktop/bwa/bwa-0.5.7$ 

```

Anyone recognize these errors? Or have any idea what I should do about them?

Help would be so appreciated. I need this for a project for school. 

Thanks in advance!

---

### Post by Bachstelze on 2010-08-06
It's in the repos:

[http://packages.ubuntu.com/lucid/bwa](http://packages.ubuntu.com/lucid/bwa)

If you really want to compile from source, you'll need [font=monospace]bild-essential[/font].

---

### Post by mindlessbrain on 2010-08-06
I just had a whole issue where I finally got build essential installed. It says its installed in the synaptic package manager. It had better be freakin installed. I spent hours on it! Does this mean its not installed?

Thanks! I didn't even think of looking in the repos for things like that. I thought it would be too out there. 

I'll report back in a bit!

---

### Post by bruno9779 on 2010-08-06
I seem to understand you are on 64 bit Ubuntu.

A lot of software out there is made to compile on 32 bit, so the program looks for libraries in the wrong place.

This is usually sorted with an easy simlink. Post the error output, so someone can show you how to do that

---

### Post by mindlessbrain on 2010-08-06
Its installed! I am aware this is a pretty silly question, but once its installed how do i run it?

---

### Post by mindlessbrain on 2010-08-07
> **bruno9779 said:**
> I seem to understand you are on 64 bit Ubuntu.

A lot of software out there is made to compile on 32 bit, so the program looks for libraries in the wrong place.

This is usually sorted with an easy simlink. Post the error output, so someone can show you how to do that

I certainly didn't mean to install 64 bit ubuntu. I just installed it from the installation CD. 

How do I do the simlink? Do I need to reinstall the whole thing to get it to 32 bit, or will it be ok on 64 bit?

---

### Post by nothingspecial on 2010-08-07
I depends on weather or not you have a 64 bit computer.

You don`t run build essential, it is a collection of programs "essential" for "building" (gedit?) stuff from source (compiling, make etc etc)

If you have it then you are using it (or some part of it) when you type make.
[U]
The instructions for use are in the link you provided in your first post
[/U]

---

