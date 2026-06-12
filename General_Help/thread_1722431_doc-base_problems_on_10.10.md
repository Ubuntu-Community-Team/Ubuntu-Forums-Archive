---
title: "doc-base problems on 10.10"
date: 2011-04-05
forum: General Help
---

### Post by blimbo on 2011-04-05
Hi gang,

I have a problem with doc-base (which ubuntu-desktop needs) on 10.10. Fails on loading Storable.so (wrong ELF class: ELFCLASS3). This file is 32 bit, my version of perl is 64 bit.. seems this EFL class problem can be causes by 32/64 bit mismatches.

Can anyone see a way of resolving this?

Thanks,

Tim

tnugent@lucid-vaio:/$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up doc-base (0.9.5) ...
MLDBM error: Please make sure MLDBM/Serializer/Storable.pm is a properly installed package.
	Perl says: "Can't load '/usr/local/lib/perl/5.10.1/auto/Storable/Storable.so' for module Storable: /usr/local/lib/perl/5.10.1/auto/Storable/Storable.so: wrong ELF class: ELFCLASS32 at /usr/lib/perl/5.10/DynaLoader.pm line 192.
 at /usr/share/perl5/MLDBM/Serializer/Storable.pm line 5
Compilation failed in require at /usr/share/perl5/MLDBM/Serializer/Storable.pm line 5.
BEGIN failed--compilation aborted at /usr/share/perl5/MLDBM/Serializer/Storable.pm line 5.
Compilation failed in require at /usr/share/perl5/MLDBM.pm line 107.
" at /usr/share/perl5/Debian/DocBase/DB.pm line 44
Can't access /var/lib/doc-base/info/status.db: No such file or directory
 at /usr/share/perl5/Debian/DocBase/Document.pm line 39
dpkg: error processing doc-base (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on doc-base; however:
  Package doc-base is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 doc-base
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
tnugent@lucid-vaio:/$

tnugent@lucid-vaio:/$ file /usr/local/lib/perl/5.10.1/auto/Storable/Storable.so
/usr/local/lib/perl/5.10.1/auto/Storable/Storable.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped
tnugent@lucid-vaio:/$ file `which perl`
/usr/bin/perl: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
tnugent@lucid-vaio:/$ uname -a
Linux lucid-vaio 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
tnugent@lucid-vaio:/$

---

### Post by blimbo on 2011-04-11
Anyone have any ideas on this one?

Thanks,

Tim

---

### Post by blimbo on 2011-04-12
Ok figured this out. Somehow I had a 32 bit version of Storable.so on my system. Just re-installed that module via cpan with:

sudo cpan -i Storable

And this built a nice 64 bit shared object:

file /usr/local/lib/perl/5.10.1/auto/Storable/Storable.so
/usr/local/lib/perl/5.10.1/auto/Storable/Storable.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not stripped

No more complaints about doc-base :-)

---

