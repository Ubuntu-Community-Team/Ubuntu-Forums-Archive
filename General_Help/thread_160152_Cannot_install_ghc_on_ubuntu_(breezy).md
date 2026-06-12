---
title: "Cannot install ghc on ubuntu (breezy)"
date: 2006-04-14
forum: General Help
---

### Post by frank05 on 2006-04-14
I cannot install any version of ghc on breezy (ghc5, ghc6 or ghc-cvs).
```

sudo apt-get install ghc6

```

gives me this:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ghc6: Depends: libreadline5-dev but it is not going to be installed
E: Broken packages

```

probing a little further I looked to see if i can explicitly install libreadline5-dev, which gives a similar message.
```

The following packages have unmet dependencies:
  libreadline5-dev: Depends: libncurses5-dev but it is not going to be installedE: Broken packages

```

repeating the process with libncurses gives
```

The following packages have unmet dependencies:
  libncurses5-dev: Depends: libncurses5 (= 5.4-9ubuntu4) but 5.5-1 is to be installed
E: Broken packages

```

Admitedly my installation of breezy is an upgrade from hoary. I'd prefer not to do a fresh install until dapper is released, or at least until I've finished the assignments I'm doing! :???: 

Has anybody got any solutions/suggestion?

Thanks,

---

### Post by frank05 on 2006-04-14
Ok looks like I've fixed it. If this happens to you, do the following:

Download and install the following debs from the debian (stable) website (a google search will get you there):
libncurses5_5.4-4_i386.deb
and then;
libncurses5-dev_5.5-1_i386.deb

You should now be able to install ghc6 using apt-get, with no further problems.

Should I report this as a bug?

---

### Post by .sith on 2006-04-27
Hello, i'm been reading what you worte about the installing of ghc, well i have de same problem, i can not install ghc, i did everything you said:
firt i download and install libncurses5_5.4-4_i386.deb, but when i try to install the other one iit shows me that:


dpkg -i libncurses5-dev_5.5-1_i386.deb
(Reading database ... 61778 files and directories currently installed.)
Preparing to replace libncurses5-dev 5.5-1 (using libncurses5-dev_5.5-1_i386.deb) ...
Unpacking replacement libncurses5-dev ...
dpkg: dependency problems prevent configuration of libncurses5-dev:
 libncurses5-dev depends on libncurses5 (= 5.5-1); however:
  Version of libncurses5 on system is 5.4-4.
 libncurses5-dev depends on libc-dev; however:
  Package libc-dev is not installed.
dpkg: error processing libncurses5-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libncurses5-dev


please help me

---

### Post by frank05 on 2006-05-07
[QUOTE=.sith]Hello, i'm been reading what you worte about the installing of ghc, well i have de same problem, i can not install ghc, i did everything you said:
firt i download and install libncurses5_5.4-4_i386.deb, but when i try to install the other one iit shows me that:


dpkg -i libncurses5-dev_5.5-1_i386.deb
(Reading database ... 61778 files and directories currently installed.)
Preparing to replace libncurses5-dev 5.5-1 (using libncurses5-dev_5.5-1_i386.deb) ...
Unpacking replacement libncurses5-dev ...
dpkg: dependency problems prevent configuration of libncurses5-dev:
 libncurses5-dev depends on libncurses5 (= 5.5-1); however:
  Version of libncurses5 on system is 5.4-4.
 libncurses5-dev depends on libc-dev; however:
  Package libc-dev is not installed.
dpkg: error processing libncurses5-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libncurses5-dev


please help me[/QUOTE]

Hmm... Well I've looked at my own installation (again!) and both libncurses packages are 5.5-1. Have you tried installing the 5.5-1 version of libncurses5 before libncurses5-dev? Looking at those messages, that would seem to fix it. It looks (from those messages you post) as though you will also need to install libc-dev.
I must say I cannot really help you. I put my above solution down to luck, I was really just "jiggling" the system to see if it would cooperate.

---

