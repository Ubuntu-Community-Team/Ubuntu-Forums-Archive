---
title: "Errors compiling printer driver"
date: 2009-09-18
forum: General Help
---

### Post by yknivag on 2009-09-18
As part of a project I'm working on, I'm trying to get a receipt printer to work with my laptop (running a fairly standard Jaunty install). It's a Citizen CBM1000-II which, according to the vendor has manufacturer supported linux drivers.  I followed [this link on their site](http://www.citizen-systems.co.jp/support/download/printer/driver/cups/index.html) and downloaded and extracted the tarball.

This gave me the following files:

```

gavin@elbow:~/Desktop/cups-CBM1000$ ls -l
total 44
-rw-r--r-- 1 gavin gavin 27756 2006-03-03 06:47 CBM1000.ppd
-rw-r--r-- 1 gavin gavin 13489 2006-03-01 06:48 rastertocbm1k.c
gavin@elbow:~/Desktop/cups-CBM1000$ 

```

The .ppd file is recognised ok by CUPS (latest version packaged with Jaunty).

The instructions on the site say I need to compile the .c file to get a filter file for CUPS. This is the gcc version I'm using (which is quite a bit ahead of the one stated on the Citizen website):

```

gavin@elbow:~/Desktop/cups-CBM1000$ gcc --version
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I have "build-essentials" installed which should give me all I need to do this? But I get the errors below:

```

gavin@elbow:~/Desktop/cups-CBM1000$ gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k.c -lcupsimage -lcups
rastertocbm1k.c:33:23: error: cups/cups.h: No such file or directory
rastertocbm1k.c:34:22: error: cups/ppd.h: No such file or directory
rastertocbm1k.c:35:25: error: cups/raster.h: No such file or directory
rastertocbm1k.c: In function ‘outputCommand’:
rastertocbm1k.c:158: warning: implicit declaration of function ‘putchar’
rastertocbm1k.c: At top level:
rastertocbm1k.c:161: error: expected declaration specifiers or ‘...’ before ‘ppd_file_t’
rastertocbm1k.c: In function ‘getOptionChoiceIndex’:
rastertocbm1k.c:163: error: ‘ppd_choice_t’ undeclared (first use in this function)
rastertocbm1k.c:163: error: (Each undeclared identifier is reported only once
rastertocbm1k.c:163: error: for each function it appears in.)
rastertocbm1k.c:163: error: ‘choice’ undeclared (first use in this function)
rastertocbm1k.c:164: error: ‘ppd_option_t’ undeclared (first use in this function)
rastertocbm1k.c:164: error: ‘option’ undeclared (first use in this function)
rastertocbm1k.c:166: warning: implicit declaration of function ‘ppdFindMarkedChoice’
rastertocbm1k.c:166: error: ‘ppd’ undeclared (first use in this function)
rastertocbm1k.c:168: warning: implicit declaration of function ‘ppdFindOption’
rastertocbm1k.c:169: warning: implicit declaration of function ‘ppdFindChoice’
rastertocbm1k.c: At top level:
rastertocbm1k.c:174: error: expected ‘)’ before ‘*’ token
rastertocbm1k.c: In function ‘initializeSettings’:
rastertocbm1k.c:247: error: ‘ppd_file_t’ undeclared (first use in this function)
rastertocbm1k.c:247: error: ‘ppd’ undeclared (first use in this function)
rastertocbm1k.c:248: error: ‘cups_option_t’ undeclared (first use in this function)
rastertocbm1k.c:248: error: ‘options’ undeclared (first use in this function)
rastertocbm1k.c:251: warning: implicit declaration of function ‘ppdOpenFile’
rastertocbm1k.c:252: warning: implicit declaration of function ‘ppdMarkDefaults’
rastertocbm1k.c:253: warning: implicit declaration of function ‘cupsParseOptions’
rastertocbm1k.c:255: warning: implicit declaration of function ‘cupsMarkOptions’
rastertocbm1k.c:256: warning: implicit declaration of function ‘cupsFreeOptions’
rastertocbm1k.c:259: warning: implicit declaration of function ‘memset’
rastertocbm1k.c:259: warning: incompatible implicit declaration of built-in function ‘memset’
rastertocbm1k.c:260: error: too many arguments to function ‘getOptionChoiceIndex’
rastertocbm1k.c:261: error: too many arguments to function ‘getOptionChoiceIndex’
rastertocbm1k.c:262: error: too many arguments to function ‘getOptionChoiceIndex’
rastertocbm1k.c:263: error: too many arguments to function ‘getOptionChoiceIndex’
rastertocbm1k.c:266: warning: implicit declaration of function ‘getPageWidthPageHeight’
rastertocbm1k.c:267: warning: implicit declaration of function ‘ppdClose’
rastertocbm1k.c: In function ‘jobSetup’:
rastertocbm1k.c:290: warning: implicit declaration of function ‘printf’
rastertocbm1k.c:290: warning: incompatible implicit declaration of built-in function ‘printf’
rastertocbm1k.c: At top level:
rastertocbm1k.c:294: error: expected declaration specifiers or ‘...’ before ‘cups_page_header_t’
rastertocbm1k.c: In function ‘main’:
rastertocbm1k.c:348: error: ‘cups_raster_t’ undeclared (first use in this function)
rastertocbm1k.c:348: error: ‘ras’ undeclared (first use in this function)
rastertocbm1k.c:349: error: ‘cups_page_header_t’ undeclared (first use in this function)
rastertocbm1k.c:349: error: expected ‘;’ before ‘header’
rastertocbm1k.c:392: warning: implicit declaration of function ‘fputs’
rastertocbm1k.c:392: error: ‘stderr’ undeclared (first use in this function)
rastertocbm1k.c:402: warning: implicit declaration of function ‘perror’
rastertocbm1k.c:403: warning: implicit declaration of function ‘sleep’
rastertocbm1k.c:416: warning: implicit declaration of function ‘cupsRasterOpen’
rastertocbm1k.c:416: error: ‘CUPS_RASTER_READ’ undeclared (first use in this function)
rastertocbm1k.c:417: warning: implicit declaration of function ‘cupsRasterReadHeader’
rastertocbm1k.c:417: error: ‘header’ undeclared (first use in this function)
rastertocbm1k.c:421: warning: implicit declaration of function ‘cupsRasterClose’
rastertocbm1k.c:421: warning: implicit declaration of function ‘close’
rastertocbm1k.c:426: error: too many arguments to function ‘pageSetup’
rastertocbm1k.c:428: warning: implicit declaration of function ‘fprintf’
rastertocbm1k.c:428: warning: incompatible implicit declaration of built-in function ‘fprintf’
rastertocbm1k.c:433: warning: incompatible implicit declaration of built-in function ‘printf’
rastertocbm1k.c:440: warning: implicit declaration of function ‘cupsRasterReadPixels’
gavin@elbow:~/Desktop/cups-CBM1000$ 

