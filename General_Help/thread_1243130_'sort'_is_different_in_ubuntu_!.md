---
title: "'sort' is different in ubuntu !?"
date: 2009-08-17
forum: General Help
---

### Post by joseche on 2009-08-17
How is that 'sort' works different in ubuntu !?

How is that this doesn't work: 

  >  ls -al | sort +4n

Basic unix needs !, what is it about sort in ubuntu !?

:confused:

---

### Post by Wim Sturkenboom on 2009-08-18
Tested your command on a Slackware box (no Ubuntu at hand). Seems to sort by size. Question is what does not work? Can you give sample output of what you expect and what you actually get?

*ls* has an sort-by-size option.

---

### Post by joseche on 2009-08-18
```

$ ls -al | sort +4n
sort: open failed: +4n: No such file or directory

```

this is really something I didn't expect from ubuntu !

---

### Post by kaibob on 2009-08-18
I tested the OP's command in Jaunty, and it didn't work. I checked the sort man page and tried the following, which did work:

```
ls -al | sort -k 5 -n
```

> $ ls -al | sort -k 5 -n
total 12936
-rw-r--r--  1 root root    1074 2009-07-24 19:13 vmcoreinfo-2.6.28-14-generic
drwxr-xr-x 22 root root    4096 2009-08-01 22:54 ..
drwxr-xr-x  2 root root    4096 2009-08-01 22:54 grub
drwxr-xr-x  3 root root    4096 2009-08-01 22:54 .
-rw-r--r--  1 root root   96768 2009-07-24 19:12 config-2.6.28-14-generic
-rw-r--r--  1 root root  128796 2009-03-27 10:15 memtest86+.bin
-rw-r--r--  1 root root  528128 2009-07-24 19:12 abi-2.6.28-14-generic
-rw-r--r--  1 root root 1449836 2009-07-24 19:12 System.map-2.6.28-14-generic
-rw-r--r--  1 root root 3490224 2009-07-24 19:12 vmlinuz-2.6.28-14-generic
-rw-r--r--  1 root root 7494986 2009-08-01 20:54 initrd.img-2.6.28-14-generic

---

### Post by joseche on 2009-08-18
the point here is:

what about the compatibility with the "unix command line", how about the myriad of scripts using the "unix's sort", I just don't get it, ubuntu seems like a good distro of a unix os, but it won't be one option of they change the basics. I was considering ubuntu server but right now I think it may be better to hold it since I don't want to discover there is a new syntax for sh, cp or mv !

---

### Post by lisati on 2009-08-18
> **joseche said:**
> the point here is:

what about the compatibility with the "unix command line", how about the myriad of scripts using the "unix's sort", I just don't get it, ubuntu seems like a good distro of a unix os, but it won't be one option of they change the basics. I was considering ubuntu server but right now I think it may be better to hold it since I don't want to discover there is a new syntax for sh, cp or mv !

The thing about Ubuntu is that it's based in Linux, which in turn is unix-like without actually being unix.

---

### Post by joseche on 2009-08-18
hhhhhhmmm.........     I don't think you speak for many people !, basically you are saying ubuntu is not unix ?

---

### Post by HiImTye on 2009-08-18
yes, Ubuntu is not Unix

it is Linux

Linux is in the catagory of 'Functional Unix' as it is a Unix-Like operating system

basically, Unix has AT&T base code which is expensive and so Linux is meant as a 'free' alternative, at least that's how Linux began. now there are many varieties of 'free' and 'non-free' versions around. Ubuntu happens to be one of the 'free and open source' versions

---

### Post by slakkie on 2009-08-18
Linux is not Unix. Linux is a Unix-like system. So therefor Ubuntu is not Unix, since Ubuntu is Linux. GNU/Linux to be more precise.

Most tools can be run in a POSIX style, so you have similar flags so it maintains platform independence.

But these small differences are more common, I also have problems when I write shell scripts. Some functions work in Ubuntu (Linux), while are unsupported on Solaris (Unix). Which then leads to solve it differently or make an exception for an OS.

---

### Post by lisati on 2009-08-18
> **joseche said:**
> hhhhhhmmm.........     I don't think you speak for many people !, basically you are saying ubuntu is not unix ?

In the two years I've been using Ubuntu, it has NEVER been Unix. 

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)
[http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)

---

### Post by P4man on 2009-08-18
It actually appears ubuntu (/linux) follows posix standards here, and ironically, whatever unix version allowed that command, does not:

[http://www.devdaily.com/unix/man/man1/sort.1.shtml](http://www.devdaily.com/unix/man/man1/sort.1.shtml)

---

### Post by joseche on 2009-08-18
you are right, by definition Linux is not Unix, GNU is not Unix, and Ubuntu is just Linux like. The reality is, GNU, Linux and Ubuntu will not exist if there is no benefit in them, and this very benefit comes from the 'compliance' with the Unix philosophy which all these terms try to avoid. Ubuntu and Linux distros in general are 'Unix like but not really Unix', the more they differentiate the more they become unusable, is the compliance what makes these initiatives strong.

I don't think making Ubuntu less like the other 'Unix like' OSs is a smart decision, anyways.... How can I get the 'unix kinda sort utility' ?

---

### Post by P4man on 2009-08-18
> **joseche said:**
>  and this very benefit comes from the 'compliance' with the Unix philosophy which all these terms try to avoid. Ubuntu and Linux distros in general are 'Unix like but not really Unix', the more they differentiate the more they become unusable, **is the compliance what makes these initiatives strong**.

Compliance to posix standards.. and again, it seems like linux here complies, and that command you are used to, is not compliant. Im guessing you're used to BSD? 

Anyway the answer to your question is already give by kaibob I believe.

---

### Post by dcstar on 2009-08-19
> **joseche said:**
> you are right, by definition Linux is not Unix, GNU is not Unix, and Ubuntu is just Linux like. The reality is, GNU, Linux and Ubuntu will not exist if there is no benefit in them, and this very benefit comes from the 'compliance' with the Unix philosophy which all these terms try to avoid. Ubuntu and Linux distros in general are 'Unix like but not really Unix', the more they differentiate the more they become unusable, is the compliance what makes these initiatives strong.

I don't think making Ubuntu less like the other 'Unix like' OSs is a smart decision, anyways.... How can I get the 'unix kinda sort utility' ?

Which "unix"? I used to use SCO Unix and commands that worked on that platform would not work on alternative Unix "Y", and Unix "Y" also had differences to Unix "Z".

This is the sort of thing that allowed Unix to be supplanted by NetWare and then Windows as people were always highly annoyed that one Unix family was never the same as any other (basically due to the snobbery of each group that thought that *their* platform was always superior......)

Be thankful that now things like POSIX standards exist so people have a fighting chance now of writing things that will work across any complying platform.

---

