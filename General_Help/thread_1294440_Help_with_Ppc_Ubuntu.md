---
title: "Help with Ppc Ubuntu"
date: 2009-10-18
forum: General Help
---

### Post by zaksworld on 2009-10-18
So i'm running a power pc version of ubuntu, and I'm recompiling programs from their source to the ppc architecture.

I'm using this code to do this:

[I]apt-get source packagename
[/I][I]cd packagename-version
[/I][I]apt-get build-dep packagename 
[/I][I]debuild -us -uc 

[/I]This would then make a deb file of my program in the ppc architecture.

The problem is when I run the *debuild *command it says *command not found*

I tried running *apt-get install debuild *and *apt-get install devscripts build-essential fakeroot, *but my computer still thinks debuild doesn't exist.  How do I get the debuild program?  Is there another way I could compile the source for ppc?  This is all running on my ppc computer.  Thanks!

Zak

---

