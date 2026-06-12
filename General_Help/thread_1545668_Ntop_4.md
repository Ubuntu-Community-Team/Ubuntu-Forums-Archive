---
title: "Ntop 4"
date: 2010-08-04
forum: General Help
---

### Post by kelmos on 2010-08-04
Hi,

Has anyone compiled NTOP 4 on their systems yet? I've installed all dependencies and yet still get errors.

Ubuntu Server 8.04
NTOP 4
Python 2.7

Problem:
When running ./configure for ntop, I get an error, or warning, stating that Python 2.6 or newer needs to be installed.

I've installed Python 2.6.4 and then 2.6.5 and then ended up with 2.7. 

Here's what happens after running "make" for Ntop:

> /usr/bin/ld: /usr/local/lib/libpython2.7.a(boolobject.o): relocation R_X86_64_32 against `_Py_ZeroStruct' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libpython2.7.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libntopreport.la] Error 1
make[2]: Leaving directory `/root/ntop-4.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/ntop-4.0'
make: *** [all] Error 2


Anyone else got this problem before? If so, how did you manage to fix it?

I don't want to install Python3 just yet as I don't know if Ntop will support it yet.

Thanks,
K

---