```

Does anyone know what may be wrong?

I'm reasonably confident with most things, but compiling from source isn't really something I've done much (apart from the ./configure, make, makeinstall type of installation).

---

### Post by snova on 2009-09-18
> **yknivag said:**
> I have "build-essentials" installed which should give me all I need to do this? But I get the errors below:

Well, it's the essentials at least, programs may have dependencies beyond that.

This is the interesting bit:

> ```

rastertocbm1k.c:33:23: error: **cups/cups.h: No such file or directory**
rastertocbm1k.c:34:22: error: **cups/ppd.h: No such file or directory**
rastertocbm1k.c:35:25: error: **cups/raster.h: No such file or directory**

```

And this is a convenient means of finding which package contains those files:

```
$ apt-file search cups/cups.h
libcups2-dev: /usr/include/cups/cups.h

```

So install the **libcups2-dev** package and try again.

---

### Post by yknivag on 2009-09-18
I'm guessing from these lines:

```

rastertocbm1k.c:33:23: error: cups/cups.h: No such file or directory
rastertocbm1k.c:34:22: error: cups/ppd.h: No such file or directory
rastertocbm1k.c:35:25: error: cups/raster.h: No such file or directory

```

That I need some sort of development libraries for CUPS.  The only one I can find in the repositories is "libgnomecups1.0-dev" which says it has the headers in but I can't install it due to broken dependancies.

---

### Post by yknivag on 2009-09-18
Thanks snova.

I tried installing libcups2-dev but got this:

```

gavin@elbow:~$ sudo apt-get install libcups2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libcups2-dev: Depends: libgnutls-dev but it is not going to be installed
E: Broken packages

```

So I tried adding lingnutls-dev too:

```

