---
title: "Perl Error"
date: 2006-06-14
forum: General Help
---

### Post by jeisma on 2006-06-14
hello!

how do you fix an error like this in ubuntu?

```

admin@ubuntu:/opt/pxesconfig-1.2$ perl Makefile.PL

Can't locate ExtUtils/MakeMaker.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at Makefile.PL line 9.
BEGIN failed--compilation aborted at Makefile.PL line 9.
admin@ubuntu:/opt/pxesconfig-1.2$ sudo apt-cache search ExtUtils
coreutils - The GNU core utilities

```

thank you!

---

### Post by croak77 on 2006-06-14
Try installing  perl-modules ( should be installed with perl though)  or  maybe libperl-dev package.

---

