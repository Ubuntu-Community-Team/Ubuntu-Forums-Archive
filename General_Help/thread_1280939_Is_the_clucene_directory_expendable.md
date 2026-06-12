---
title: "Is the clucene directory expendable?"
date: 2009-10-02
forum: General Help
---

### Post by t0p on 2009-10-02
I've been looking at the Disk Usage Analyzer, trying to figure out what I can delete in order to increase available storage space.  In my home directory I found this directory called **clucene**, which takes up 1.1GB according to the Analyzer.  Here is a list of clucene's contents:

```
t0p@ubunty:~/.strigi/clucene$ ls -l
total 1120300
-rwxr-xr-x 1 t0p t0p 153210935 2008-08-04 02:12 _2g2h.cfs
-rwxr-xr-x 1 t0p t0p 154828873 2008-08-04 04:05 _4w7o.cfs
-rwxr-xr-x 1 t0p t0p 155858137 2008-08-04 06:10 _7cbp.cfs
-rwxr-xr-x 1 t0p t0p 154059196 2008-08-04 07:52 _9sgx.cfs
-rwxr-xr-x 1 t0p t0p 154834330 2008-08-04 09:35 _c8m8.cfs
-rwxr-xr-x 1 t0p t0p         4 2008-08-04 14:23 deletable
-rwxr-xr-x 1 t0p t0p 155845504 2008-08-04 11:12 _eon6.cfs
-rwxr-xr-x 1 t0p t0p 152354423 2008-08-04 13:43 _h4oh.cfs
-rwxr-xr-x 1 t0p t0p  18752711 2008-08-04 13:53 _hdhl.cfs
-rwxr-xr-x 1 t0p t0p  14486808 2008-08-04 14:07 _hman.cfs
-rwxr-xr-x 1 t0p t0p  18841280 2008-08-04 14:16 _hv42.cfs
-rwxr-xr-x 1 t0p t0p    861832 2008-08-04 14:16 _hw05.cfs
-rwxr-xr-x 1 t0p t0p   1876141 2008-08-04 14:21 _hwx3.cfs
-rwxr-xr-x 1 t0p t0p    467725 2008-08-04 14:21 _hxry.cfs
-rwxr-xr-x 1 t0p t0p    466173 2008-08-04 14:21 _hymt.cfs
-rwxr-xr-x 1 t0p t0p   1413850 2008-08-04 14:21 _hziy.cfs
-rwxr-xr-x 1 t0p t0p   6022459 2008-08-04 14:22 _i0eu.cfs
-rwxr-xr-x 1 t0p t0p    411089 2008-08-04 14:22 _i1a4.cfs
-rwxr-xr-x 1 t0p t0p    865375 2008-08-04 14:23 _i276.cfs
-rwxr-xr-x 1 t0p t0p      3795 2008-08-04 14:23 _i27l.cfs
-rwxr-xr-x 1 t0p t0p     62461 2008-08-04 14:23 _i27y.cfs
-rwxr-xr-x 1 t0p t0p    121996 2008-08-04 14:23 _i28a.cfs
-rwxr-xr-x 1 t0p t0p    115398 2008-08-04 14:23 _i28l.cfs
-rwxr-xr-x 1 t0p t0p    120329 2008-08-04 14:23 _i28x.cfs
-rwxr-xr-x 1 t0p t0p      3385 2008-08-04 14:23 _i29f.cfs
-rwxr-xr-x 1 t0p t0p      3469 2008-08-04 14:23 _i29v.cfs
-rwxr-xr-x 1 t0p t0p      3658 2008-08-04 14:23 _i2ab.cfs
-rwxr-xr-x 1 t0p t0p      1766 2008-08-04 14:23 _i2ag.cfs
-rwxr-xr-x 1 t0p t0p       290 2008-08-04 14:23 segments

```Does anyone know what the clucene directory is for?  Are its contents likely to be expendable?

Note: the files with .cfs extension are reported as "data".  cfs is "crypto file system".

---

### Post by falconindy on 2009-10-02
Based on the path in your snippet, I'd say its related to Strigi, which is a desktop search daemon. [This page here]("http://www.vandenoever.info/software/strigi/") mentions that clucene is a c++ based search engine.

I think the .cfs is a coincidence with 'crytpo file system'.  It's more likely those are cache files, and while expendable, they'll be back. There seem to be a fair number of people upset with Strigi taking up so much disk space.

---

### Post by ustramooner on 2009-10-12
Actually, it means "compound file system". It's a Clucene file format and the files are used to make your files quickly searchable. There are some options in strigi to limit which files are indexed. Removing files that don't need to be searched would make this folder smaller. If you don't want any search capablitids you can also turn strigi off completely.

---

### Post by t0p on 2009-10-12
Thanks both!

---