gavin@elbow:~$ sudo apt-get install libcups2-dev libgnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgnutls-dev: Depends: libgnutls26 (= 2.4.2-6ubuntu0.1) but 2.4.2-6+lenny1 is to be installed
E: Broken packages

```

and when I try adding libgnutls26 I get:

```

gavin@elbow:~$ sudo apt-get install libcups2-dev libgnutls-dev libgnutls26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnutls26 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgnutls-dev: Depends: libgnutls26 (= 2.4.2-6ubuntu0.1) but 2.4.2-6+lenny1 is to be installed
E: Broken packages

```

Any ideas?

EDIT: Apologies if I'm posting too much detail, hope it means more to others than it does to me.

---

### Post by yknivag on 2009-09-18
I've found three files named cups.h, ppd.h and raster.h but they seem to be at a different location to where the compiler is looking:

```

gavin@elbow:/usr/include/lsb3/cups$ ls -l
total 20
-rw-r--r-- 1 root root 7672 2008-11-06 15:53 cups.h
-rw-r--r-- 1 root root 4797 2008-11-06 15:53 ppd.h
-rw-r--r-- 1 root root 3697 2008-11-06 15:53 raster.h

```

I copies these files to /usr/lib/cups/ but the compiler still fails to find them...

---

### Post by yknivag on 2009-09-20
Sorry to bump the thread, but I can't find anything anywhere that would explain this.

I have no knowledge at all about gcc, I'm guessing the "rpath" option in the command is setting the path to which all the paths in the errors point, is that correct? Or do I need to move the three .h files so the paths stated are relative to the location of the .c file?

---

### Post by yknivag on 2009-09-20
Having a look at the code (C really isn't my forte!), this appears in a comment right at the top:

```

/*
 * Citizen Systems
 *
 * CUPS Filter
 *
 * compile cmd: gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k.c -lcupsimage -lcups
 * compile requires cups-devel-1.1.19-13.i386.rpm (version not neccessarily important?)
 * find cups-devel location here: http://rpmfind.net/linux/rpm2html/search.php?query=cups-devel&submit=Search+...&system=&arch=
 */

```

I can't find a cups-devel* package in Synaptic though.  Any ideas?

---

### Post by t0p on 2009-09-20
That source comment you quoted contains this line:

> 
find cups-devel location here: [http://rpmfind.net/linux/rpm2html/search.php?query=cups-devel&submit=Search+...&system=&arch=](http://rpmfind.net/linux/rpm2html/search.php?query=cups-devel&submit=Search+...&system=&arch=)

I suggest you stick that url in your browser and see what's there.  This will find an rpm package, which you'll need to convert to a deb with the **alien** package.  At least, that's what I *assume* you'll find there - I haven't looked myself.

---

### Post by yknivag on 2009-09-20
Aha, it seems there is something wrong with the relative paths.  After changing all the paths to absolute in both the .c files and the .h files I've now got a lot less errors:

```

gavin@elbow:~/Downloads/cups-CBM1000$ sudo gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k_2.c -lcupsimage -lcups
rastertocbm1k_2.c: In function &#8216;initializeSettings&#8217;:
rastertocbm1k_2.c:259: warning: implicit declaration of function &#8216;memset&#8217;
rastertocbm1k_2.c:259: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
rastertocbm1k_2.c: In function &#8216;main&#8217;:
rastertocbm1k_2.c:403: warning: implicit declaration of function &#8216;sleep&#8217;
rastertocbm1k_2.c:421: warning: implicit declaration of function &#8216;close&#8217;
/usr/bin/ld: cannot find -lcupsimage
collect2: ld returned 1 exit status

```

My C really isn't good enough to really understand the warnings or their impact.  Does anyone know what "lcupsimage" is and why it wouldn't be found?

I still can't install all the cups development libraries (presumably it's in there somewhere) due to a circular package dependancy that apt can't resolve.

Has anyone ever managed to install these packages on Jaunty?  Should I file a bug about the circular dependancy issue?

---

### Post by yknivag on 2009-09-20
> **t0p said:**
> I suggest you stick that url in your browser and see what's there.  This will find an rpm package, which you'll need to convert to a deb with the **alien** package.  At least, that's what I *assume* you'll find there - I haven't looked myself.

Hi t0p, thanks for your help.  Sadly the file I require is unavailable on that site.  It's available in the repositories as "libcupsys2" but this won't install.

---

### Post by yknivag on 2009-09-22
I hate bumping threads, but I really need to get this working.

Can anyone advise on the issues with cups libraries not intalling? (I've put the error below)

```

