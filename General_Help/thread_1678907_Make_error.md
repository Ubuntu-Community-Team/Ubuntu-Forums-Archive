---
title: "Make error"
date: 2011-01-31
forum: General Help
---

### Post by JannuBl22t on 2011-01-31
Hey!

I'm trying to "make" one thing, but it seems it doesn't want to work.

I get this error:

```

root@queries:~/WWW-Google-PageRank-0.16# make
make: Warning: File `lib/WWW/Google/PageRank.pm' has modification time 2.8e+08 s in the future
Skip blib/lib/WWW/Google/PageRank.pm (unchanged)
Manifying blib/man3/WWW::Google::PageRank.3pm
make: warning:  Clock skew detected.  Your build may be incomplete.

```

```

root@queries:~/WWW-Google-PageRank-0.16# make test
make: Warning: File `lib/WWW/Google/PageRank.pm' has modification time 2.8e+08 s in the future
Skip blib/lib/WWW/Google/PageRank.pm (unchanged)
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00use.t .. ok
t/local.t .. ok
t/utf8.t ... ok
All tests successful.
Files=3, Tests=17,  1 wallclock secs ( 0.03 usr  0.00 sys +  0.14 cusr  0.02 csys =  0.19 CPU)
Result: PASS
make: warning:  Clock skew detected.  Your build may be incomplete.

```

```

root@queries:~/WWW-Google-PageRank-0.16# make install
make: Warning: File `lib/WWW/Google/PageRank.pm' has modification time 2.8e+08 s in the future
Skip blib/lib/WWW/Google/PageRank.pm (unchanged)
Manifying blib/man3/WWW::Google::PageRank.3pm
Appending installation info to /usr/local/lib/perl/5.10.1/perllocal.pod
make: warning:  Clock skew detected.  Your build may be incomplete.

```

Please help me out.
):P

---

### Post by gmargo on 2011-01-31
You need to re-extract the archive.  Somehow one of your files got strangely modified.

I downloaded 
[http://search.cpan.org/CPAN/authors/id/Y/YK/YKAR/WWW-Google-PageRank-0.16.tar.gz](http://search.cpan.org/CPAN/authors/id/Y/YK/YKAR/WWW-Google-PageRank-0.16.tar.gz)
and had no problem compiling/testing.  The files in the archive have normal timestamps.  The PageRank.pm file was modified on 2010-12-07.

---

### Post by JannuBl22t on 2011-01-31
Hey thank you for your reply. Can you please tell me how you extracted it

---

### Post by JannuBl22t on 2011-01-31
I get this:

```


root@queries:~# tar -zxvf WWW-Google-PageRank-0.16.tar.gz
WWW-Google-PageRank-0.16/
WWW-Google-PageRank-0.16/META.yml
tar: WWW-Google-PageRank-0.16/META.yml: time stamp 2010-12-07 17:51:58 is 275716729.613512 s in the future
WWW-Google-PageRank-0.16/t/
WWW-Google-PageRank-0.16/t/00use.t
tar: WWW-Google-PageRank-0.16/t/00use.t: time stamp 2010-08-08 09:52:17 is 265233548.613197 s in the future
WWW-Google-PageRank-0.16/t/local.t
tar: WWW-Google-PageRank-0.16/t/local.t: time stamp 2010-08-08 09:52:17 is 265233548.613087 s in the future
WWW-Google-PageRank-0.16/t/utf8.t
tar: WWW-Google-PageRank-0.16/t/utf8.t: time stamp 2010-08-08 09:52:17 is 265233548.612957 s in the future
WWW-Google-PageRank-0.16/Changes
tar: WWW-Google-PageRank-0.16/t: time stamp 2010-12-07 17:51:58 is 275716729.612853 s in the future
tar: WWW-Google-PageRank-0.16/Changes: time stamp 2010-12-07 17:41:11 is 275716082.612729 s in the future
WWW-Google-PageRank-0.16/MANIFEST
tar: WWW-Google-PageRank-0.16/MANIFEST: time stamp 2010-08-08 09:52:17 is 265233548.61258 s in the future
WWW-Google-PageRank-0.16/README
tar: WWW-Google-PageRank-0.16/README: time stamp 2010-08-08 09:52:17 is 265233548.612473 s in the future
WWW-Google-PageRank-0.16/Makefile.PL
tar: WWW-Google-PageRank-0.16/Makefile.PL: time stamp 2010-08-08 09:52:17 is 265233548.612368 s in the future
WWW-Google-PageRank-0.16/lib/
WWW-Google-PageRank-0.16/lib/WWW/
WWW-Google-PageRank-0.16/lib/WWW/Google/
WWW-Google-PageRank-0.16/lib/WWW/Google/PageRank.pm
tar: WWW-Google-PageRank-0.16/lib/WWW/Google/PageRank.pm: time stamp 2010-12-07 17:43:36 is 275716227.612028 s in the future
tar: WWW-Google-PageRank-0.16/lib/WWW/Google: time stamp 2010-12-07 17:51:58 is 275716729.611905 s in the future
tar: WWW-Google-PageRank-0.16/lib/WWW: time stamp 2010-12-07 17:51:58 is 275716729.611804 s in the future
tar: WWW-Google-PageRank-0.16/lib: time stamp 2010-12-07 17:51:58 is 275716729.611707 s in the future
tar: WWW-Google-PageRank-0.16: time stamp 2010-12-07 17:51:58 is 275716729.61161 s in the future

```

---

### Post by JannuBl22t on 2011-01-31
Ahhhhhh when I do "date" then it shows:

```

root@queries:~# date
Wed Mar 13 13:58:50 UTC 2002
```

and when I try to set it then I can't because I don't have permissions

---

### Post by [Snc] on 2011-01-31
> **JannuBl22t said:**
> ...and when I try to set it then I can't because I don't have permissions

Have you tried sudo? :)

---

### Post by JannuBl22t on 2011-01-31
Yes I tried sudo

---

