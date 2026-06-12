---
title: "maxima crashes upon start"
date: 2009-11-29
forum: General Help
---

### Post by pythonscript on 2009-11-29
When I start maxima from the command line, I get this welcome text followed by an error:

```

Maxima 5.13.0 http://maxima.sourceforge.net
Using Lisp GNU Common Lisp (GCL) GCL 2.6.8 (aka GCL)
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
This is a development version of Maxima. The function bug_report()
provides bug reporting information.
(%i1) 
Maxima encountered a Lisp error:

 Error in PROGN [or a callee]: Couldn't protect

Automatically continuing.
To reenable the Lisp debugger set *debugger-hook* to nil.
(%i1) xmalloc: out of virtual memory

```

When I start wxmaxima, I can do basic mathematical exercises (like 2+2) but graphing and the calculus functions simply return no output. Any ideas how to fix this?

---

### Post by pythonscript on 2009-12-01
Anyone else had this problem? Thanks!

---

### Post by mionescu on 2009-12-12
This might be related to bug
[https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587](https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587)

Maybe comment #14 will help.

---

### Post by pythonscript on 2009-12-13
That worked perfectly; thank you. For the sake of the forum, the referred solution fixed it for me:

>            This problem occurs when address space randomization is enabled (which is enabled by default on newer kernels). When this option is set to 0 or 1, the error does not occur (default is 2). As a workaround, you should add the following line to /etc/sysctl.conf:
 kernel.randomize_va_space = 1
 After that, run sysctl -p
 Good luck!

        


Thank you again for pointing me to this.

---

