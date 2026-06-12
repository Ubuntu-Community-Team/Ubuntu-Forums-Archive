---
title: "Magicfilter and printing"
date: 2009-12-20
forum: General Help
---

### Post by knietzsche on 2009-12-20
My ultimate goal is to get my laptop, which is running ubuntu to be abe  to print from the printer that is shared on a windows xp pc.  The printer was a network printer before but i changed it to be shared on the xp pc.

I did some looking into it and i found that i needed magicfilter to help me or change some code manually so i chose to try magic filter.  I tried to install magicfilter, but then i needed m4, so i got m4 but i still can't install magicfilter.  i can ./configure.sh but when i try "make" i get:

/usr/bin/cc -I. -I/home/kevin/Downloads/magicfilter-2.3.h -I/home/kevin/Downloads/magicfilter-2.3.h/file -g -c -o getline.o getline.c
In file included from getline.c:40:
rule.h:58: error: conflicting types for &#8216;getline&#8217;
/usr/include/stdio.h:651: note: previous declaration of &#8216;getline&#8217; was here
getline.c:179: error: conflicting types for &#8216;getline&#8217;
/usr/include/stdio.h:651: note: previous declaration of &#8216;getline&#8217; was here
make: *** [getline.o] Error 1

I also am using 2.3.h but i've also seen 1.2 and im not sure which one i should use.

Perhaps i dont even need magicfilter in the first place to use my printer... i'm very new to linux.

Any help?

---

