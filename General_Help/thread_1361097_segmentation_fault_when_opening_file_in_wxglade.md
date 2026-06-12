---
title: "segmentation fault when opening file in wxglade"
date: 2009-12-21
forum: General Help
---

### Post by pythonscript on 2009-12-21
I installed the python-wxglade package from the repos, but when I try to open a saved .wxg file (the file type the designer uses) I get a segmentation fault. Does anyone else have this problem and know of a solution? The only output I get on the terminal is "segmentation fault" so the designer is woefully lax on troubleshooting details, it seems. Thanks!

---

### Post by pythonscript on 2009-12-23
Does anyone else have this problem? I can't find a bug report anywhere, so I don't know if this is a problem with ubuntu interfering with the software or something deeper. Thanks!

---

### Post by maruman on 2011-06-02
It seems a permission issues, using 'sudo wxglade' it  run ...

---

### Post by __Sun__ on 2011-06-02
If you're a programmer and have a decent knowledge and experience on problem-finding then try these:

```

gdb application-name

```

 It will tell where (which function, file, etc.) the segmentation fault occurred if the executable was compiled in debug-mode. 

Also try:

```

strace application-name

```

It will tell which were the last system calls made before the SIGSEGV was raised.

Try checking the website for troubleshooting or installation errors.
Could be a bug in the programme itself.

---

### Post by dernier_recours on 2011-08-12
My computer is powered by Ubuntu Natty 11.04 - AMD64. I came through this kind of segmentation fault using python. The attached capture shows what happens when some commands are used (using python-occ, a set of CAD libraries). An inelegant solution is to run programs as root. I'm looking forward for a more convenient solution. Is this a bug?

---

