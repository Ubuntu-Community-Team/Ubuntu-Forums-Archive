---
title: "Software needs 'Linux gcc 4.1.0/glibc 2.4': Will this run on Ubuntu 11?"
date: 2011-08-01
forum: General Help
---

### Post by Pixion on 2011-08-01
Hi,

I am trying to run software that requires "Linux® gcc 4.1.0/glibc 2.4"

I have the latest Ubuntu version downloaded and installed from cd and when running the program I get an 'Illegal instruction' message. I suspect the gcc/glibc version to be the culprit:

GCC: t seems the GCC version is 4.5.2 in this Ubuntu version, so this should be o.k. as it is > 4.1(?)

Glibc: it seems Ubuntu has an embedded version of the glibc (eglibc) linked to from glibc.so.6. The version is 2.13-0Ubuntu.

Do I need to install a glibc package myself to make this software work?

Any help is welcome!

Thanks.

---

### Post by Foxheadz on 2011-08-01
well going by the info you've given it should technically work, what's the application?

---

### Post by Pixion on 2011-08-01
It is computer graphic rendering software. 

So, as long as gcc version installed  >= required gcc version it should be good to go? 

What about the glibc version? Ubuntu uses a embedded (why?) glibc with another versioning system. Is there a way to compare eglibc to glibc versions?

Thanks for your help.

---

### Post by Pixion on 2011-08-01
Or could it be that I use the 64 bit Ubuntu edition on an Intel cpu?

There could be opcodes that AMD supports but which are not implemented in Intel and that could throw an Illegal instruction message.

---

### Post by Pixion on 2011-08-03
Solved,

It turned out I had to install the 32 bit libraries as some of the sw was 32 bit an did not run on my Ubuntu 64. 

The 32 bit libraries are downloaded during install if you select 'download updates during install' but I switched this option off when I installed.

---

