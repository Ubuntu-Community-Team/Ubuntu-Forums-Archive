---
title: "error: m4_copy: won't overwrite defined macro: _AC_ARG_VAR_PRECIOUS"
date: 2009-11-02
forum: General Help
---

### Post by pawel2k on 2009-11-02
Hello,

Not sure if this is the correct forum to post but here goes.

After upgrading from 9.4 to 9.10 i got the following error compiling and i not sure why.

Can anybody help me .

toolchain-powerpc_gcc4.2.1/gcc-4.2.1/libstdc++-v3; autoconf;
configure.ac:83: error: m4_copy: won't overwrite defined macro: _AC_ARG_VAR_PRECIOUS
acinclude.m4:48: GLIBCXX_CONFIGURE is expanded from...
configure.ac:83: the top level
autom4te: /usr/bin/m4 failed with exit status: 1


Thanks,
Pawel

---

### Post by mich4elp on 2009-12-28
I got this error in the project GDC too when upgrading to 9.10. (Except it was with m4_rename)
I searched m4_rename, and found that there was a function called m4_rename_force.(There is also a m4_copy_force)
If you go to line 83 of configure.ac, and replace m4_copy with m4_copy_force, it should work.
Here is where I found the functions:
[http://www.gnu.org/software/autoconf/manual/html_node/Redefined-M4-Macros.html](http://www.gnu.org/software/autoconf/manual/html_node/Redefined-M4-Macros.html)

---

### Post by fackie on 2010-08-20
@mich4elp

Where did you find m4_copy?

I'm having the same issue, different line numbers (different versions, I suppose) but I have not mention whatsoever of m4_copy in the following files:

configure.ac:65: error: m4_copy: won't overwrite defined macro: _AC_ARG_VAR_PRECIOUS
aclocal.m4:94: GLIBCXX_CONFIGURE is expanded from...
configure.ac:65: the top level

configure.ac instantiates GLIBCXX_CONFIGURE, which is defined in aclocal.m4. In this file I have several m4_define and m4_rename calls in GLIBCXX_CONFIGURE, but no m4_copy - so I guess this must be called elsewhere. Grep didn't help me find it either.

Any ideas?

Thanks.

---

