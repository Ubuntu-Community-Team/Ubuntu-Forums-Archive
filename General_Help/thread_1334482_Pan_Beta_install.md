---
title: "Pan Beta install"
date: 2009-11-22
forum: General Help
---

### Post by yester64 on 2009-11-22
Hi,
i try to install pan beta 0.132 and i ran in a problem which i can not figure out right now.
I installed all the libraries and did ./configure so far.
But once i execute make, it give errors back.

```
joerg@joerg-desktop:~/src/pan-0.132$ make
make  all-recursive
make[1]: Entering directory `/home/joerg/src/pan-0.132'
Making all in po
make[2]: Entering directory `/home/joerg/src/pan-0.132/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/joerg/src/pan-0.132/po'
Making all in uulib
make[2]: Entering directory `/home/joerg/src/pan-0.132/uulib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/joerg/src/pan-0.132/uulib'
Making all in pan
make[2]: Entering directory `/home/joerg/src/pan-0.132/pan'
Making all in general
make[3]: Entering directory `/home/joerg/src/pan-0.132/pan/general'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../.. -D_LARGEFILE64_SOURCE -I/usr/include/gmime-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT file-util.o -MD -MP -MF ".deps/file-util.Tpo" -c -o file-util.o file-util.cc; \
    then mv -f ".deps/file-util.Tpo" ".deps/file-util.Po"; else rm -f ".deps/file-util.Tpo"; exit 1; fi
file-util.cc: In function ‘std::string pan::file::sanitize(const pan::StringView&)’:
file-util.cc:189: error: ‘replace’ is not a member of ‘std’
file-util.cc: In function ‘bool pan::file::get_text_file_contents(const pan::StringView&, std::string&, const char*, const char*)’:
file-util.cc:301: error: ‘remove’ is not a member of ‘std’
make[3]: *** [file-util.o] Error 1
make[3]: Leaving directory `/home/joerg/src/pan-0.132/pan/general'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/joerg/src/pan-0.132/pan'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joerg/src/pan-0.132'
make: *** [all] Error 2

```

can someone enlighten me how i can fix this? Thx :);)

---

### Post by oldos2er on 2009-11-22
If you're running 9.10, Pan v0.133 is in the repositories.

---

### Post by yester64 on 2009-11-22
> **oldos2er said:**
> If you're running 9.10, Pan v0.133 is in the repositories.

you are right. my mistake. should have looked before it did that. :(

---

### Post by ssptfire on 2010-08-05
multi-part message encoding for viewing pictures is broken in .133.  Trying to build from earlier versions to get around that and getting the same problem.  It looks like these may be causing the problems:
file-util.cc:189: error: ‘replace’ is not a member of ‘std’
file-util.cc:301: error: ‘remove’ is not a member of ‘std’

but I'm not a coder and don't know how to fix those, and Google is failing me as well.

Any advice, or phrases to search on Google?

---

