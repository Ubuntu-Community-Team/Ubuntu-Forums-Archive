---
title: "Installing bioperl-ext"
date: 2009-11-15
forum: General Help
---

### Post by WouterVP on 2009-11-15
Hello,

i've got problems installing the bioperl-ext package... I've tried [http://www.bioperl.org/Core/Latest/INSTALL](http://www.bioperl.org/Core/Latest/INSTALL) and other ways but there's always a problem. The problem is I really need the packagein one of the following days. 

I hope this can help you understanding my problem.  

wouter@wout:~/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext$ perl Makefile.PL
Writing Makefile for Bio::Ext::Align
Writing Makefile for Bio::Ext
wouter@wout:~/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext$ make
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt binnengegaan
cc -c  -I./libs -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.1\" -DXS_VERSION=\"0.1\" -fPIC "-I/usr/lib/perl/5.10/CORE"  -DPOSIX -DNOERROR Align.c
Running Mkbootstrap for Bio::Ext::Align ()
chmod 644 Align.bs
rm -f ../blib/arch/auto/Bio/Ext/Align/Align.so
cc  -shared -O2 -g -L/usr/local/lib Align.o  -o ../blib/arch/auto/Bio/Ext/Align/Align.so libs/libsw.a    \
       -lm      \
      
chmod 755 ../blib/arch/auto/Bio/Ext/Align/Align.so
cp Align.bs ../blib/arch/auto/Bio/Ext/Align/Align.bs
chmod 644 ../blib/arch/auto/Bio/Ext/Align/Align.bs
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt verlaten
wouter@wout:~/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext$ make test
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt binnengegaan
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt verlaten
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt binnengegaan
PERL_DL_NONLAZY=1 /usr/bin/perl "-I../blib/lib" "-I../blib/arch" test.pl
1..2
ok 1

2..2
Testing bp_sw with a protein alignment...

ProteinSW Matrix calculation: [      0] Cells  0%
one         1        WLGQRNLVSSTGGNLLNVWLKDW                           
                     W+G RN+V     NLLNVW +DW                           
two         1        WMGNRNVV-----NLLNVWFRDW                           


ok 2
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt verlaten
wouter@wout:~/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext$ make install
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt binnengegaan
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt verlaten
Files found in blib/arch: installing files in blib/lib into architecture dependent library tree
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/lib/perl/5.10.0/Bio/Ext'
Do not have write permissions on '/usr/local/lib/perl/5.10.0/Bio/Ext'
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_site_install] Fout 255
wouter@wout:~/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext$ sudo make install
[sudo] password for wouter: 
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt binnengegaan
make[1]: Map '/home/wouter/Documenten/SCHOOL/Perl/bioperl-ext-1.4/Bio/Ext/Align' wordt verlaten
Files found in blib/arch: installing files in blib/lib into architecture dependent library tree
Writing /usr/local/lib/perl/5.10.0/auto/Bio/Ext/.packlist
Appending installation info to /usr/local/lib/perl/5.10.0/perllocal.pod


and than when i run my script:

wouter@wout:~/Documenten/SCHOOL/Perl$ perl HMMtest.pl

The C-compiled engine for Hidden Markov Model (HMM) has not been installed.
 Please read the install the bioperl-ext package

BEGIN failed--compilation aborted at /usr/share/perl5/Bio/Tools/HMM.pm line 140.
Compilation failed in require at HMMtest.pl line 3.


many thanks

W

---

