---
title: "File extension Z - Unix compressed archive file?"
date: 2010-05-06
forum: General Help
---

### Post by Blackylol on 2010-05-06
Anyone know how to compress a file to extension z?


not tar.gz , zip, 7zip


thanks any response!!

---

### Post by gmargo on 2010-05-07
If you are talking about the traditional capital-Z file extension, this is the original "compress" format.  The **compress(1)** tool is available in the **ncompress** package.

---

### Post by cak3 on 2010-05-07
file-roller (default archive manager) will support that format if you have the ncompress package that gmargo mentioned installed.

---

### Post by Blackylol on 2010-05-07
many thanks...  I did install the ncompress package, but how to use it  now? I tried trough file-roller but I cant c that file extension in the  list

---

### Post by gmargo on 2010-05-07
> **Blackylol said:**
> how to use it?

It's a command-line tool.
```

$ ls -lgG file_to_comp*
-rw-r--r-- 1 22495 May  7 10:35 file_to_compress

$ compress file_to_compress 

$ ls -lgG file_to_comp*
-rw-r--r-- 1 7225 May  7 10:35 file_to_compress.Z

```

---

### Post by Blackylol on 2010-05-07
thanks but I tried and nothing happened o_O

$ ls -lgG doc*
-rw-r--r-- 1 2157593 2010-05-06 15:30 doc

$ compress doc

$ ls -lgG doc*
-rw-r--r-- 1 2157593 2010-05-06 15:30 doc

---

### Post by gmargo on 2010-05-07
If compress(1) cannot improve on a file's compression then it gives up without the -f option.

```

$ ls -lgG already_comp*
-rw-r--r-- 1 7225 May  7 12:26 already_compressed

$ compress already_compressed 
$ echo $?
2

$ ls -lgG already_comp*
-rw-r--r-- 1 7225 May  7 12:26 already_compressed

$ compress -f already_compressed 
$ echo $?
0

$ ls -lgG already_comp*
-rw-r--r-- 1 10265 May  7 12:26 already_compressed.Z

```Or try the "-v" (verbose) option to see what it says.
```

$ compress -v already_compressed 
already_compressed: No compression -- already_compressed unchanged

```

---

