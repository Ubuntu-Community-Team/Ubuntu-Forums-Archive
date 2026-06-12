---
title: "&quot;This Perl not built to support threads&quot;"
date: 2010-10-27
forum: General Help
---

### Post by Darxus on 2010-10-27
$ /usr/bin/perl -e "require threads;"
This Perl not built to support threads
Compilation failed in require at -e line 1.

I reinstalled the perl, perl-base, and perl-modules packages.  The md5sum of /usr/bin/perl matches that of the same file on another machine which is not having this problem (4523fdc6d9f3d8cfe46340d4c2c47948).  Both are Lucid 64 bit.

What could be causing this?

---

### Post by Darxus on 2010-10-27
It's my PERL5LIB environment variable.  If it's not defined, or empty, it works fine.  If it has stuff in it it breaks.  I guess default stuff is used if that variable is empty, and I need to figure out what that is to add it.

---

### Post by Darxus on 2010-10-27
I needed to add "/usr/lib/perl/5.10:" to the beginning of my PERL5LIB environment variable.  It was finding a Config.pm in another directory listed in that variable.  

I think this might be worth considering a bug in the default environment variables.  I was setting PERL5LIB as "export PERL5LIB=$PERL5LIB:", so if it had existed, defined with the default, I wouldn't have had this problem.

---

### Post by Darxus on 2010-10-27
BTW, I figured this out by diffing strace output, and noticing the differences of paths it was searching.

---

