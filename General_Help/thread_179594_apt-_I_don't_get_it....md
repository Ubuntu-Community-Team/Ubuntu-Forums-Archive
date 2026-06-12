---
title: "apt- I don't get it..."
date: 2006-05-20
forum: General Help
---

### Post by MartinHvidberg on 2006-05-20
I want to install R on my box

Acording to the R webpage ([http://www.r-project.org/](http://www.r-project.org/)) I could try somthing like:

> apt-cache search ^r-.*
>

That gave absolutely no result, just a new prompt.
I then tried to uncomment some of the lines in /etc/apt/sources.list, and added:

deb [http://mirrors.dotsrc.org/cran](http://mirrors.dotsrc.org/cran) bin linux debian stable

Now I get:

> apt-cache search ^r-.*
W: Couldn't stat source package list [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) bin/linux Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_linux_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) bin/debian Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_debian_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) bin/stable Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_stable_binary-i386_Packages) - stat (2 No such file or directory)

All this seems to be related to som of the lines I uncommented, if so, never mind.

But where is my R - What is going wrong here...

:-( Martin

---

### Post by astoltz on 2006-05-20
The actual package name is r-base.  It's in the universe repository so you'll need to have that un-commented in your /etc/apt/sources.list.  It doesn't look like you need the [http://mirrors.dotsrc.org/cran](http://mirrors.dotsrc.org/cran) - unless it has a newer version or something - so you can get rid of it.

To install, it would just be ```
sudo apt-get install r-base
```

---

### Post by MartinHvidberg on 2006-05-20
Thanks that helped...

> sudo apt-get install r-base
Password:
Reading package lists... Done
Building dependency tree... Done

But now what, need I do some more apt- stuff or what?

It went to far to belive that it's ready for
./config
make

? Martin ?

---

### Post by astoltz on 2006-05-20
You shouldn't have to compile anything with "./config, make".  What happened after the Building dependency tree?  Did it give you a list of dependecies and ask if it was OK to install, or did it say something like "couldn't find package r-base"?

---

### Post by MartinHvidberg on 2006-05-21
Sorry - I overlooked the last, but important, line in the responce.
The entire responce is like this:

```
> sudo apt-get install r-base
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://mirrors.dotsrc.org bin/linux Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_linux_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://mirrors.dotsrc.org bin/debian Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_debian_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://mirrors.dotsrc.org bin/stable Packages (/var/lib/apt/lists/mirrors.dotsrc.org_cran_dists_bin_stable_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package r-base
```

The whole thing takes about 1-2 seconds, so it don't have time to download mutch but can proberly just check the package availablity on the diferent servers.

I did just try to run the sugested "apt-get update" but when re-running "sudo apt-get install r-base" the output remains the same, as showen here abowe.

:-? Martin

---

### Post by MartinHvidberg on 2006-05-21
Please ignor this thread for a moment... I uncommented some more lines in /etc/apt/sources.list and ran apt-get update again.
Now it seems to have found what I want...
I'll be back...

:-) Martin

---

### Post by MartinHvidberg on 2006-05-21
It's working now - Thanks for your help.

:-) Martin

---

### Post by Keith_Beef on 2006-05-22
I managed to install R with no problems that I can spot yet, though I got a message when installing some of the recommended extra packages:

```
$ history
  204  sudo apt-get -f install
  205  sudo apt-get install r-base
  206  sudo apt-get install atlas3-3dnow atlas3-sse atlas3-sse2 refblas3 lapack3 ess r-doc-info r-doc-pdf r-doc-html
  207  sudo apt-get install atlas3-3dnow atlas3-sse atlas3-sse2 refblas3 lapack3 ess r-doc-info r-doc-pdf r-doc-html
  208  sudo apt-get install emacs21-el xlispstat pspp
  209  sudo apt-get -f install
  210  sudo apt-get install emacs21-el xlispstat pspp

```

I had a couple of messages about sonfiguration not being quite right, and suggesting that I do apt-get with the -f option, as you see.

After this, I saw this message:

```
The running cpu cannot execute SSE2 code

 You are installing SSE2 enhanced Atlas libs on a system which cannot execute them.  This is
 either because your processor is not an Intel Pentium IV or higher, or because your kernel is not
 configured to handle these instructions.  (For 2.2 kernels, you can reconfigure/rebuild with the
 kernel-patch-2.2.x-sse2 package, if you wish).  This package will go ahead and install the libs,
 but not set the runtime linker on this machine to use them.  You can later perform this
 configuration with dpkg-reconfigure atlas3-sse2.

```

I don't want to mess up my kernel (currently 2.6.12-10-386), and in any case my CPU can't handle the SSE2 instructions:

```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm)
stepping        : 0
cpu MHz         : 1152.523
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 2277.37
```

Is there anything else I should do, or any other packages I've missed?

Beef.

---

