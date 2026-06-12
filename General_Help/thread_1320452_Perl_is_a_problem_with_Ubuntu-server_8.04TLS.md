---
title: "Perl is a problem with Ubuntu-server 8.04TLS"
date: 2009-11-09
forum: General Help
---

### Post by redelek on 2009-11-09
Hi everyone,
Perl-DB I need to run bacula-web.
I ran CPAN and I gave the command install Bundle:: CPAN.
Unfortunately, it ended in failure

```
Recursive dependency detected:
    Bundle::CPAN
 => Test::Harness
 => A/AN/ANDYA/Test-Harness-3.17.tar.gz
 => File::Spec
 => S/SM/SMUELLER/PathTools-3.31.tar.gz
 => Scalar::Util
 => G/GB/GBARR/Scalar-List-Utils-1.21.tar.gz
 => Test::More
 => M/MS/MSCHWERN/Test-Simple-0.94.tar.gz
 => Test::Harness.
Cannot continue.
```Issue the command make install ends with this error

```

  CPAN.pm: Going to build F/FD/FDESAR/Parse-Yapp-1.05.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Parse::Yapp
    -- NOT OK
Running make for J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz
  Is already unwrapped into directory /home/predel/.cpan/build/junoscript-perl-6.4I0

  CPAN.pm: Going to build J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz

    -- NOT OK
```Please help

Best regards 
Redelek

---

