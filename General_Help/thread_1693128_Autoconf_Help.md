---
title: "Autoconf Help"
date: 2011-02-22
forum: General Help
---

### Post by awaisclub on 2011-02-22
Hi,

I am having a problem while getting the path through the macro that is placed in .m4 file. That macro is called in configure.ac file. The macro is simple. It has to get the folder in the directory. But the macro is only getting the command as it is i.e "ls /bin". Does anyone know the solution?


[COLOR=SeaGreen]############### CONFIGURE.AC ####################[/COLOR]
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
[COLOR=Red]#calling macro[/COLOR]
[COLOR=Red]m4_include(AC_TEST.m4)[/COLOR]

AC_PREREQ([2.55])
AC_INIT(hello, 2.0, @aclub)
AC_CONFIG_SRCDIR([src/hello.h])
AM_INIT_AUTOMAKE

[COLOR=Red]#Trying to get value over here[/COLOR]
[COLOR=Red]AC_SUBST([FOLDER])
if test "$FOLDER" != "10.2.4.032"; then
        AC_MSG_ERROR([$FOLDER is found])
fi
[/COLOR]
#AC_SUBST([LIBS], ["-L/opt/intel/mkl/$FOLDER/lib/em64t/ -lmkl_intel_lp64 -lmkl_intel_thread -lmkl_core -liomp5 -lpthread"])
AC_CONFIG_HEADERS([config.h])
#AC_CONFIG_FILES([Makefile src/Makefile])
# Checks for programs.
AC_PROG_CC
# Checks for libraries.
# Checks for header files.
# Checks for typedefs, structures, and compiler characteristics.
# Checks for library functions.
AC_CONFIG_FILES([Makefile src/Makefile])
AC_OUTPUT


[COLOR=DarkGreen]##################  [/COLOR][COLOR=DarkGreen]AC_TEST[/COLOR][COLOR=DarkGreen].m4  #####################[/COLOR]
[COLOR=Red]AC_DEFUN([AC_TEST], [FOLDER= 'ls /opt/intel/mkl'])[/COLOR]



Rg,
Aclub

---

