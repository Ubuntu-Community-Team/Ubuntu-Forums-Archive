---
title: "Segmentation Fault of compiled executable"
date: 2009-10-15
forum: General Help
---

### Post by scott_g on 2009-10-15
Hi,

I compiled some an executable from some fortran based source code.  I believe it compiled fine, but when I try giving it some extra libraries, and using the executable, it results in a segmentation fault.  

Does anyone know how to diagnose why the segmentation fault is occuring?  Or how to fix it?

I can post more information, if needed.

Thank you,
Scott

---

### Post by Giblet5 on 2009-10-15
Recompile w/ debugging enabled.

```
gfortran -fbacktrace .....
```

You should get a stack trace that will point you to the problem.

---

### Post by scott_g on 2009-10-15
Hi,

Thanks for the quick response.  When I try that, I get the following:

```

f951: error: unrecognized command line option "-fbacktrace"

```

I tried installing debugging symbols, but that didn't seem to fix it.  

The code is actually compiled by a shell script, and I think has a bit of c too, although I'm not too sure.  The code is located [here]("ftp://ftp.polymtl.ca/pub/nucl/dragon/dragon-3.05/DRAGON305E.TGZ"), if you need to take a look at it.  

Thank you again,
Scott

---

