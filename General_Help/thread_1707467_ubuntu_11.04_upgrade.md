---
title: "ubuntu 11.04 upgrade"
date: 2011-03-15
forum: General Help
---

### Post by TheMixtureMedia on 2011-03-15
Hi there I can not upgrade one of my computers to 11.04 it gets this error



"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report."


can anyone help please.

---

### Post by zvacet on 2011-03-15
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

See if this helps.

---

### Post by grahammechanical on 2011-03-15
So you want to upgrade to 11.04, is that correct? I know it is 2011 but I also know that it is not yet April. I was born on the first, you see.

As the error message says, it could be that some of the packages are being held back. This could be because Canonical is close to the final release of 11.04.

Regards.

---

### Post by TheMixtureMedia on 2011-03-16
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

See if this helps.


I tried them commands and nothing this sucks maybe they are holding it back right now.

---

### Post by Bucky Ball on 2011-03-16
Well, it ain't released yet, as mentioned. Don't think you can upgrade that easily. You would need to download and install it onto your hard drive. Just a question: Why do you want to? You could possibly be in for a world of pain, but also a steep learning curve. If it's stability you're after, I perhaps wouldn't go there. But that may not be the case.

This should possibly be in the Natty Narwhal forum rather than General Help. ;)

---

