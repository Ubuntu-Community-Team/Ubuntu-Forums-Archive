---
title: "A whole mess of stupidity."
date: 2009-07-22
forum: General Help
---

### Post by damian_ on 2009-07-22
Alright, so I've been using Ubuntu on/off for a few years, generally things work pretty good.
  I haven't touched my server in about a year (just let her go about her business and do what I need her to), I go and install something recently and it spits this out:

```

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

```

This happens every time I try and configure something (anything). So I read up that I need built-essential:

```

root@herman:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

```

Ok, so I try and install libc-dev ...

```

root@herman:~# apt-get install libc-dev
Reading package lists... Done
Building dependency tree... Done
Package libc-dev is a virtual package provided by:
  libc6-dev 2.3.6-0ubuntu20.5
You should explicitly select one to install.
E: Package libc-dev has no installation candidate

```

.. Try and install libc6-dev ...

```

root@herman:~# apt-get install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.5) but 2.4-1ubuntu12 is to be installed
E: Broken packages

```

So it keeps on this routine, just can't find the right packages to install in order for it to all work ..

Anyway, needless to say I'm probably doing something wrong, I just want to know what it is and how I can go about fixing it so I can at least compile things that don't come in packages :(

If anyone can help me, I would be muchly appreciative.

Thanks!

---

### Post by philinux on 2009-07-22
I assume you've run this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by damian_ on 2009-07-22
I have, with 20mins of download + install, everything has been upgraded besides; linux-image-386 linux-restricted-modules-386 openssh-client openssh-server

It still did nothing :(

---

### Post by regala on 2009-07-22
> **damian_ said:**
> I have, with 20mins of download + install, everything has been upgraded besides; linux-image-386 linux-restricted-modules-386 openssh-client openssh-server

It still did nothing :(

can you post the content of your obviously garbaged sources.list ? :)

---

### Post by gastly on 2009-07-22
I had something like this, it turned out to be a sources.list error...
Can you please post the contents of it?

---

### Post by jerome1232 on 2009-07-22
I would try ```
sudo apt-get install -f
``` which will attempt to fix broken packages.

---

### Post by damian_ on 2009-07-22
install -f didn't do anything, there's nothing banked up there (until i try and manually install build-essential from the .deb file, in which case it gives me more errors about g++ or something)

```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

```

---

### Post by gastly on 2009-07-22
hmmm...maybe try commenting the last line, the 'cdrom' one?
When I had a similar problem, it was because of my local repositories and when I commented them out, it worked.

Be sure to run, **sudo apt-get update** after that.

---

### Post by damian_ on 2009-07-22
It fails after that as well, I don't think I even have the disc in the system anyway, haha.

That's two suggestions down, keep them coming please! haha

:P

---

