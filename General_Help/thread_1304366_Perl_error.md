---
title: "Perl error"
date: 2009-10-29
forum: General Help
---

### Post by Slowloris on 2009-10-29
Hey guys when i try to run a certain perl script i get this error, can someone tell me what modules im missing/ if any. And how i can install them thanks.

```
Can't locate Net/SSLeay.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/share/perl/5.10.0/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.0/IO/Socket/SSL.pm line 18.
Compilation failed in require at rtyty.pl line 4.
BEGIN failed--compilation aborted at rtyty.pl line 4.
```

---

### Post by tornadof3 on 2009-10-29
You're missing the Net::SSLeay module which provides SSL support for Perl. You can install this using CPAN or use Synaptic Package Manager and try installing the libnet-ssleay-perl package.

---

### Post by Giblet5 on 2009-10-29
tornadof3 said it better.

---

### Post by Slowloris on 2009-10-29
Thanks guys, problem solved :)

---

