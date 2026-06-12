---
title: "Help installing perl Net::Interface module"
date: 2012-01-09
forum: General Help
---

### Post by tbaror on 2012-01-09
Hello All,

I am trying to install [PacketFence ]("http://www.packetfence.net")under Ubuntu 11.10 the installation  succeeded but when i am executing the configurator.pl is ending with  error module missing showed below  i tried install the module as follows 
```

perl -MCPAN -e 'install Net::Interface'  
```I get error 
Please advise 
Thanks
```

make: *** [test_dynamic] Error 255
  MIKER/Net-Interface-1.012.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports MIKER/Net-Interface-1.012.tar.gz
Running make install
  make test had returned bad status, won't install without force                      

```I f somone could help resolve this missing perl module some how


error during running configuration 
```
@gfn-srv-secmnn:/home/pf# ./configurator.pl     
  Can't locate Net/Interface.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at ./configurator.pl line 60. BEGIN 
failed--compilation aborted at ./configurator.pl line 60 (#1)     (F) You said to do (or require, or use) a file that couldn't be     found. Perl looks for the file in all the locations mentioned in @INC,     unless the file name included the full path to the file. 

 Perhaps you     need to set the PERL5LIB or PERL5OPT environment variable to say where     the extra library is, or maybe the script needs to add the library name     to @INC.  Or maybe you just misspelled the name of the file.  See     perlfunc/require and lib.  Uncaught exception from user code:         Can't locate Net/Interface.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at ./configurator.pl line 60. BEGIN failed--compilation aborted at ./configurator.pl line 60.  at ./configurator.pl line 60

```

---

### Post by Lars Noodén on 2012-01-09
I wasn't able to duplicate precisely the same error, but I did have to install the package **liblocal-lib-perl** to get rid of my errors.

---

### Post by tbaror on 2012-01-09
> **Lars Noodén said:**
> I wasn't able to duplicate precisely the same error, but I did have to install the package **liblocal-lib-perl** to get rid of my errors.

Hi 
Thanks for the post i tried it but same error
```
Test Summary Report
-------------------
t/faceinfo.t    (Wstat: 65280 Tests: 2 Failed: 1)
  Failed test:  1
  Non-zero exit status: 255
  Parse errors: Tests out of sequence.  Found (1) but expected (2)
                Bad plan.  You planned 1 tests but ran 2.
t/symbols.t     (Wstat: 1280 Tests: 41 Failed: 5)
  Failed tests:  3-6, 13
  Non-zero exit status: 5
Files=12, Tests=765,  1 wallclock secs ( 0.10 usr  0.03 sys +  0.34 cusr  0.02 csys =  0.49 CPU)
Result: FAIL
Failed 2/12 test programs. 6/765 subtests failed.
make: *** [test_dynamic] Error 255
  MIKER/Net-Interface-1.012.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports MIKER/Net-Interface-1.012.tar.gz
Running make install
  make test had returned bad status, won't install without force
root@gfn-srv-secmnn:~#

```

---

