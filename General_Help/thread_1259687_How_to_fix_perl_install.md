---
title: "How to fix perl install?"
date: 2009-09-06
forum: General Help
---

### Post by bbell2000 on 2009-09-06
First, let's just say I was being really stupid.  I'll admit and now I need help getting myself out of this mess I'm in.

I was having problems with a Perl app, so I followed some instructions I found for downgrading my jaunty Perl from 5.10 to 5.8.  Even though I tried to install 5.8 in its own special location, it put it in /usr/local/bin.

I managed to figure out the original problem so now I want to get rid of it.  But here's what I don't understand:

which perl returns /usr/local/bin/perl
/usr/local/bin/perl -v returns 5.8.8
/usr/bin/perl -v returns 5.10.0

So I thought I could remove /usr/local/bin/perl.  However, after doing so:

which perl still returns /usr/bin/perl
/usr/bin/perl -v still returns 5.10.0
But perl -v says /usr/local/bin/perl: No such file or directory

What I'd really like to do is remove the 5.8.8 that I built, then make ubuntu reinstall perl... but I'd be happy just to make everything ignore 5.8.8.

Can someone explain why /usr/bin/perl -v and perl -v don't do the same thing?

---

### Post by Liolikas on 2009-09-06
>Can someone explain why /usr/bin/perl -v and perl -v don't do the same thing?
Because /usr/local/ is priority over /usr.

>Downgrading my jaunty Perl from 5.10 to 5.8.
It was bad idea.

I think just: 
apt-get install perl
And if:
perl -v
Shows .10 then ok and forget it. Removing something after manual install is just *, better just keep some broken useless files.

---

### Post by wojox on 2009-09-06
Try:

```
locate perl-5.8.8
```

Remove all instances.

Then open Synaptic and search perl and mark for re-installation.

---

### Post by bbell2000 on 2009-09-07
[QUOTE=Liolikas;7908095]>Can someone explain why /usr/bin/perl -v and perl -v don't do the same thing?
Because /usr/local/ is priority over /usr.

I understand that /usr/local appears before /usr in my path.  But...
    which perl first showed /usr/local/bin/perl
    After removing /usr/local/bin/perl, which perl showed /usr/bin/perl and perl -v gave the "/usr/local/bin/perl" not found error.

However, when I looked at the size of /usr/bin/perl, it's size was tiny in comparison.  It wasn't a symbolic link, so it looks like something created a stub that somehow redirects to the 5.8.8 binary.

For the short term, I linked /usr/local/bin/perl to the 5.10 binary, but I think I'll try what the next poster said to get 5.10 installed the way it should be.

---

