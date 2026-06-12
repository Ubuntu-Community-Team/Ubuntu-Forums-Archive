---
title: "GPG error or some errors related, How do they happen?"
date: 2012-07-05
forum: General Help
---

### Post by silencej on 2012-07-05
Once upon a time, now often, I come across the GPG error a lot as in:

```
W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

The solution provided in [http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/](http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/) could be helpful but it always failed for me!

Another problem is the so-called bzip error:

```
Get:7 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [85.9 kB]                                                                                     
100% [7 Packages bzip2 0 B] [1 Release.gpg 0 B/198 B 0%]                                                                                                     292 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

```

For the suspects, my assumptions are:

1. Network interruption. When I was downloading or updating the index files, the network interruption lead to such errors.

2. Repository instability. The US main server is assumed to be stable. But I would still like to mention here.

Could any guru provide cues on how to find out the actual culprit?

---

