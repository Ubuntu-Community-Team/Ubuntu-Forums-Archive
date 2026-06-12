---
title: "Perl modules using CPAN"
date: 2010-06-07
forum: General Help
---

### Post by umeboshi80 on 2010-06-07
Hi,

I think I lack some basic understanding. I tried to use CPAN to install a module Algorithm::Loops using "install Algorithm::Loops". I get the message from CPAN that
this module is already up to date.

But, when I try to use it I get the message:

Can't locate Algorithm/Loops.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./test.pl line 4.
BEGIN failed--compilation aborted at ./test.pl line 4.

And indeed, the file Loops.pm is nowhere to be found.
Isn't that a contradiction?

Thanks for any input!

Hadassa

---

### Post by umeboshi80 on 2010-06-07
Will answer that myself:

Looks like I have a big mess with having different perl folders (some called perl, some called perl5 etc.). I used the "use lib" command in the perl program to circumvent this problem temporarily.

Thanks,
Hadassa

---

### Post by ba_saish on 2010-06-08
I think you can add the path to where ever your lib files are located to  your INC variable

---

