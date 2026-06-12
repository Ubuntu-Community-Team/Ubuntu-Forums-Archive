---
title: "Can't get SLIME to work with SBCL"
date: 2010-05-23
forum: General Help
---

### Post by olwe on 2010-05-23
Yeah, that's it in a nutshell, on my new U10.04 it errors out thusly:

> SBCL is free software, provided as is, with absolutely no warranty.
It is mostly in the public domain; some portions are provided under
BSD-style licenses.  See the CREDITS and COPYING files in the
distribution for more information.
* 
; loading #P"/usr/share/common-lisp/source/slime/swank-loader.lisp"

debugger invoked on a SB-C::INPUT-ERROR-IN-COMPILE-FILE in thread #<THREAD
                                                                    "initial thread" RUNNING
                                                                    {A9F28C9}>:
  READ failure in COMPILE-FILE:
    SB-INT:SIMPLE-READER-PACKAGE-ERROR at 5151 (line 128, column 45) on #<SB-SYS:FD-STREAM
                                                                          for "file /usr/share/common-lisp/source/slime/swank-loader.lisp"
                                                                          {A9FC3D1}>:
      package "CLC" not found

Type HELP for debugger help, or (SB-EXT:QUIT) to exit from SBCL.

restarts (invokable by number or by possibly-abbreviated name):
  0: [ABORT] Exit debugger, returning to top level.

(SB-C::READ-FOR-COMPILE-FILE
 #<SB-SYS:FD-STREAM
   for "file /usr/share/common-lisp/source/slime/swank-loader.lisp" {A9FC3D1}>
 4663)
0]  

Somebody from Slime-land says I might need a sbcl.rc with lots of asdf stuff in it. The Ubuntu(debian) sbcl (1.0.29) doesn't create any asdf lines, though.

---

### Post by fbkarsdorp on 2010-06-01
can you post your slime-setup in your .emacs file?

---

### Post by olwe on 2010-06-01
Somebody on the slime list said there's a bug in the debian/ubuntu slime package, so I uninstalled it. I set up sbcl and slime by hand straight from their downloads, so my .emacs is for hand installs. Works. But my system tried to find slime in /usr/share/common-lisp/sources/slime where apt-get originally put it. I had to put a symbolic link to my hand-installed slime to get it to work finally. Any idea why/where the system knows about an uninstalled slime?

---

### Post by eric3_14159 on 2010-08-09
It seems to be tied up with CLC, the Common Lisp Controller, which uses /usr/share/common-lisp or /usr/lib/common-lisp. I've been having trouble with it recently. It looks like the common lisp controller is a package which tries to handle package managing for all of the Lisps on the system.

---

