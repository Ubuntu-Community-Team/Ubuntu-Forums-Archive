---
title: "Fortran tools"
date: 2009-11-12
forum: General Help
---

### Post by Lachlanus on 2009-11-12
I'm looking for some tools for manipulating fortran files in ubuntu.  Specifically, I was hoping to find the equivalent of fsplit, which separates a .f file into several files, each containing only one routine, and a program that will take several separate .f files and paste them together (for easier searching, etc.)  Is there a fortran toolbox like that available?

---

### Post by egalvan on 2009-11-12
google showed some hits, such as


[http://www.rpmfind.net/linux/RPM/falsehope/home/pierre/fsplit/fsplit-5.5-1.i386.html](http://www.rpmfind.net/linux/RPM/falsehope/home/pierre/fsplit/fsplit-5.5-1.i386.html)


[http://www.lahey.com/other.htm](http://www.lahey.com/other.htm)


[http://www.fnal.gov/docs/UNIX/unix_at_fermilab/htmldoc/rev1997/uatf-103.html](http://www.fnal.gov/docs/UNIX/unix_at_fermilab/htmldoc/rev1997/uatf-103.html)

---

### Post by niteshifter on 2009-11-13
Hi,

Ah ... memories ;)

The source for fsplit.c is available from [here]("http://www.opensource.apple.com/source/developer_cmds/developer_cmds-28/fsplit/fsplit.c") (opensource.apple.com). The plain text link on that page will get you non-htmled source suitable for compiling.

Compile by:
```
gcc -Dlint fsplit.c -o fsplit
```

---

### Post by mwparis on 2010-04-02
I just did what you suggested, niteshifter and got this:

$ gcc -Dlint fsplit.c -o fsplit
fsplit.c:94: error: conflicting types for &#8216;getline&#8217;
/usr/include/stdio.h:651: note: previous declaration of &#8216;getline&#8217; was here
fsplit.c:255: error: conflicting types for &#8216;getline&#8217;
/usr/include/stdio.h:651: note: previous declaration of &#8216;getline&#8217; was here

Any suggestions?

---

