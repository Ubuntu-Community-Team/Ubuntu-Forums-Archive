---
title: "How do you build a package for a script?"
date: 2009-10-05
forum: General Help
---

### Post by markseger on 2009-10-05
I've been trying to build a package based on the descriptions in [https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/) which are quite good.  However the one thing that has me stumped is what to do about the fact that I don't have a makefile.  My installation exists of simply copying some files into a few directories and building some links to them.  Perhaps my mind has also been polluted but thinking of builds in terms of RPM.

I did create a build environment and commented out the calls to make in my rules  file just to see what would happen and it did indeed work, creating a very small '.deb' file which obviously doesn't even contain my code.

Might there be any examples around for building a package that is only a bunch of files that don't require 'make'ing?

-mark

---

### Post by markseger on 2009-10-05
I think I've figured it out.  I wrote a thin makefile that calls my scripts.  Whether this is considered legal is another story.  ;-)
-mark

---

