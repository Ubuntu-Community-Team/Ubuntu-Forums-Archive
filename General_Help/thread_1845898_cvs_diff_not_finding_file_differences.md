---
title: "cvs diff not finding file differences"
date: 2011-09-18
forum: General Help
---

### Post by hwttdz on 2011-09-18
I keep track of versioning for a program I keep on cvs using a version file, which is included from the main program, so that when the main is compiled it gets the version number from the version file.  Generally the version file consists of a single line 
"      version = '##.###'"
or what-have-you. However, cvs seems to be foiling all my best attempts, because when the version file is committed by another user and I cvs diff, diff tells me nothing is changed.  I tried to get around it by appending a comment of random characters

head -c 500 /dev/urandom | perl -pe 'tr//A-Za-z0-9/cd'

But diff still tells me no changes, which correspondingly means that update does nothing for me. Any thoughts.  

If I check out a project without specifying a release tag, and the head release tag gets changed, will I still be held on the old release tag?

SOLUTION: CVS will diff against the version you checked out, so since we always increment the version when we edit the version file you never get a difference when you diff the version file.  If I 
cvs diff -rHEAD 
I will get the behavior I expected.  I'll have to add that to my .cvsrc.

---