gavin@elbow:~$ sudo apt-get install libcups2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libcups2-dev: Depends: libgnutls-dev but it is not going to be installed
E: Broken packages

```

If I try again adding libgnutls-dev to the apt-get it comes back with this which is what I can't understand how to resolve:

```

gavin@elbow:~$ sudo apt-get install libcups2-dev libgnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  [COLOR="Red"]libgnutls-dev: Depends: libgnutls26 (= 2.4.2-6ubuntu0.1) but 2.4.2-6+lenny1 is to be installed[/COLOR]
E: Broken packages

```

---

### Post by snova on 2009-09-22
> **yknivag said:**
> 
```

The following packages have unmet dependencies.
  [COLOR="Red"]libgnutls-dev: Depends: libgnutls26 (= 2.4.2-6ubuntu0.1) but 2.4.2-6+lenny1 is to be installed[/COLOR]

```

Lenny? That's odd. What are the contents of /etc/apt/sources.list?

---

### Post by yknivag on 2009-09-23
Hi snova, thanks for your input.  I was a bit concerned about the lenny bit too (isn't that native Debian from which Ubuntu is built?)

I've attached my sources.list as a tar.gz

There is a line in there from Debian which I added for something specific (can't remember what now) but I can't see how that has caused the issue as the library concerned seems to be a dependency for the whole of gnome (or at least that's what apt tries to remove if I try and remove the library.

Any ideas?

I guess I really should reinstall (hasn't really been the same since I upgraded from Hardy to Jaunty) but am waiting for Koala for that.

---

### Post by snova on 2009-09-23
> **yknivag said:**
> Hi snova, thanks for your input.  I was a bit concerned about the lenny bit too (isn't that native Debian from which Ubuntu is built?)

I think so, but mixing the two generally doesn't end well.

> There is a line in there from Debian which I added for something specific (can't remember what now) but I can't see how that has caused the issue as the library concerned seems to be a dependency for the whole of gnome (or at least that's what apt tries to remove if I try and remove the library.

Any ideas?

As long as it was only used for that one package I can't see it messing anything up, but what concerns me now is that it still wants to install stuff from Lenny. The line in question is commented out, but if you haven't told apt-get to update since you did so, it will still look there.

Well, try this just in case:

```
sudo apt-get update
sudo apt-get install libcups2-dev
```

---

### Post by yknivag on 2009-09-23
Hi snova,

I've tried that before, but did again and came up with the same result:

```

The following packages have unmet dependencies.
  libgnutls-dev: Depends: libgnutls26 (= 2.4.2-6ubuntu0.1) but 2.4.2-6+lenny1 is to be installed
E: Broken packages

```

I commented out the debian specific repository ages ago (after I'd installed whatever it was that was dependant on it) but something seems to be stopping apt from either ovewriting libgnutls26 wih the Ubuntu version or accepting that it is the same file...

My plan was to run:

```

sudo apt-get remove libgnutls26 && sudo apt-get install libcups2-dev

```

but when doing that apt tries to remove gnome!

---

### Post by yknivag on 2009-09-27
I hate bumping my own threads, but before I reinstall the entire OS does anyone know anyway I can replace the lenny version of libgnutls26 with the Ubuntu one without apt removing and re-installing all of Gnome?

---

### Post by yknivag on 2009-09-30
I guess that's a no then. Rebuild time it is...

---

### Post by kadejo on 2009-11-02
Hi!

I could compile rastertocbm1k.c (in 9.04, 64 bits) installing the package libcupsimage2-dev, which has raster.h (that was the only header I had not, the other headers needed I suppose that came with libcups2-dev, that I had already installed).

[http://packages.ubuntu.com/jaunty/libcupsimage2-dev](http://packages.ubuntu.com/jaunty/libcupsimage2-dev)

Afterwards, the original gcc command line that was inside the .c worked like a charm:
gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k.c -lcupsimage -lcups

What I haven't done is to make that works, as I don't have the real printer here, it was a friend of mine who asked me to try to do something with that rpm-distro lover .c code.

Hopefully this helps!

---

### Post by yknivag on 2009-11-08
Hi kadejo, thanks for your reply.  I manged to get it to work after re-installing.  I should have come back really and marked the thread as solved.

My problem was something I had previously installed had used a native Debian library rather than the Ubuntu equivalent.

---

