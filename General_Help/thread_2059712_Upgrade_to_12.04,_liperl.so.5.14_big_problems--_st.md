---
title: "Upgrade to 12.04, liperl.so.5.14 big problems-- stuck"
date: 2012-09-18
forum: General Help
---

### Post by vfulco on 2012-09-18
Upgrade from 10.04 to 11.04 to 12.04 and had no problems.  Tried to restart server after a number of weeks idle and now having shared library problems.

Error states "/usr/bin/perl: error while loading shared libraries: /usr/lib/libperl.so.5.14: unsupported version 0 of Verneed record"

Have scoured net, forums and asked on IRC for assistance.  I am in a bind since I can not remove/install/upgrade without this resolved since it affects sysv-rc.

Thanks in advance for your assistance. V.

:guitar:

---

### Post by DouglasAWh on 2013-01-12
I am using Linux Mint, but it seems like these problems might be related.

```

dwhitfield@lawcast ~/Dropbox/Music Manumit (1)/temp_music_files/metaparser/M4_Parser(2) $ parl M4.par
Can't load '/tmp/par-dwhitfield/cache-e82d96948c65045be2ca39cd77a6002f4dcbb752/e6ec213b.so' for module Wx: /tmp/par-dwhitfield/cache-e82d96948c65045be2ca39cd77a6002f4dcbb752/e6ec213b.so: wrong ELF class: ELFCLASS64 at /usr/lib/perl/5.14/DynaLoader.pm line 184.
 at /usr/share/perl5/PAR/Heavy.pm line 120
Compilation failed in require at M4App.pm line 9.
BEGIN failed--compilation aborted at M4App.pm line 9.
Compilation failed in require at script/run.pl line 3.
BEGIN failed--compilation aborted at script/run.pl line 3.

```

I'm hoping someone might be able to piece together a common thread in these problems. I am using Linux 13, which is based on Ubuntu 12.04.

---

