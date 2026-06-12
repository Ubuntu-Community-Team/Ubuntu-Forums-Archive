---
title: "libstdc++-libc6.2-2.so.3 missing?"
date: 2004-10-23
forum: General Help
---

### Post by tambooki on 2004-10-23
I tried to fire up a binary tonight, and was told that my system doesn't have libstdc++-libc6.2-2.so.3. I googled around, and used debian's package search on the site to find what packages should provide this (libstdc++2.10, I believe), but that package isn't availble for me. I'm running a 64-bit system, and I did notice that such a file exists in the ia32-libs package listed on the debian site, but my ia32-libs didn't include it. Am I missing something here? Also, is there something similar to the debian package search ([http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents)) for ubuntu? I find it really useful when trying to track down what package provides a specific file. I don't believe apt or dpkg let's you list files installed by package if they aren't already installed, but correct me if I'm wrong.
-tambooki

---

### Post by ubuntu-geek on 2004-10-24
Hello,

This package isnt installed by default however you can install it via apt or synaptic you make also want to enable the universe.

---

### Post by rossiam on 2006-10-31
Does anyone have answers to any of tambooki's questions?  I am also having exactly this issue.  Pardon my restating of the question, but ubuntu-geek's answer didn't even begin to answer it.  I'm running amd64 edgy eft and have some old software which depends on libstdc++-libc6.2-2.so.3.  On Debian, the libstdc++-libc6.2-2.so.3 library comes from ia32-libs but on edgy eft this package does not contain libstdc++-libc6.2-2.so.3.

I have found how to use apt-file to search for packages containing files and cannot find any packages which contain the libstdc++-libc6.2-2.so.3.

Here's what I did:

sudo apt-get install apt-file
sudo apt-file update
apt-file compress # just to check that' apt-file is working; this returned lots
apt-file libstdc++-libc6.2-2.so.3

No packages are listed containing libstdc++-libc6.2-2.so.3.

I should also mention that I have universe and multiverse packages and do already have the ia32-libs package installed.

---

### Post by rossiam on 2006-11-02
One other quick note.  The libstdc++-libc6.2-2.so.3 file for *32* bit edgy is supplied by the libstdc++2.10-glibc2.2 package.  I'm still mystified as to where to get this file for 64 bit edgy.

---

