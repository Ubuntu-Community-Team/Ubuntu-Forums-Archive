---
title: "Guide to Updating an Octave software version"
date: 2012-04-29
forum: General Help
---

### Post by RexFuzzle on 2012-04-29
Hello

I am running 12.04 will latest updates but have found the the version of octave that is included is 2 major releases behind. The bug is [here]("https://bugs.launchpad.net/ubuntu/+source/octave3.2/+bug/842479")
My question is how to help out to get it to the upgraded? Is there a guide to doing such things or is it purely experienced based. How do I know if anybody is working on it at all? Ideally it should be as easy as installing updates though the update manager if my understanding is correct?

Thank You

---

### Post by hackTHEgibson on 2012-05-01
Add one of these PPAs 
[https://launchpad.net/~picaso/+archive/octave]("https://launchpad.net/~picaso/+archive/octave")
or
[https://launchpad.net/~mvanderkolff/+archive/octave-3.6]("https://launchpad.net/~mvanderkolff/+archive/octave-3.6")


[what-are-ppas-and-how-do-i-use-them]("http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them")

---

### Post by RexFuzzle on 2012-05-01
Ok, maybe I should have stated without going the PPA route...

EDIT: Typo

---

### Post by hackTHEgibson on 2012-05-01
It will be in 12.10 but not 12.04 because LTS's are merged from debian testing and Octave 3.6 had not yet got to testing in time for the last merge. Normal releases like 12.10 are merged from unstable I think, but either way it will get into 12.10. 

The[DebianOctaveGroup]("http://wiki.debian.org/Teams/DebianOctaveGroup") does all the packaging and then Ubuntu just grabs it and rebuilds for ubuntu from whatever window they are merging from. 

So yes somebody is working on it. But no it is not as easy as installing updates through the update manager. What you are talking about is packaging and MOTU stuff.  For a guide start here [https://wiki.ubuntu.com/MOTU]("https://wiki.ubuntu.com/MOTU").

Maybe it will update when they do 12.04.1 or 12.04.2 I don't really know the specifics of how they do that. But if you don't like PPAs and it doesn't update your only other real option is to compile the source.  Which depending on your computer takes awhile.

---

