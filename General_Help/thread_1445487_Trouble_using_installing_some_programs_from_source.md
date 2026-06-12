---
title: "Trouble using installing some programs from source"
date: 2010-04-02
forum: General Help
---

### Post by X-Malleus on 2010-04-02
Hi everyone,

I'm trying to install my mesa 3D drivers from source for my Intel GM965 graphics chip, and I can't seem to get it going.  When I've installed programs from source in the past, there has usually been a configuration script in the top directory, from which point I would always execute ./configure to set up the files needed for installation.  However, in this source package, there doesn't seem to be such a file, which is indicated by "no such file or directory" error I receive.  There is an autogen.sh script here, which seems to be the script that is executed in order to generate the configuration files.  I execute the script:

sudo bash autogen.sh

It then goes through numerous lines that appear to be doing the same thing that ./configure has done for other installations that I've used.  I've been able to work out all of the problems that I've come across by installing things that error messages said I needed, but I'm now stuck.  When I execute autogen.sh in the mesa-7.8 folder, I get this:

checking for GLPROTO... configure: error: Package requirements (glproto >= 1.4.11) were not met:

Requested 'glproto >= 1.4.11' but version of GLProto is 1.4.10


So okay, I search the internet and download glproto-1.4.11.  Execute autogen.sh in glproto-1.4.11.  This is what I get:

configure.ac:7: error: must install xorg-macros 1.3 or later before running autoconf/autogen

This is where I'm not sure what to do.  I went to [http://cgit.freedesktop.org/xorg/](http://cgit.freedesktop.org/xorg/) and downloaded a source package called util-macros-1.6.1, and I THINK I installed it properly, but I'm still getting the error message that I need xorg-macros 1.3 or later when I try to install glproto.  I'm not even entirely sure that this is the right macros package that I downloaded.  Anyone have any ideas about this?

---

### Post by Ancanus on 2010-04-02
Try
```

sudo aptitude install x11proto-gl-dev  
```


I found the package name using:
```

aptitude search proto

```

---

### Post by Chronon on 2010-04-02
It seems like you're trying to install bleeding edge source and it's requiring that you uprgrade a bunch of dependencies to versions that are newer than what's available in the repositories.  Do you need the bleeding edge or is it suitable to check out an older version, whose dependencies can be met by software that's downloadable from the repositories?  

It looks like glproto.pc is contained in the package x11proto-gl-dev (version 1.4.10-1 in Karmic, version 1.4.11-1 in Lucid).  I don't know your situation, but it might be easier to upgrade to the beta of Lucid and try compiling there (or do as I suggested in the first paragraph and check out an older version of the mesa drivers).

---

### Post by X-Malleus on 2010-04-02
> **Chronon said:**
> It seems like you're trying to install bleeding edge source and it's requiring that you uprgrade a bunch of dependencies to versions that are newer than what's available in the repositories.  Do you need the bleeding edge or is it suitable to check out an older version, whose dependencies can be met by software that's downloadable from the repositories?  

It looks like glproto.pc is contained in the package x11proto-gl-dev (version 1.4.10-1 in Karmic, version 1.4.11-1 in Lucid).  I don't know your situation, but it might be easier to upgrade to the beta of Lucid and try compiling there (or do as I suggested in the first paragraph and check out an older version of the mesa drivers).

Thank you so much for this advice to try an older version.  I got many more errors for missing packages, but installed all of them, and managed to get through the configuration script.

Unfortunately, when I tried to do make,  I got this error:

/bin/bash: g++: command not found
make[4]: *** [libnurbs/interface/bezierEval.o] Error 127

Is my computer missing a library/package that lets it recognize C commands or something?

---

### Post by Chronon on 2010-04-02
Did you install the package build-essential before trying to compile?  It should have pulled in g++ as a dependency.

---

### Post by X-Malleus on 2010-04-03
> **Chronon said:**
> Did you install the package build-essential before trying to compile?  It should have pulled in g++ as a dependency.

Hah!  I knew there was something.  Thank you so much, for this was the last problem that I needed to fix in order to make it work.

---

### Post by Chronon on 2010-04-03
You're welcome.  I'm glad to have helped.  :)

---

