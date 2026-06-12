---
title: "ubuntu repositories in debian lenny?"
date: 2009-11-28
forum: General Help
---

### Post by mtgmutton on 2009-11-28
i have successfully installed debian lenny on my laptop, and after wrestling with wireless, i was able to add the karmic koala repositories to my "/etc/apt/sources.list" file. i added the keys as required, but it looks like it isn't using the repositories i've added. i try to use "apt-get install firefox" as root, but it spits this back at me:

```
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  iceweasel
E: Package firefox has no installation candidate

```

are the karmic repositories not compatible with lenny? i can post the sources file if need be.
thanks in advance!

---

### Post by dcstar on 2009-11-28
> **mtgmutton said:**
> i have successfully installed debian lenny on my laptop, and after wrestling with wireless, i was able to add the karmic koala repositories to my "/etc/apt/sources.list" file. i added the keys as required, but it looks like it isn't using the repositories i've added. i try to use "apt-get install firefox" as root, but it spits this back at me:

```
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  iceweasel
E: Package firefox has no installation candidate

```

are the karmic repositories not compatible with lenny? i can post the sources file if need be.
thanks in advance!

Ubuntu <> Debian. Ubuntu is a distro based on Debian but quite different.

---

### Post by mtgmutton on 2009-11-28
i read somewhere on the internet that i could use ubuntu repositories for debian... i'm guessing this means that isn't true?

---

### Post by jollysnowman on 2009-11-28
iceweasel is Debian's firefox. It's the exact same, so go ahead and install it.

And yes, the repositories are different. Out of curiosity, why would you add Ubuntu repos to Debian? The Debian repos aren't really lacking anything, and regardless, you might as well install Ubuntu.

---

### Post by mtgmutton on 2009-11-28
i figured it can't hurt to have more options in my repositories :)

i am actually considering switching from debian to ubuntu, though i've only had it installed for a day. i have no idea why, but gnome is INCREDIBLY fragile on this system, and i've had to fix it 4 times now. the package manager keeps automatically removing gnome libraries... it's very frustrating.

got iceweasel, and it is just the same. thanks for your help!

---

### Post by fluffman86 on 2009-11-28
I've only ever heard of really bad things happening when adding ubuntu repos to debian or vice versa.  Unless it's a PPA for a non-critical file or something similar.

Even so, the latest testing or unstable debian repos should be more up-to-date than Ubuntu, while Ubuntu will be more stable.  Ubuntu will also be more up-to-date than Debian stable.

---

### Post by dcstar on 2009-11-29
> **fluffman86 said:**
> I've only ever heard of really bad things happening when adding ubuntu repos to debian or vice versa.  Unless it's a PPA for a non-critical file or something similar.

Even so, the latest testing or unstable debian repos should be more up-to-date than Ubuntu, while Ubuntu will be more stable.  Ubuntu will also be more up-to-date than Debian stable.

All Ubuntu versions up to 9.10 have been based on Debian Unstable, but AFAIK the next Ubuntu 10.04 LTS version will be based on Debian Testing to improve overall reliability.

Given the issues people are having with 9.10, and the increasing quantity of new Ubuntu users who just want a working system with as few problems as possible, it sounds like very good policy to base Ubuntu on a more evolved environment.

The days of new Ubuntu release having its users as the proverbial "Crash Test Dummies" should come to an end.

---

### Post by mtgmutton on 2009-11-29
that's good! a more stable version that "just works" will be pretty nice... maybe it'll increase the conversion rate from windows :D

---

