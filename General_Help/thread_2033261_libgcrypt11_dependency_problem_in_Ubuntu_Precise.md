---
title: "libgcrypt11 dependency problem in Ubuntu Precise"
date: 2012-07-25
forum: General Help
---

### Post by pramuko on 2012-07-25
I have no idea how it started, but now my Ubuntu 12.04 is in broken state because of a dependency problem with libgrcypt11.

The message was
> You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgcrypt11 : Breaks: libgcrypt11:i386 (!= 1.5.0-3ubuntu0.1) but 1.5.0-3 is to be installed
 libgcrypt11:i386 : Breaks: libgcrypt11 (!= 1.5.0-3) but 1.5.0-3ubuntu0.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Reinstalling the package doesn't work. I also tried running 'apt-get -f install' as suggested but had no luck. 

How do I solve it?

---

### Post by pramuko on 2012-07-26
bump
8-[

---

### Post by jmfal on 2012-07-26
Welcome to Ubuntu Forums
Run this in a terminal

```
 sudo apt-get install -f   
```

You can copy/paste to terminal
Post errors if any .

---

### Post by pramuko on 2012-07-26
> **jmfal said:**
> Welcome to Ubuntu Forums
Run this in a terminal

```
 sudo apt-get install -f   
```

You can copy/paste to terminal
Post errors if any .

Sorry I have tried that before but didn't work.

here is the error message

> dpkg: error processing libgcrypt11:i386 (--configure):
 libgcrypt11:i386 1.5.0-3 cannot be configured because libgcrypt11:amd64 is in a different version (1.5.0-3ubuntu0.1)
dpkg: error processing libgcrypt11 (--configure):
 libgcrypt11:amd64 1.5.0-3ubuntu0.1 cannot be configured because libgcrypt11:i386 is in a different version (1.5.0-3)
Errors were encountered while processing:
 libgcrypt11:i386
 libgcrypt11
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by pramuko on 2012-07-26
second bump
:confused:

---

