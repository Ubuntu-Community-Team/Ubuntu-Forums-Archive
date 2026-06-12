---
title: "How to remove Mint Plymouth packages?"
date: 2010-10-16
forum: General Help
---

### Post by topdownjimmy on 2010-10-16
A while back in Lucid, I wanted to install the Mint menu, and so added a Mint repository, which proceeded to overwrite a bunch of Ubuntu packages (should have been much more careful).

I was able to revert most of them to the Ubuntu version, but one that is very very persistent is plymouth and its dependencies (libplymouth2, plymouth-label, etc.)

I removed the Mint repository and expected that the version numbers of the Ubuntu Plymouth packages would eventually become greater than those of Mint and overwrite them during a typical upgrade.  This hasn't happened yet, and it looks like it might not for a while.

I've tried doing "Force Version" in Synaptic, but I get some broken package errors.  On top of that, libplymouth2 has about a million dependants, all of which are marked for removal when I mark libplymouth2 for removal.

What I'd like to be able to do is remove these Plymouth-related Mint packages and install the Ubuntu ones immediately afterwards, but I'm having trouble forcing apt to ignore these multiple errors.  I know you're not supposed to ignore dependencies and broken packages when using apt, but in this case I think it'd be pretty safe to remove four Mint packages and promptly install the Ubuntu versions.

Any suggestions?  Other than reinstalling Maverick entirely.

---

