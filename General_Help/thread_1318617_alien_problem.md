---
title: "alien problem"
date: 2009-11-07
forum: General Help
---

### Post by supermooshman on 2009-11-07
Hi All,

Since I installed 9.10 my lexmark printer does not work anymore (it did in jaunty)

I am following the HOWTO which can be found here on the forum.
- The problem is I have to alien something, which gives me an error:
```
desktop:~/lexmark$ alien -t z600cups-1.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
```

anyone who can tell me what to do?
Thanks

---

### Post by wojox on 2009-11-07
```
desktop:~/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm
```

Maybe, never used alien.

---

### Post by supermooshman on 2009-11-07
> **wojox said:**
> ```
desktop:~/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm
```Maybe, never used alien.

woopsie, forgot to mention, I tried sudo alien...

it got me:
```

sudo alien -t z600cups-1.0-1.i386.rpm
[sudo] password for rudolf: 
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
```

---

### Post by lswb on 2009-11-07
Try doing as the warning suggests:

sudo alien --scripts -t z600cups-1.0-1.i386.rpm

---

### Post by r0f1 on 2010-01-06
i have the exact same problem with my lexmark on ubuntu 9.10 :(

```
me@me-laptop:~/lexmark$ sudo alien --scripts -t z600cups-1.0-1.i386.rpm
error: incorrect format: unknown tag
z600cups-1.0.tgz generated

```

what can I do?

---

### Post by Leppie on 2010-01-06
did you guys have a look at the hardware support page: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

---

### Post by r0f1 on 2010-01-06
thank you for your fast responds. i tried out this guide but
it contains also these following lines (step 7):

```
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
```

and alien just does not work -.-
it only prints the above mentioned error.

---

### Post by adam814 on 2010-01-06
If you're using alien anyway why not make .deb packages instead of .tgz (Slackware/Generic Linux I think)?
```
sudo alien --to-deb z600cups-1.0-1.i386.rpm
```
You may still get the error, but if you don't and it works you should be a step closer to getting it installed.

---

### Post by Leppie on 2010-01-06
are you sure you downloaded the correct archive?
i've actually done the thing a while ago myself (even though on a debian lenny system) and a different guide, but the procedure seems the same.
however, come to think of it, i believe that guide instructed to install gcc 4.3 as there was something wrong with 4.4.

---

### Post by r0f1 on 2010-01-06
i downloaded this driver: [http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_Z605&id=DR15809&os=RED_HAT_LINUX&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_Z605&id=DR15809&os=RED_HAT_LINUX&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en)

how do i install  gcc 4.3 ??

the solution adam814 suggested didn't work. my terminal printed these lines: 

```
my@my-laptop:~/lexmark$ sudo alien --to-deb *.rpm
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/z600cups
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: error: couldn't find library libstdc++.so.5 needed by debian/z600cups/usr/lib/cups/filter/rastertoz600 (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `z600cups-1.0': No such file or directory

```

---

### Post by adam814 on 2010-01-06
I see 2 problems with that log.  One is you're running the amd64 version of Ubuntu but trying to convert and install an i386 RPM package.  Is there no 64-bit rpm available?

The second (and more worrying problem) is that it's been built with libstdc++5, which has been replaced with version 6 in Karmic.  If it were an open-source package it wouldn't be a problem as you'd just build it from source with the new library.  But I'm assuming they don't post source code if you're trying to convert an RPM.

---

### Post by r0f1 on 2010-01-06
>  Is there no 64-bit rpm available?
no, there is not :( this is a workaround, because there are hardly any drivers available for linux.

> The second (and more worrying problem) is that it's been built with libstdc++5, which has been replaced with version 6 in Karmic. If it were an open-source package it wouldn't be a problem as you'd just build it from source with the new library. But I'm assuming they don't post source code if you're trying to convert an RPM.

any ideas, what i could try next? is there maybe a way to reinstall  libstdc++5?

---

### Post by adam814 on 2010-01-06
I've been there.  I know how it is when you can't get a piece of hardware to work.

Hmm...you could use the "linux32" program to try to fool alien into thinking you're running on i386 then force the architecture with dpkg on install.  That might work.

As for installing libstdc++5 I'm less optimistic.  On my system (Karmic amd64) libstdc++6 lists a lot of dependencies.  You might be able to install it without messing up your system, but you don't want to lose libstdc++6 since every application written in C++ needs it.

What you might want to do is try running alien -g instead to make a temporary directory and then try to fish out any .ppd files you find since those should be all you need and (mostly) platform independent.

---

### Post by Leppie on 2010-01-06
i'll have a look and see if i still have the deb package for the drivers around somewhere.

---

### Post by PhazzedOut on 2010-05-07
Still no solution?

---

### Post by WorMzy on 2010-05-07
I gave up with my Lexmark z517 about half-way through Karmic's time as flagship. It was working for the first half but then the drivers stopped working, and no amount of uninstalling and reinstalling would fix it. I guess CUPS was updated, and no longer wanted to play nice with the drivers. The printers never played well on Windows either -- never working on 64-bit versions, or Vista, therefore forcing me to use Windows XP Home whenever I wanted to print something -- so I've just decided to just buy a more common printer once I get some money flow.

Just thought I'd add my tuppence worth.

---

